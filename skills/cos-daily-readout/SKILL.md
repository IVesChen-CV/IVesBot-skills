---
name: CoS Daily Readout
description: >-
  Use this when running a scheduled or on-demand Chief of Staff daily readout
  across connected tools, routines, and teammates.
---
# Chief of Staff Daily Readout

## Preconditions & Sources
- Check live connector status first; scan only currently connected sources (such as Slack, email, calendar, meeting notes, GitHub, Origin, active routines, and teammates).
- Silently skip unconnected or unauthenticated sources; never fabricate or infer data from disconnected apps.
- Track a last-run watermark (timestamp or cursor) so scheduled runs report deltas only.

## Steps
1. Query connected sources read-only for updates since the last watermark.
2. Filter out low-signal noise and map each meaningful change to the user's active priorities.
3. Classify findings as `P0` (urgent / blocking today), `P1` (important / decision needed soon), or `P2` (FYI / monitor).
4. Update the last-run watermark after completing the scan.

## Output Schema
- Present the readout in the user's preferred language, ordered `P0` -> `P1` -> `P2`:
  `- [P0/P1/P2] Title — [Source](url) — Why it matters — Next action / Owner`
- Every item must cite an exact URL, PR/issue link, file path, or teammate reference.
- Report any failed or unreachable connected source plainly.

## Stop & Safety Rules
- **Quiet-on-empty**: On scheduled routine runs, stay completely silent if nothing new reaches P0–P2.
- **No unasked actions**: Never send external messages, merge or approve PRs, or mutate files on your own; stop at a summary, draft, or proposal for user confirmation.
