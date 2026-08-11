# Conventions — esneiderbravo

Naming, branching, PR, and tracking conventions. A law of the project — see
[`../../LAWS.md`](../../LAWS.md).

## Branches

- Pattern: Trunk-based — commits land directly on `main` (history shows no
  feature branches). For larger changes, optional short-lived `topic/<slug>`
  branches (e.g. `topic/contribution-calendar`).
- `main` is always live; keep it publishable. Don't invent a heavier branching
  scheme than the repo actually uses.

## Pull requests

- Title and body in the repo's artifact language, following the PR template.
- If the team uses a tracker, the body references its ticket so it links; the
  ticket lives in the PR title/body only — never in the code.
- CI must be green before requesting review.

## Tracker

speclaw does not prescribe a ticket tool — each team configures its own. Follow
whatever convention this repo already uses (inferred from its branches, PRs, and
history); if there is none, leave tracker linkage to the team.

- New behavior, endpoints, schema changes, or UI flows get a spec change;
  one-line fixes need not.
- Where a tracker is in use, ticket ↔ PR traceability is expected: closing a
  ticket attaches its PR.

## Versioning & releases

No semver, no release tags, no changelog — this is a continuously-published
profile repo. `main` is the only long-lived branch and is always live: a push to
`main` updates the public profile immediately, and the metrics workflow commits
regenerated SVGs on top. There are no versioned releases.

