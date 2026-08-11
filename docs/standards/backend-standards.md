# Backend / Automation Standards — esneiderbravo

Rules for executable logic. A law of the project — see [`../../LAWS.md`](../../LAWS.md).
Architecture and boundaries: [`architecture.md`](architecture.md).

> **This repo has no application backend.** There are no services, endpoints, or
> persistence. The only executable logic is the GitHub Actions metrics workflow,
> so this standard governs that workflow. If application code is ever added, fill
> in the real layer table below and restore the app-backend rules.

## The only executable logic — the metrics workflow

| Piece | File | Responsibility |
|-------|------|----------------|
| Workflow definition | `.github/workflows/metrics.yml` | Triggers (daily cron, manual dispatch, self-change push), permissions, and the ordered `lowlighter/metrics` steps |
| Overview step | `metrics.yml` → `Overview stats` | Regenerates `metrics.base.svg` (stats, repositories), themed via `extras_css` |
| Languages step | `metrics.yml` → `Languages` | Regenerates `metrics.langs.svg` (top 8 most-used), themed via `extras_css` |
| Generated outputs | `metrics.base.svg`, `metrics.langs.svg` | Committed assets — outputs only, never hand-edited |

### Workflow rules — strictly enforced

- **Least privilege.** Keep `permissions:` scoped to exactly what the job needs
  (currently `contents: write` to commit the SVGs). Do not broaden it.
- **Secrets only via GitHub secrets.** Authenticate with `${{ secrets.METRICS_TOKEN }}`.
  Never inline a token or PAT.
- **Outputs are generated, not authored.** `metrics.*.svg` are produced only by
  this workflow. Never hand-edit them; regenerate by running the Action.
- **Theme in `extras_css`, in brand tokens.** Styling changes go through the
  step's `extras_css`, using the teal brand palette (see
  [`base-standards.md`](base-standards.md)). Keep the timezone
  (`America/Bogota`) consistent across steps.
- **Comment the non-obvious.** Each step carries a `#` comment explaining intent,
  as the file already does. Keep that density.

## Formatting & linting

- **Lint / type-check command**: No linter configured. Optional Markdown hygiene:
  `npx --yes markdownlint-cli2 "**/*.md"`. Validate `metrics.yml` as valid YAML
  before pushing (any YAML linter, or rely on the Action failing fast).

## Docstrings & typing

Not applicable — there is no docstring-bearing or typed code (no Python/TS/etc.).
The workflow YAML is documented with `#` comments instead; see
[`documentation.md`](documentation.md).

## Tests

- **Test command**: No test runner (no application code). A workflow change is
  verified by running the Action (manual `workflow_dispatch`) and confirming it
  completes green and produces the expected SVGs — see
  [`testing-standards.md`](testing-standards.md).

## Migrations

Not applicable — there is no database or schema.
