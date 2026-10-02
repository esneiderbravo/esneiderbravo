# Lawbook — esneiderbravo

The process law of the project — see [`../../LAWS.md`](../../LAWS.md). This
repo is spec-driven through speclaw's **spec** module (no external CLI; the
mechanical steps are speclaw MCP tools).

## The loop

No non-trivial change lands without a lawbook change. The default execution
model is **Cortex** (*One brain. Many agents.*): the host primary agent is the
**coordinator** (`cortex` skill / MCP `cortex`) and dispatches explorer → planner →
implementer → reviewer → tester → archiver. State lives in
`lawbook/changes/<name>/harness.json` (`speclaw cortex`). Lawbook owns specs
and ceremony; Cortex owns the multi-agent loop. Cheat sheet:
[`../cortex.md`](../cortex.md).

1. **explore** (explorer) — think an idea through before committing (writes nothing under `lawbook/`).
2. **draft** / **quick** (planner) — create `lawbook/changes/<name>/` artifacts for the confirmed ceremony level. Questions go to the human via the coordinator.
3. **build** (implementer) — implement the tasks; hand off before final gates.
4. **review** (reviewer) — `reports/review.md` PASS/FAIL (skipped at level 0).
5. **test** (tester) — quality gates, manual verification, discipline reports. This repo has no test runner; the gate is the rendered profile and a green Metrics workflow.
6. **sync** / **archive** (archiver) — reconcile, sync when the level requires specs, then archive within the same PR. Gated on Cortex verdicts plus tasks, reports, and sync.

## Ceremony

Artifact volume follows the confirmed level in `change.json`. A missing
`change.json` means level 3 (full ceremony). `speclaw quick` scaffolds level 0.
`speclaw lawbook level` / `lawbook_level` proposes, sets, or promotes a level.
Optional `ceremony:` cuts live in `lawbook/config.yaml` (default `[3, 8, 15]`).

| Level | When | Artifacts |
| --- | --- | --- |
| 0 | One-liner, typo, or docs-only | `record.md` + `reports/` |
| 1 | Small fix with a delta | `record.md` + `tasks.md` + at least one delta + `reports/` |
| 2 | Normal feature | `proposal.md` + `tasks.md` + deltas + `reports/` (`design.md` optional, with a justification when omitted) |
| 3 | Full ceremony | `proposal.md` + `design.md` + `tasks.md` + deltas + `reports/` |

Not every change needs all four of proposal, design, tasks, and delta specs.

## Mandatory task steps

`tasks.md` MUST include the steps defined in `lawbook/config.yaml` and the
`spec-tasks-mandatory-steps` rule when the ceremony level requires `tasks.md`.
The **tester** role performs the manual verification — never the user. The
coordinator does not archive without a test PASS.

## Reports

Every change carries a `reports/` folder. The tester writes one discipline
report per area it touched (`backend.md`, `frontend.md`, …) with the commands
run and their real output. The reviewer writes `reports/review.md`. Archive is
blocked until that evidence exists and the harness verdicts are complete.

## Delta specs

- Normative requirements use SHALL/MUST.
- Requirement headers use `### Requirement:`.
- Scenario headers use exactly `#### Scenario:`.
- Acceptance criteria are testable without production integrations.
- The implemented code must match what the delta spec promises. Validate with
  `lawbook_change` (canonical) before syncing or archiving. `lawbook_validate`
  remains a deprecated alias.
- `speclaw coverage` / `lawbook_coverage` tracks `req~name~1` to implementation
  and tests via `// Covers:` comments. `speclaw drift` / `lawbook_drift` checks
  sealed spec↔code anchors in `lawbook/anchors/*.json`.

## Archiving discipline

Always archive with the `archive` command / `lawbook_archive` tool, never a manual
`mv` — the tool performs the spec promotion and validation a manual move skips.

Before archiving, the agent runs a reconciliation review: it compares what was
built against the delta specs and, when the code has drifted past the original
contracts, shows short insights and reconciles the delta specs.

The engine refuses to archive while any required task is unchecked, while
`reports/` holds no discipline report, while delta specs required by the level
are not yet synced, or while harness review/test verdicts are not PASS.
Reconcile, `sync` when the level needs it, then archive — inside the same PR.

## Amendments to the law

The standards in `docs/standards/` are amended like code: through a spec change
reviewed by a human. An agent may propose an amendment; it may never silently
ignore a standard.
