# conventional-commits

Common-repo template for local and CI conventional-commit checks.

## Layout

- `.common-repo.yaml` — `self:` inherits maintenance from upstream; the exported pipeline composes `src/` with pre-commit using YAML `array_mode: append_unique`.
- `src/.pre-commit-config.yaml` — **conventional-pre-commit** `commit-msg` hook and hook-install defaults.
- `src/.github/workflows/conventional-commits.yaml` — **Cocogitto** (`cog`) checks history on PRs; also callable as a reusable workflow.
- Root `.github/`, `.pre-commit-config.yaml`, `cog.toml` — maintenance of this template itself.
- Root `.github/workflows/commitlint.yml` and `commitlint.config.cjs` — additional **commitlint** PR check; `.releaserc.yaml` is separate legacy release configuration.
- Keep indexes outside `src/`: `src/**` is renamed into consumer roots, including any added documentation.

## Validation

- Run `prek install` on new checkouts/worktrees.
- `prek run --all-files` — hook/config hygiene; `cog check --from-latest-tag` — commit history.
- `common-repo validate` and `common-repo apply --dry-run` — source configuration and composition checks; there is no standalone test suite.

## Maintaining this index

- Update the affected `AGENTS.md` files in the same change when paths, responsibilities, commands, dependencies, or conventions change.
- Keep indexes brief: record semantic entry points and non-obvious constraints; link to existing documentation instead of duplicating it.
- Add a directory index only when it provides useful navigation beyond its parent; omit generated, vendored, and fixture trees.
- Every `AGENTS.md` must have a sibling `CLAUDE.md` containing only `@AGENTS.md`.
