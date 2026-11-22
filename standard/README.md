# Why standard

A repository keeps its Why in `why/`. The artifacts record agreed requirements, decisions, implementation responsibilities and interfaces. Each schema uses JSON Schema Draft 2020-12 and applies to the data parsed from the corresponding YAML file. Keep the schema files together so their relative references resolve.

## Artifacts

| Artifact | Location | Purpose |
|---|---|---|
| [Requirement](requirement.schema.json) | `why/requirements/REQ-NNNN.yaml` | State one binding, verifiable condition and explain why it matters. Cite the decisions that shaped it, and use `obsolete: true` to retain a historical requirement. A repository may define its own `area` categories. Use `test_exemption` to explain why no automated test cites the requirement. |
| [Decision](decision.schema.json) | `why/decisions/DEC-NNNN.yaml` | Record a deliberate choice with its context and rationale. When a later decision replaces one, cite the earlier decision in `supersedes` and retain it for traceability. |
| [Component](component.schema.json) | `why/components/COMP-NNNN.yaml` | Record one implementation responsibility, its boundaries, its files and its dependencies. Use paths relative to the repository root and assign each implementation file covered by the component map to exactly one component. Cite the requirements the component implements. |
| [Contract index](contract-index.schema.json) | `why/contracts/<interface>/api.yaml` | Record an interface and its compatibility version. Each contract entry has its own ID, a document and the requirements it specifies. An entry may also point to a structural schema. Document and schema paths are relative to the index. |

Assign permanent IDs within each repository and never reuse them. Requirement, decision and component filenames match their IDs. An API index has an `API-NNNN` ID, and each of its contract entries has a repository-wide unique `CON-NNNN` ID. In all five prefixes, `NNNN` is four decimal digits.

## Artifact references

An unqualified ID such as `DEC-0001` refers to the repository containing the reference. Use `alias:ID` to refer to an artifact in a linked repository. The prefix must be an alias in the local declaration's `linked` list. An artifact's own `id` is always unqualified.

For example, a reference to decision DEC-0001 in a repository declared under the alias `shared` is written as follows.

```yaml
shared:DEC-0001
```

The [reference schema](reference.schema.json) defines the syntax and the typed references used by artifact fields. A reference must resolve to an existing artifact of the kind the field expects.

## Repository declaration

Use `why/repositories.yaml` and the [repository declaration schema](repositories.schema.json). The `repository` entry identifies the current repository. The `linked` list declares the other repositories it references and can be empty.

```yaml
repository:
  alias: handbook
  source: github:example-org/example-repo
linked:
  - alias: shared
    source: github:example-org/shared-material
```

An alias starts with a lowercase ASCII letter and may contain lowercase ASCII letters, digits and hyphens. Each alias is unique across `repository` and `linked` in one declaration, and it denotes the same repository in every declaration in the group. This lets a group retain an alias when it updates a source after a repository rename.

A source has the form `<ecosystem>:<owner>/<name>`. The defined ecosystem is `github`, whose repository URL is `https://github.com/<owner>/<name>`. A Markdown link into a linked repository uses that URL as its base. For example, a file link for the `shared` entry above can use `https://github.com/example-org/shared-material/blob/main/why/decisions/DEC-0001.yaml` when the intended revision is `main`.

## Identifying a checkout

Read a candidate checkout's `origin` remote and compare its normalized host, owner and repository name with the declared source. For a `github` source the expected host is `github.com`. Extract the owner and name from the remote path, accepting HTTPS, SSH URLs and SSH remotes of the form `git@github.com:owner/name.git`. Ignore the transport and SSH user, remove a trailing `.git` from the remote repository name, and compare the three parts case-insensitively. For example, `git@github.com:Example-Org/Shared-Material.git` and `https://github.com/example-org/shared-material` identify the same repository.

Use these coordinates regardless of the checkout's folder name. A mismatch indicates a stale declaration or the wrong checkout. This comparison uses the local environment. Snapshot validation covers declarations and artifact data, while checkout identification reads local remote configuration.

Schema validation checks data shape and reference syntax. Alias uniqueness by key, agreement between declarations, reference targets and file ownership depend on other entries or artifacts and must also follow the rules above.
