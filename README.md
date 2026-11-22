# Why

Why is a documentation approach that puts the reasons first. The name is an acronym with a pun: **W** is for What, **H** is for How and **Y** is for Why, and the English word "why" is pronounced like the letter Y.

## Approach

Code shows what a system does. It rarely says why it does so, and it can drift away from what was intended. Why keeps the business view next to the code:

- **Requirements** state what the product must satisfy.
- **Decisions** record why it is the way it is.
- **Components** assign the large building blocks and their responsibilities, and so show how the product is built.
- **Rules and rule sets** carry a rationale for the same reason: it orients people and agents when they change them.

The documentation leads. It is the source of truth. If code and documentation disagree, either the code is changed or the documentation is corrected afterwards, and the difference is judged explicitly. Neither silently wins.

Why describes the present: what exists and why. Ideas for the future belong in [vision.md](vision.md) and become requirements and decisions once they exist.

## Layout

Every repository keeps the Why of its own component in a `why/` directory. This repository holds the Why that spans several components: the building blocks of the product and the decisions and requirements that concern more than one of them.

Shared decisions live here. Component-specific decisions and contracts stay in the repositories that own them. [DEC-0003](why/decisions/DEC-0003.yaml) defines how to cite artifacts across repositories.

## Repositories

| Repository | Responsibility |
|---|---|
| `cli` | The `please` executable: configuration, checks, reviews, reports. |
| `action` | GitHub Action that installs and invokes the CLI. |
| `gateway` | Authenticates senders, validates attestations and forwards them to the ledger. |
| `ledger` | Stores attestations and serves them for reading. |
| `cockpit` | Shows reported attestations to authorized viewers. |
| `why` | Holds the product principles, shared decisions and visual identity. |

## Documents

- [Product](why/README.md): purpose, principles and the decisions that span components.
- [Vision](vision.md): where Please Behave is heading.
- [Visual identity](brand/README.md) documents the shared logo assets, color tokens and their use.
