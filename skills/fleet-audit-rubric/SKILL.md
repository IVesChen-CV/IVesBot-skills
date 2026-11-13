---
name: Fleet Audit Rubric
description: >-
  Use this when auditing bot transcripts, PRs, and outputs for truthfulness,
  boundary compliance, gate order, and continuous improvement loops.
---
# Fleet Audit Rubric

Use this workflow to independently audit the Grok Bot fleet for factual truthfulness, boundary compliance, gate order, and continuous improvement.

## Steps

1. **Gather evidence (read-only).**
   - Inspect recent bot activity via `SearchTranscripts` / `ReadTranscript`, plus `/workspace/handoff_ledger.json`, live `profile.json`, `workflows/`, `automations/`, and read-only GitHub/WebFetch checks.
   - Cite exact transcript session IDs, message IDs, ledger task IDs, PR URLs, or file paths for every finding; never guess.

2. **Score the 5 rubric checks.**
   - **Truthfulness**: Zero fabricated facts, metrics, URLs, or unverified completion claims.
   - **Anti-job boundaries**: Each bot stays inside its role (e.g., `Atelier` writes no code, `Forge` writes no original copy, `Folio` touches no repo).
   - **Gate order**: Website pipeline honors `Folio` -> `Writing Bot` -> `Copy Humanizer` -> `Atelier` -> `Forge` -> IVes approval, and open handoffs/nested `children[]` are accurately tracked in `/workspace/handoff_ledger.json`.
   - **Verification**: Claims of done are backed by live readback, build output, or screenshot proof.
   - **User preferences**: Replies to IVes use concise Traditional Chinese with low slop; inter-agent notes stay structured.

3. **Drive fixes and report.**
   - **Inter-agent wake-up & ledger rules**: On `SendToAgent`, **ALWAYS set `priority: true`** for any `[AUDIT-FIX]` ticket, patch proposal, review request, or action item where the target bot must act or reply (`priority: false` **only** for passive FYIs/CCs). Track open `[AUDIT-FIX]` tickets in `/workspace/handoff_ledger.json` (via locked atomic read-modify-write, without overwriting sibling entries) and close them only when the fix is verified.
   - **P0/P1 violations**: Send `[AUDIT-FIX]` via `SendToAgent` (`priority: true`) directly to the responsible bot with evidence and required fix, and CC `Chief of Staff` (`priority: false`).
   - **Recurring drift (>= 2 occurrences)**: Send a concrete skill/prompt patch proposal to `dr eggbot` via `SendToAgent` (`priority: true`) and notify `Chief of Staff`.
   - **Scorecard**: Deliver a concise Traditional Chinese scorecard directly to IVes (`Pass / Warn / Fix-Required` per bot, closed fixes, open blockers) and CC `Chief of Staff` (`priority: false`).
   - On scheduled runs with zero new issues or proposals, stay completely silent. Never edit another bot's profile, skills, or routines directly, and never merge PRs or send external messages.
