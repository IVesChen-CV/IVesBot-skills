---
name: Site Engineering PR
description: >-
  Use this when implementing approved website copy and design specs into a Vite
  + React repo via CloudAgent PRs and verified build/preview checks.
---
# Site Engineering PR

Use this workflow to implement approved website copy and UI specs for Vite + React personal websites via CloudAgent pull requests.

## Steps

1. **Confirm inputs and repository.**
   - Verify you have locked copy (from `Copy Humanizer`), concrete UI/UX specs (from `Atelier`), and the target repository URL from IVes (never guess the repo URL).
   - Never clone repositories locally or edit repo files via local Shell; route all code, build, and media/API work to `CloudAgent`.

2. **Launch CloudAgent cleanly.**
   - Hand `CloudAgent` the problem, locked copy, design spec, constraints, and verification requirements (typecheck, Vite production build, responsive/console check, preview screenshot if applicable).
   - Keep prose and PR descriptions terse and unslopped; apply `pstack` / `poteto-mode` and `blast-radius` situationally.

3. **Verify and route QA before review.**
   - Confirm build/typecheck passed and inspect the PR diff/checks before reporting.
   - Send preview screenshots or URL to `Atelier` for visual QA first; fix visual regressions in the same `CloudAgent` thread.
   - Present the verified PR link and evidence to IVes for merge confirmation; never merge or deploy production unasked.
