# Vision

This document describes where the platform is heading. The [product documentation](why/README.md) records the decisions that apply today. Open questions are listed at the end.

## Purpose

The vision adds a central governance platform. The CLI verifies one repository at a time and stays fully functional without it. The platform answers a different question for a whole organization: for which commits is there evidence that which rules, in which version, passed, and where are the gaps against what the organization expects?

The platform creates transparency. It does not block builds; the CLI and the CI gates do that.

## Evidence, not proof

A report is a local, unsigned file. An attestation sent from CI is evidence: its origin is authenticated, but its results are self-reported by the sender. The platform presents it as evidence and never as proof.

## Components

```
CI run ──────────────attestation─────┐
Release workflow ────release fact────┼──► Gateway ──► Ledger ──► Database
Deployment workflow ─deployment fact─┘

Source-control collector ──platform facts──► Ledger ◄──reads── Cockpit
```

Each component has its own repository, so its boundaries stay explicit and a developer or agent works with one component's code and knowledge at a time. A contract is owned by its producer; consumers reference it.

- **Gateway.** The address the senders push to. Stateless, public, without database access. It authenticates senders, validates submissions and forwards them. Several instances behind one address provide horizontal scaling.
- **Ledger.** The single owner of the database and the only API to it. It receives attestations, release facts and deployment facts from the gateway and serves the combined view for reading. Its append-only attestations form the history of verification over time. It also receives platform facts from collectors over the internal network.
- **Source-control collector.** Reads its platform API and reports repository inventory and default-branch head observations directly to the ledger. The first is the [GitHub collector](https://github.com/please-behave/github-collector).
- **Cockpit.** The user interface. It talks to the ledger only and knows no source-control platform.

## Attestation

A small, immutable statement about one CI run:

- the execution point;
- per rule: rule identity, version and registration digest when available,
  status and whether it blocks;
- the rule sets bound in the run: identity, version and execution points;
- the overall status;
- the scope of the run, such as checks-only or fail-fast;
- the CLI version.

It carries no report, tool output, error messages, findings or code excerpts. Teams read those in their own CI artifacts and in local feedback. This keeps sensitive data out of the platform.

Repository and commit are taken from the authenticated source, not from the payload.

Evidence belongs to the commit reported in the attestation. A pull request run can provide feedback and help trial new Rule Sets. If squash or rebase produces a different commit, evidence for that commit requires its own attestation.

Execution points tied to Git hooks are not the basis. `check` is the recommended point for CI, and a project may define further execution points that behave like it.

[DEC-0010](why/decisions/DEC-0010.yaml) defines rule identity and the role of
the run-scoped ID. [DEC-0011](why/decisions/DEC-0011.yaml) defines rule versions.
[DEC-0012](why/decisions/DEC-0012.yaml) defines what gets registered,
[DEC-0013](why/decisions/DEC-0013.yaml) defines how results match registrations,
and [DEC-0014](why/decisions/DEC-0014.yaml) assigns ownership and validation for
rule knowledge in registrations.

## Sending

A failed delivery is a separate outcome from the rule verdict. Each project configures whether it fails the build or lets it pass. Missing check evidence for an observed default-branch head appears in the cockpit according to the repository status in [DEC-0024](why/decisions/DEC-0024.yaml). Delivery is idempotent per repository, run, attempt and execution point, so it can be retried.

## Authentication

The gateway offers authentication methods as adapters:

- **GitHub OIDC.** Repository, commit and workflow come from signed claims. The accepted workflow can be restricted to an approved reusable one.
- **API key.** Platform-independent. An organization secret that rotates. It is not bound to a repository, so the sender's identity is self-asserted.

Every stored attestation records the method used, so the cockpit can show the weaker trust level of the second one.

## Rule sets

A rule set is a versioned platform entity that bundles rules. [DEC-0016](why/decisions/DEC-0016.yaml) defines its identity, version and display name, [DEC-0017](why/decisions/DEC-0017.yaml) its registration and members, [DEC-0018](why/decisions/DEC-0018.yaml) how an attestation records the sets bound in a run and [DEC-0019](why/decisions/DEC-0019.yaml) when a set is complete for a repository. Rules defined in a repository without a set are not a rule set.

## Expectations and gaps

An organization defines which repositories must apply which rule sets and can set an effective date. The ledger combines those expectations with the repository inventory from the source-control platform and the attestations it has received. That lets it identify gaps even for repositories that have never reported.

The cockpit uses the [shared status palette](brand/README.md#status-tokens). A team binds a new rule set to a separate execution point that no gate requires. The CLI reports the failure, and the cockpit presents it as not yet satisfied but allowed until the effective date. Then the team moves the rule set to the blocking execution point.

Expectations carry validity ranges so historical views can use the expectations in effect at the relevant time.

## Releases

An authenticated release workflow can explicitly report the repository, version and full commit ID. The ledger records receipt time and sender provenance. [Release Facts](why/decisions/DEC-0020.yaml) defines ownership and how retries and conflicts preserve the first record for each version.

The ledger links the release to reported evidence for the same repository and commit, regardless of delivery order. [Evidence per Commit](why/decisions/DEC-0021.yaml) defines which attestation supplies the rule results and completed Rule Sets. A release can have no evidence if its commit has no attestation containing `check`.

## Deployments and environments

The reporter is the authenticated sender and owns the target. The subject is the deployed software, identified by its repository and a release version or full commit. The target is where the software runs, identified by its owner and registered name. For example, an infrastructure repository can report that it deployed a release of an application repository to a target registered by the infrastructure repository.

[Deployment Targets](why/decisions/DEC-0022.yaml) defines target declaration and registration. Central classes of targets, such as live and non-live, belong to expectations. [Deployment Facts](why/decisions/DEC-0023.yaml) defines the current deployment, its history and the link to reported commit evidence.

## Source-control platform

[Repository Inventory and Status](why/decisions/DEC-0024.yaml) defines periodic collection, the inventory and sampled default-branch heads. The ledger combines these platform facts with reported check evidence for the exact observed commit to derive repository status on read. This shows where evidence is pending or overdue, where a repository has never integrated and where collection data is missing or stale.

## Policy inheritance and controlled exceptions

Organizations may want policies that projects inherit, and exceptions that are explicit, justified and limited in time instead of silent. How this relates to immutable shared rule sets and to adoption phases is open.

## Governance based on architectural decisions

Reviews could evaluate changes against the decisions a project has documented, so that recorded architecture is enforced and not only read. Rule sets can already express this; what a platform adds is visibility across repositories.

## Open questions

- **Sender.** The CLI writes the attestation and a CI step sends it, or the CLI sends it itself. The first keeps an HTTP and OIDC client out of the CLI.
- **Queue.** Whether and when to decouple gateway and ledger with a queue; the internal interface leaves room for it.
- **Database.** A relational database is expected, because the questions are joins between expectation, evidence and facts.
- **Source of expectations.** A versioned file, repository properties of the source-control platform, or both.
- **Platform-sourced releases.** Whether and how source-control platform events or API reads should complement explicitly reported releases.
- **Non-blocking checks.** Whether deterministic checks also need an adoption phase, or the separate execution point suffices.
- **Hosting.** Where the platform runs.
