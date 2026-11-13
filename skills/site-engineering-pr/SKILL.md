---
name: Site Engineering PR
description: >-
  Use this when implementing approved website copy and design specs into a Vite
  + React repo via CloudAgent PRs and verified build/preview checks.
---
# Site Engineering PR

Use this workflow to implement approved website copy and design specs into a Vite + React personal website via CloudAgent pull requests.

## Steps

1. **Confirm inputs and repository.**
   - Verify you have locked copy (from `Copy Humanizer`), concrete UI/UX specs (from `Atelier`), and the target repository URL from IVes (never guess the repo URL).
   - Never clone repositories locally or edit repo files via local Shell; route all code, build, and media/API work to `CloudAgent`.

2. **Launch CloudAgent cleanly.**
   - Hand `CloudAgent` the problem, locked copy, design spec, constraints, and verification requirements (typecheck, Vite production build, responsive/console check, preview screenshot if applicable).
   - Keep prose and PR descriptions terse and unslopped; apply `pstack` / `poteto-mode` and `blast-radius` situationally.

3. **Verify, route QA & update ledger.**
   - Confirm build/typecheck passed and inspect the PR diff/checks before reporting.
   - Send preview screenshots or URL to `Atelier` via `SendToAgent` (`priority: true`) for visual QA first; fix visual regressions in the same `CloudAgent` thread.
   - Whenever sending QA requests, spec/copy clarifications, or PR completion reports via `SendToAgent`, **ALWAYS set `priority: true`** (`priority: false` **only** for passive FYIs where no reply or action is expected).
   - Update your own task/nested `children[]` entries in `/workspace/handoff_ledger.json` (status `pending | in_progress | waiting_review | closed | blocked`) via locked atomic read-modify-write, and mark an entry `closed` only once the receiving owner confirms receipt or deliverable completion.
   - Present the verified PR link and evidence to IVes (or via `Chief of Staff`) for merge confirmation; never merge or deploy production unasked.
