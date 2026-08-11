# Documentation Standard — esneiderbravo

The docstring/API-comment law of the project — see [`../../LAWS.md`](../../LAWS.md).
One consistent convention per language, so every public API reads the same way.
Comment *philosophy* (what a comment is for) lives in
[`base-standards.md`](base-standards.md); this file defines the *format*.

## Convention per artifact

This repo has **no docstring-bearing code** — there is no Python/TS/etc. The only
structured artifacts are the workflow YAML and the profile Markdown, so the
"documentation" convention is about them, not language docstrings.

| Artifact | Convention | What it must carry |
|----------|------------|--------------------|
| GitHub Actions workflow (`metrics.yml`) | Inline `#` comments | A comment on each step (and each non-obvious option) stating its intent, as the file already does |
| Profile Markdown (`README.md`) | Headings + `alt` text | Section headers that describe their content; a meaningful `alt` on every `<img>` |

If application code is ever added, adopt one idiomatic docstring convention for
its language (e.g. Google-style for Python, TSDoc for TypeScript) and record it
here.

## Repo-specific note

The only structured artifact with logic is the GitHub Actions workflow
(`metrics.yml`): document non-obvious steps with `#` comments, as it already
does. For the profile itself, Markdown headings and image `alt` text are the
"API docs" — every `<img>` carries meaningful `alt`, and section headers
describe their content.


## Rules

- **Required on every public API**: exported/public modules, classes,
  functions, and methods. Internal helpers get a docstring when their intent
  isn't obvious from the name.
- **Write them as you code**, not afterward — a new or changed public symbol is
  not done until it is documented.
- **Describe intent and contract** (what and why, inputs/outputs, errors), not
  a restatement of the syntax. No ticket text, no changelog narration.
- **Exempt**: trivial dunders/accessors and test functions, unless they carry
  non-obvious behavior.
- **One style per language** — never mix conventions within the same language
  in the repo.

## Enforcement

Prefer a docstring linter in the quality gates when the language has one
(e.g. `ruff`'s pydocstyle rules for Python, `eslint-plugin-jsdoc` for TS/JS).
List the concrete command in [`testing-standards.md`](testing-standards.md).
