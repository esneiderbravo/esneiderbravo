# speclaw — operating notes

Tooling notes for this repo. The agent contract is [`../AGENTS.md`](../AGENTS.md).
Compass: [`compass.md`](compass.md). Cortex: [`cortex.md`](cortex.md). Lawbook:
[`standards/lawbook.md`](standards/lawbook.md).

- Install and refresh with `npx @esneiderbravo/speclaw@latest init`. `speclaw update` migrates this project only; it does not run `npm install -g`. Upgrade a stale CLI separately (`npm i -g @esneiderbravo/speclaw@latest` or `npx @esneiderbravo/speclaw@latest update`).
- Support report: `speclaw doctor --json` (redacted by default).
- `speclaw budget` reports always-on context cost. `speclaw init --minimal` or `SPECLAW_MINIMAL=1` omits setup MCP tools. There is no server-side `defer_loading`.
- Coverage: `speclaw coverage` / `lawbook_coverage` (`req~name~1`, `// Covers:` comments). Drift: `speclaw drift` / `lawbook_drift` (committed `lawbook/anchors/*.json`, body and norm hashes). Compass schema is 10 — reindex with `speclaw index`, then `speclaw drift --reseal` once after an upgrade.
- Integrity: `speclaw.lock` at the repo root. `speclaw laws lock` / `scan`. `speclaw laws accept` is interactive TTY only, never via MCP. `speclaw verify` folds integrity findings with deps and graph laws. Strict paths include `AGENTS.md`, `CLAUDE.md`, and compiled rules; standards docs are advisory.
- Canonical MCP tools (nine): `compass_explore`, `compass_find`, `compass_diff_context`, `compass_index`, `lawbook_change`, `lawbook_investigate`, `speclaw_setup`, `speclaw_check`, `cortex`. Retired names (`compass_search`, `lawbook_validate`, `init_project`) are deprecated aliases. `scaffold`, `doctor`, `compass_visualize`, and `law_verify` are CLI-only. The minimal profile omits setup, check, investigate, and index.
- `compass_impact` is grouped by default (`format: flat` for a flat list). `compass_affected_tests` / `speclaw affected-tests --from-diff`. `compass_hotspots` / `speclaw hotspots` and `compass_coupling` / `speclaw coupling` (default history window 90 days).
- Optional `team.owners` in `lawbook/config.yaml` maps capabilities to owners. `speclaw owners --write` compiles a managed block at the end of `.github/CODEOWNERS`. This repo does not declare owners.
- CI consumers use `esneiderbravo/speclaw@v2`. speclaw never turns on branch protection; add the `speclaw` check as a required status check yourself if pull requests should be gated on it.
