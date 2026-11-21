# Why

Central documentation of Please Behave: the direction, the reasoning and the concepts that span several repositories.

## What belongs here

- Vision and direction, including ideas that are not implemented yet.
- Cross-cutting concepts that several components share, such as identities and the trust model.
- The map of repositories and how they relate.

## What does not belong here

Requirements, decisions and API contracts describe what a component is, not what it may become. They live in the repository of the component that owns them. Nothing in this repository is binding. A text here becomes a requirement or decision in the owning repository only once it describes that component as it exists.

Component repositories reference this repository; this repository never references them back.

## Repositories

| Repository | Responsibility |
|---|---|
| `cli` | The `please` executable: configuration, checks, reviews, reports. |
| `action` | GitHub Action that installs and invokes the CLI. |
| `why` | This repository. |
| `gateway` (planned) | Receives attestations from CI runs. |
| `ledger` (planned) | Stores evidence and platform facts and serves them. |
| `cockpit` (planned) | Shows evidence, expectations and gaps. |

## Documents

- [Governance platform](governance-platform.md): the central component that makes governance visible across repositories.
