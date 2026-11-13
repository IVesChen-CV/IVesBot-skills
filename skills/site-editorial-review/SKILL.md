---
name: Site Editorial Review
description: >-
  Use this when reviewing, proofreading, and humanizing drafted personal-website
  copy before final user sign-off.
---
# Site Editorial Review

Use this workflow to review and tighten website copy drafts for clarity, accuracy, and natural human voice before publication.

## Steps

1. **Verify facts and consistency.**
   - Check paper titles, co-author names, dates, affiliations, tags, and spelling/typos across all sections.
   - Flag any ungrounded claim or ambiguity instead of silently smoothing it over.

2. **Cut slop and tighten voice.**
   - Remove AI tells, throat-clearing openers, repetitive sentence structures, and inflated adjectives while preserving the author's voice and technical accuracy.
   - Check scannability: lead sentences should carry the point so a skimmer gets the message in 5 seconds.

3. **Show changes with rationale, hand off & update ledger.**
   - Present the polished candidate copy, followed by a concise change log (what changed and why) plus any remaining questions or revision requests.
   - Stop after presenting the edited draft; never finalize or publish without the user's explicit go-ahead.
   - **Inter-agent wake-up rule**: Whenever sending a review request, revision loop message, editorial verdict, or locked copy handoff to `Folio`, `Writing Bot`, `Atelier`, `Forge`, or `Chief of Staff` via `SendToAgent`, **ALWAYS set `priority: true`** so the recipient wakes immediately (`priority: false` **only** for passive FYIs where no reply or action is expected).
   - **Nested handoff ledger**: Track your task and any nested review sub-handoffs (`children[]`, e.g., `Copy Humanizer -> Folio / Writing Bot`) in `/workspace/handoff_ledger.json` (status `pending | in_progress | waiting_review | closed | blocked`) via locked atomic read-modify-write, and mark a handoff `closed` only after the receiving owner confirms receipt or deliverable completion.
