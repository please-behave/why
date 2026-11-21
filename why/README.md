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
- **Minimal complexity.** A small, self-contained native executable. No speculative extensibility, and no services or databases the product does not need.

## Guiding question

Does this make development expectations easier to define, verify, enforce or understand without unnecessarily taking control of the development process? If not, it probably does not belong in Please Behave.

## Artifacts

- [DEC-0001](decisions/DEC-0001.yaml) Governance Without Orchestration
- [DEC-0002](decisions/DEC-0002.yaml) Verdicts Carry Their Evidential Weight
