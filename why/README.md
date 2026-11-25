# Please Behave

Please Behave makes software development governance explicit, executable and verifiable, independently of who or what writes the code.

AI-assisted development is becoming more autonomous, while responsibility for quality, architectural consistency, maintainability and adherence to requirements stays with developers and organizations. Compilers, tests and linters already provide deterministic gates, but many expectations cannot be expressed through them alone: whether an implementation satisfies its documented requirements, whether a change respects architectural decisions, whether unnecessary complexity was introduced. Reviews by language models can evaluate these questions, but their judgments are probabilistic. Please Behave combines both in one configurable governance model and establishes whether explicitly configured expectations are satisfied, with evidence when they are not.

## Principles

- **Governance without orchestration.** Please Behave governs outcomes and not how they are produced ([DEC-0001](decisions/DEC-0001.yaml)).
- **Agent-agnostic.** It is independent of coding agents and AI providers. Executable adapters connect providers, and the product supplies none.
- **Verification as code.** Governance definitions live next to the source. They are declarative, version-controlled, human-readable and reviewable.
- **Evidential weight.** Deterministic and probabilistic verification stay distinguishable ([DEC-0002](decisions/DEC-0002.yaml)).
- **Explicit enforcement.** Quality gates prevent progression when required conditions are not satisfied. A violation is distinguished from a technical failure to verify. A locally bypassable hook is no unconditional guarantee, and verification in CI is the authoritative one.
- **Actionable and auditable results.** Results are structured and machine-readable. They state what was evaluated, the outcome, the evidence, the violations, what prevented verification and which source state was evaluated.
- **Minimal complexity.** Keep each component focused on its responsibility. Add services, storage and extension points only when the product needs them.

## Guiding question

Does this make development expectations easier to define, verify, enforce or understand without unnecessarily taking control of the development process? If not, it probably does not belong in Please Behave.

## Artifacts

- [DEC-0001](decisions/DEC-0001.yaml) Governance Without Orchestration
- [DEC-0002](decisions/DEC-0002.yaml) Verdicts Carry Their Evidential Weight
- [DEC-0003](decisions/DEC-0003.yaml) One Repository per Component
- [DEC-0004](decisions/DEC-0004.yaml) Rust for the CLI and Services
- [DEC-0005](decisions/DEC-0005.yaml) CLI Binary and Service Images
- [DEC-0006](decisions/DEC-0006.yaml) Component-Owned Versioned HTTP Contracts
- [DEC-0007](decisions/DEC-0007.yaml) Public Access Through a Proxy
- [DEC-0008](decisions/DEC-0008.yaml) Attestations Carry Reported Evidence
- [DEC-0009](decisions/DEC-0009.yaml) Shared Visual Identity
- [DEC-0010](decisions/DEC-0010.yaml) Stable Rule Identity
- [DEC-0011](decisions/DEC-0011.yaml) Owner-Assigned Rule Versions
- [DEC-0012](decisions/DEC-0012.yaml) Rule Version Registration
- [DEC-0013](decisions/DEC-0013.yaml) Verification Against Rule Registrations
- [DEC-0014](decisions/DEC-0014.yaml) Rule Knowledge in Registrations
- [DEC-0015](decisions/DEC-0015.yaml) Rule Registration Ownership
- [DEC-0016](decisions/DEC-0016.yaml) Rule Set Identity and Versions
- [DEC-0017](decisions/DEC-0017.yaml) Rule Set Version Registration
- [DEC-0018](decisions/DEC-0018.yaml) Rule Sets Bound in Attestations
- [DEC-0019](decisions/DEC-0019.yaml) Rule Set Compliance
