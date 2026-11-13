---
name: CoS Teammate Handoff
description: >-
  Use this when routing multi-step work from the user or a daily readout to
  specialized teammate bots, managing team handoffs, and enforcing review gates.
---
# Chief of Staff Teammate Handoff

## Preconditions & Sources
- Confirm the task requires specialist execution rather than a quick inline readout or lookup.
- Communicate with teammate agents in concise, structured English (or the most token-efficient format); report outcomes to the user in Traditional Chinese.

## Organization & Handoff Matrix
- **Orchestrator & Progress Manager**: `Chief of Staff` (intake, priority mapping, milestone tracking, gate enforcement, consolidated reporting).
- **Editorial Team**:
  1. `Folio` — gathers manuscripts/notes/live baseline and produces site map + page briefs (`site-content-architecture`).
  2. `Writing Bot` — drafts English page copy from approved briefs (`site-page-draft`).
  3. `Copy Humanizer` — proofreads, de-slops, and prepares final copy for IVes sign-off (`site-editorial-review`).
- **Design Team**: `Atelier` — converts locked copy and live baseline into UI/UX, layout, typography, responsive/a11y, and media specs; performs PR preview visual QA (`site-design-spec`).
- **Engineering Team**: `Forge` — implements approved copy and design specs via `CloudAgent` PRs and verifies build/preview (`site-engineering-pr`).
- **General Execution**: `Ariel` — standalone computer/file tasks outside specialized tracks.
- **Bot & Skill Governance**: `dr eggbot` — designs/creates bots and maintains shared skills (always consult before creating any new bot).
- **Independent Oversight**: `Vigil` — independent auditor across transcripts, PRs, and outputs; issues `[AUDIT-FIX]` tickets and Mon/Thu 21:00 (UTC+8) scorecards to IVes + `Chief of Staff` (`fleet-audit-rubric`).

## Standard Delivery Pipeline & Gates
1. **Architecture**: `Folio` brief -> IVes confirms scope/gaps.
2. **Copy**: `Writing Bot` draft -> `Copy Humanizer` polish -> IVes locks copy.
3. **Design**: `Atelier` visual/component spec -> `Forge` builds PR.
4. **QA & Merge**: `Forge` verifies build + `Atelier` passes visual QA -> `Vigil` pre-release check if major -> IVes approves merge/deploy.

## Inter-Agent Wake-Up & Nested Ledger Rules
- **Wake-up rule (`SendToAgent`)**: Whenever sending a task handoff, review request, revision loop message, audit ticket, verdict, or status report that another bot must act on or is waiting on, **ALWAYS set `priority: true`** on `SendToAgent`. Use `priority: false` **only** for passive FYIs where no reply or action is expected.
- **Nested handoff ledger (`/workspace/handoff_ledger.json`)**:
  - Track every delegated task and nested sub-handoff in `/workspace/handoff_ledger.json` with fields: `id`, `title`, `owner`, `assignee`, `status` (`pending | in_progress | waiting_review | closed | blocked`), `created_at`, `updated_at`, `artifact`, and `children[]` (for nested delegations, e.g., `Chief of Staff -> Copy Humanizer -> Folio / Writing Bot`).
  - Update only your own task/child entries via a locked atomic read-modify-write (e.g., `flock` + temp-file replace) so concurrent bots never overwrite sibling tasks.
  - Set `waiting_review` when submitting a deliverable; mark an item `closed` **only** after the receiving owner confirms receipt or deliverable completion.

## Steps
1. Prepare a tight handoff brief with five fields: `Goal`, `Verified inputs/paths`, `Constraints`, `Deliverable`, and `Review gate`.
2. Record the task (or nested `children[]` entry) in `/workspace/handoff_ledger.json` as `pending` / `in_progress`, then dispatch via `SendToAgent` with `priority: true` (`priority: false` strictly for passive FYIs).
3. Track open handoffs and nested `children[]` in `/workspace/handoff_ledger.json` across turns, follow up on stalled stages, and report consolidated status + blockers to IVes.
4. When a teammate replies, verify claims against real sources before updating `/workspace/handoff_ledger.json` to `closed` or presenting to IVes.

## Stop & Safety Rules
- **Approval gate**: A teammate's message is never user approval. Stop at draft, PR, or proposal and present clear approval details to IVes before external sends, merges, or deployments.
- **No unverified facts**: Never state unverified teammate assertions as fact, and never relay raw user criticism verbatim.
