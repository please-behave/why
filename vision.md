# Vision

This document describes the future. Nothing in it exists yet and nothing in it is a commitment. Open questions are listed at the end.

## Purpose

The vision adds a central governance platform. The CLI verifies one repository at a time and stays fully functional without it. The platform answers a different question for a whole organization: for which commits is there evidence that which rules, in which version, passed, and where are the gaps against what the organization expects?

The platform creates transparency. It does not block builds; the CLI and the CI gates do that.

## Evidence, not proof

A report is a local, unsigned file. An attestation sent from CI is evidence: its origin is authenticated, but its results are self-reported by the sender. The platform presents it as evidence and never as proof.

## Components

```
CI run ──attestation──► Gateway ──► Ledger ──► Database
Source-control platform ──facts──────┘   ▲
                                      Cockpit
```

Each component has its own repository, so its boundaries stay explicit and a developer or agent works with one component's code and knowledge at a time. A contract is owned by its producer; consumers reference it.

- **Gateway.** The address the senders push to. Stateless, public, without database access. It authenticates, validates the attestation schema and forwards. Several instances behind one address provide horizontal scaling.
- **Ledger.** The single owner of the database and the only API to it. It has two inputs, attestations from the gateway and facts from the source-control platform, and it serves the combined view for reading. Its append-only attestations form the history of verification over time.
- **Cockpit.** The user interface. It talks to the ledger only and knows no source-control platform.

## Attestation

A small, immutable statement about one CI run:

- the execution point;
- per rule: identity, version, status and whether it blocks;
- the overall status;
- the scope of the run, such as checks-only or fail-fast;
- the CLI version.

It carries no report, tool output, error messages, findings or code excerpts. Teams read those in their own CI artifacts and in local feedback. This keeps sensitive data out of the platform.

Repository and commit are taken from the authenticated source, not from the payload.

Evidence belongs to a commit. A run on a pull request merge reference proves nothing for the commit that lands later, especially after squash or rebase. Proof for a release needs a run on the release commit itself. Pull request runs remain valuable as feedback and as a trial of new rule sets.

Execution points tied to Git hooks are not the basis. `check` is the recommended point for CI, and a project may define further execution points that behave like it.

## Sending

A failed delivery is a separate outcome from the rule verdict. Each project configures whether it fails the build or lets it pass. A missing attestation appears in the cockpit as a gap, which is why letting it pass stays visible. Delivery is idempotent per repository, run, attempt and execution point, so it can be retried.

## Authentication

The gateway offers authentication methods as adapters:

- **GitHub OIDC.** Repository, commit and workflow come from signed claims. The accepted workflow can be restricted to an approved reusable one.
- **API key.** Platform-independent. An organization secret that rotates. It is not bound to a repository, so the sender's identity is self-asserted.

Every stored attestation records the method used, so the cockpit can show the weaker trust level of the second one.

## Expectations and gaps

An organization states what it expects: which repositories must apply which rule sets, optionally from an effective date. The ledger compares this with the repository inventory of the source-control platform and the received attestations. A gap is something expected without evidence.

The cockpit shows green for passed, red for failed and yellow for not yet satisfied but allowed. Yellow needs no special CLI feature. A team binds a new rule set to a separate execution point that no gate requires, the CLI reports the failure truthfully, and the cockpit reads it as yellow until the effective date. Then the team moves the rule set to the blocking execution point.

Expectations carry validity ranges, so a past release is judged against what was expected at that time.

## Releases and deployments

A release or deployment is a fact: a tag or commit, an environment and a time. The platform links it to the attestations of that commit and shows whether every expected rule passed for what was released. This evidence per release is probably the greatest value of the platform.

## Source-control platform

GitHub comes first. The ledger integrates it through its API: repository inventory, repository properties, commits, releases and deployments. The data model keeps a platform-neutral core of repository, commit, release and deployment, each qualified by platform and host, and keeps platform-specific details beside it. Another platform is then an additional adapter inside the ledger and changes no other component. Its details are not designed ahead.

## Policy inheritance and controlled exceptions

Organizations may want policies that projects inherit, and exceptions that are explicit, justified and limited in time instead of silent. How this relates to immutable shared rule sets and to adoption phases is open.

## Governance based on architectural decisions

Reviews could evaluate changes against the decisions a project has documented, so that recorded architecture is enforced and not only read. Rule sets can already express this; what a platform adds is visibility across repositories.

## Open questions

- **Identity of imported rules.** Source repository qualified by platform, path in it and rule ID, replacing the current binding-qualified identity.
- **Rule version.** The resolved revision of the rule set, a checksum over the rule's files, or a mandatory explicit version that rejects a changed checksum.
- **Sender.** The CLI writes the attestation and a CI step sends it, or the CLI sends it itself. The first keeps an HTTP and OIDC client out of the CLI.
- **Queue.** Whether and when to decouple gateway and ledger with a queue; the internal interface leaves room for it.
- **Database.** A relational database is expected, because the questions are joins between expectation, evidence and facts.
- **Source of expectations.** A versioned file, repository properties of the source-control platform, or both.
- **Release facts.** Platform webhooks first with reporting through the gateway as a fallback, or the reverse.
- **Non-blocking checks.** Whether deterministic checks also need an adoption phase, or the separate execution point suffices.
- **Hosting.** Where the platform runs.
