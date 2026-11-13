---
name: Fleet Audit Rubric
description: >-
  Use this when auditing bot transcripts, PRs, and outputs for truthfulness,
  boundary compliance, gate order, and continuous improvement loops.
---
# Fleet Audit Rubric

Use this workflow to independently audit the Grok Bot fleet for factual truthfulness, boundary discipline, review gates, and continuous improvement.

## Steps

1. **Gather evidence (read-only).**
   - Inspect recent bot activity via `SearchTranscripts` / `ReadTranscript`, plus live `profile.json`, `workflows/`, `automations/`, and read-only GitHub/WebFetch checks.
   - Cite exact transcript session IDs, message IDs, PR URLs, or file paths for every finding; never guess.

2. **Score the 5 rubric checks.**
   - **Truthfulness**: Zero fabricated facts, metrics, URLs, or unverified completion claims.
   - **Anti-job boundaries**: Each bot stays inside its role (e.g., `Atelier` writes no code, `Forge` writes no original copy, `Folio` touches no repo).
   - **Gate order**: Website pipeline honors `Folio` -> `Writing Bot` -> `Copy Humanizer` -> `Atelier` -> `Forge` -> IVes approval.
   - **Verification**: Claims of done are backed by live readback, build output, or screenshot proof.
   - **User preferences**: Replies to IVes use concise Traditional Chinese with low slop; inter-agent notes stay structured.

3. **Drive fixes and report.**
   - **P0/P1 violations**: Send `[AUDIT-FIX]` via `SendToAgent` (`priority: true`) directly to the responsible bot with evidence and required fix, and CC `Chief of Staff` (`priority: false`).
   - **Recurring drift (>= 2 occurrences)**: Send a concrete skill/prompt patch proposal to `dr eggbot` (`priority: true`) and notify `Chief of Staff`.
   - **Scorecard**: Deliver a concise Traditional Chinese scorecard directly to IVes (`Pass / Warn / Fix-Required` per bot, closed fixes, open blockers) and CC `Chief of Staff`.
   - On scheduled runs with zero new issues or proposals, stay completely silent. Never edit another bot's profile, skills, or routines directly, and never merge PRs or send external messages.
