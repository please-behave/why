# Why

[![build](https://github.com/please-behave/why/actions/workflows/ci.yml/badge.svg?branch=main)](https://github.com/please-behave/why/actions/workflows/ci.yml) [![license](https://img.shields.io/badge/license-PolyForm%20Noncommercial%201.0.0-3949ab.svg)](https://polyformproject.org/licenses/noncommercial/1.0.0/)

Why is a documentation approach that puts the reasons first. The name is an acronym with a pun: **W** is for What, **H** is for How and **Y** is for Why, and the English word "why" is pronounced like the letter Y.

## Approach

Code shows what a system does. It rarely says why it does so, and it can drift away from what was intended. Why keeps the reasons and expectations next to the code.

- **Requirements** state what the product must satisfy.
- **Decisions** record why it is the way it is.
- **Components** assign the large building blocks and their responsibilities, and so show how the product is built.
- **Contracts** define interfaces and the obligations at those interfaces.

The documentation leads. It is the source of truth. If code and documentation disagree, either the code is changed or the documentation is corrected afterwards, and the difference is judged explicitly. Neither silently wins.

Why describes the present state and the agreed specification. Keep future proposals in a separate vision document.

## Layout

The [Why standard](standard/README.md) defines the approach, artifact schemas and cross-repository references.

The [product Why](why/README.md) holds the principles and decisions shared across Please Behave. Each component repository owns its own Why. The [repository declaration](why/repositories.yaml) records the repository identities used by shared artifacts.

## Repositories

| Repository | Responsibility |
|---|---|
| [Command-line interface](https://github.com/please-behave/cli) | The `please` executable handles configuration, checks, reviews and reports. |
| [GitHub Action](https://github.com/please-behave/action) | Installs and invokes the CLI. |
| [Gateway](https://github.com/please-behave/gateway) | Authenticates senders, validates attestations and forwards them to the ledger. |
| [Ledger](https://github.com/please-behave/ledger) | Stores attestations and serves them for reading. |
| [Cockpit](https://github.com/please-behave/cockpit) | Shows reported attestations to authorized viewers. |
| [Shared Why](https://github.com/please-behave/why) | Holds the product principles, shared decisions and visual identity. |

See the [repository declaration](why/repositories.yaml) for the aliases assigned to these sources.

## Documents

- [Product](why/README.md): purpose, principles and the decisions that span components.
- [Vision](vision.md): where Please Behave is heading.
- [Visual identity](brand/README.md) documents the shared logo assets, color tokens and their use.
