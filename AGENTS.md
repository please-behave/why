# Working on Why

- Write documentation in English. Keep the governance configuration compatible with the published Please Behave governor pinned in `mise.toml`.
- `brand/` holds the shared visual identity documentation and logo masters.
- [`standard/`](standard/README.md) holds the product-independent Why standard, its artifact schemas and its reference and repository declaration rules.
- [`why/`](why/README.md) holds the Why of Please Behave, including its shared decisions and [repository declaration](why/repositories.yaml). Future proposals belong in `vision.md`.
- Follow [DEC-0003](why/decisions/DEC-0003.yaml) and the [Why standard](standard/README.md#artifact-references) for cross-repository references.
- Keep every statement in one place. Reference the artifacts of component repositories and do not copy them.

## Validation

- Run `mise install`, then `mise exec -- please sync --yes` to install the Git hooks. Keep the hooks enabled for commits and pushes.
- Run `mise run verify` for the deterministic CI checks. Commit-message and CI reviews use Gemini.
- Check local Markdown links and anchors and declare any linked repositories in `why/repositories.yaml`.
