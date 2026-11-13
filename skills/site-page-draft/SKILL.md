---
name: Site Page Draft
description: >-
  Use this when drafting English personal or academic website copy (Home, About,
  Research, Projects) from manuscripts and section briefs.
---
# Site Page Draft

Use this workflow to turn approved page briefs and real manuscripts into clean, publish-ready website copy.

## Steps

1. **Lock the brief and sources.**
   - Confirm which page or section is being drafted, the target audience, and the source files that ground the facts.
   - Never fabricate accomplishments, co-authors, venues, metrics, or URLs. Mark any unverified detail as `[MISSING: ...]`.

2. **Draft in plain, human prose.**
   - Lead each page or section with the clearest statement of who the person is, what they build or study, and why it matters.
   - Keep sentences short and concrete. Avoid vague superlatives ("cutting-edge", "passionate", "delve into", "harness").
   - For publications or projects, follow a consistent card format: title, collaborators/venue/year, 1–2 sentence plain summary of the problem and result, and tags/links.

3. **Deliver for review & update handoff ledger.**
   - Output clean Markdown grouped by page section so it can be reviewed or handed directly to editorial review.
   - Do not modify site code, push commits, or publish changes—stop for review or hand off to editorial review (`Copy Humanizer` / `Folio` / `Chief of Staff`).
   - **Inter-agent wake-up rule**: Whenever sending a draft for review, requesting missing facts, returning a revision, or reporting completion via `SendToAgent`, **ALWAYS set `priority: true`** (`priority: false` **only** for passive FYIs where no reply or action is expected).
   - **Nested handoff ledger**: Update your own task/nested `children[]` entries in `/workspace/handoff_ledger.json` (status `pending | in_progress | waiting_review | closed | blocked`) using locked atomic read-modify-write, and mark an entry `closed` only once the receiving owner confirms receipt or deliverable completion.
