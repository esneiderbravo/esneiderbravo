# Cortex — One brain. Many agents.

Cortex is speclaw's coordinator for non-trivial changes in this repo. Lawbook
holds the specs and the ceremony level. Cortex runs the loop and stores state
in `lawbook/changes/<name>/harness.json`.

The primary agent is the **coordinator**. It does not implement the profile
change itself. It dispatches:

| Role | Stage | Owns |
| --- | --- | --- |
| explorer | exploring | Compass-first investigation; writes nothing under `lawbook/` |
| planner | planning | Ceremony level and change artifacts; questions go to the human |
| implementer | implementing | The profile change and its checks; stops at hand-off |
| reviewer | reviewing | `reports/review.md` PASS/FAIL (skipped at level 0) |
| tester | testing | Quality gates, manual verification, discipline reports |
| archiver | archiving | Sync when required, then `lawbook_archive` in the same PR |

Drive it three ways, same engine:

- In the agent: `/lawbook/cortex`
- MCP: `cortex` with `status`, `start`, `advance`, `rework`, or `brief`
- CLI: `speclaw cortex …`

Archive is gated on the harness verdicts (test PASS; review PASS when the
level is at least 1) plus tasks, reports, and sync. This repo has no test
runner: the tester's gate is that the README renders and the Metrics workflow
is green.

`speclaw cortex start --change <name>` creates the harness a change needs
before archive.
