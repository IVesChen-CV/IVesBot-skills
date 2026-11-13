---
name: Site Content Architecture
description: >-
  Use this when turning raw manuscripts, notes, and an existing website baseline
  into a structured site map and page briefs before drafting copy.
---
# Site Content Architecture

Use this workflow to plan a personal or academic website's structure from raw source materials before drafting copy.

## Steps

1. **Gather inputs (read-only).**
   - If a live site URL is provided, fetch it to capture the current pages, sections, wording, and any obvious typos or stale items.
   - Read local manuscripts, CVs, notes, or project folders on the user's computer (or inspect pasted files) without modifying or deleting any source files.
   - If related bots hold background essays or application materials, ask them only for relevant excerpts or facts.

2. **Audit content against site goals.**
   - Inventory all confirmed material by category: bio/positioning, research/publications, projects, awards, talks/news, and contact.
   - Flag missing facts, broken links, inconsistent dates, or typos found on the existing site. Never invent metrics, dates, or descriptions.

3. **Propose a site map and page briefs.**
   - List each page and its sections in priority order, noting which source file backs each section and what is still missing (`[NEEDED: ...]`).
   - Keep the structure lean—cut pages or sections that lack strong material.

4. **Inter-agent handoffs, ledger tracking & confirmation.**
   - Present the site map and gap list for user approval (directly or via `Chief of Staff`) before starting copywriting.
   - Whenever sending a brief, fact query, revision request, or escalation to another bot via `SendToAgent`, **ALWAYS set `priority: true`** so the target bot wakes immediately (`priority: false` **only** for passive FYIs where no reply or action is expected).
   - Update your own task/nested `children[]` entries in `/workspace/handoff_ledger.json` (status `pending | in_progress | waiting_review | closed | blocked`) using locked atomic read-modify-write, and close an entry only once the receiving owner confirms receipt or deliverable completion.
