# Base Standards — esneiderbravo

Cross-cutting rules that apply to **all** code in this repository, regardless
of layer or language. This is a law of the project — see [`../../LAWS.md`](../../LAWS.md).

## Languages

The working language is **inferred from this repo's own conventions** — the
language already used in docstrings, commit messages, branch names, and PR/ticket
bodies. Match what the repo does; do not impose a language it doesn't use.

- **Code, identifiers, comments, docstrings, commit messages, PR titles/bodies,
  and technical docs**: the repo's artifact language (English unless the repo
  clearly uses another).
- **User-facing product copy**: as the product requires.
- **Agent ↔ human communication** (review comments, thread replies): the same
  language the team already uses in the repo's tickets and PRs. Technical terms
  stay in English within that prose — don't force-translate them.

## Commits & branches

- **Branch naming**: Trunk-based — commits land directly on `main` (history
  shows no feature branches). For larger changes, optional short-lived
  `topic/<slug>` branches (e.g. `topic/contribution-calendar`).
- **Commit style**: Imperative mood, sentence case, English, concise; no
  conventional-commit type prefixes and no ticket IDs (e.g. "Make GitHub metrics
  section responsive; center the calendar"). Automated metrics commits are
  bot-authored and suffixed " - [Skip GitHub Action]".
- One focused change at a time; the smallest correct diff. No drive-by
  refactors mixed into an unrelated change.

## Comments & documentation

- Comments state **constraints the code cannot express** (invariants, tricky
  edge cases, "why"). They never narrate history, restate the next line, or
  address the reviewer.
- **Never** put ticket IDs, ticket text, or changelog narration
  ("added for TICKET-123", "fixed as part of…") in code or docstrings.
  Traceability lives in the branch name, PR, and git history.

## Dependencies

- Any new dependency must be justified in the PR description. Unannounced
  dependencies are a blocking finding.
- Prefer the standard library and existing project utilities before adding a
  package.

## Engineering principles

- Code reads like its neighbors (naming, structure, idioms).
- Report outcomes faithfully: if a gate fails, say so with the output; never
  claim a success you did not observe.
- Ask before irreversible or outward-facing actions (destructive commands;
  writing to a real data store — DB rows or files holding real user data,
  including to set up or tear down test data; publishing reviews/tickets/comments).

## Project-specific rules (profile repo)

- **`main` is live.** A push to `main` updates github.com/esneiderbravo
  immediately — treat every `README.md` change as a publish (see the stop
  conditions in the constitution).
- **Brand tokens are fixed.** Teal `#0E8E8E` for accents, near-black `#0B0F10`
  for badge label backgrounds, teal→cyan (`0E8E8E`→`22c9c9`) for gradients.
  Reuse these; do not introduce new palette colors.
- **Match the existing image style.** README imagery is either a committed asset
  (`./metrics.*.svg`) or a themed remote badge/card service. New badges follow
  the existing shields style (`style=for-the-badge` or `flat-square`,
  `labelColor=0B0F10`) and every `<img>` keeps a meaningful `alt`.
- **Never hand-edit generated SVGs.** Regenerate `metrics.*.svg` via the
  workflow.
- **No secrets in the repo.** The workflow authenticates only via the
  `METRICS_TOKEN` GitHub secret.

