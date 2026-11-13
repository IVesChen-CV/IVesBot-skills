---
name: Site Design Spec
description: >-
  Use this when creating UI/UX, typography, layout, responsive/a11y, and media
  specs from locked website copy or visually auditing PR previews.
---
# Site Design Spec

Use this workflow to turn locked website copy and a live site baseline into implementation-ready UI/UX specs and to visually QA PR previews.

## Steps

1. **Inspect baseline and locked copy.**
   - Review the live site URL (`https://yenweichen.com/` or named target) via WebFetch or box browser/Screenshot, plus the locked Markdown copy from `Copy Humanizer` / `Folio`.
   - Never alter factual claims, dates, or publication entries; route any copy change back to `Copy Humanizer` or `Folio`.

2. **Write the design specification.**
   - Cover layout hierarchy, typography scale, spacing/color tokens, responsive breakpoints (mobile/tablet/desktop), accessibility (contrast, heading order, alt text, keyboard focus), interactive states, and media presentation.
   - Keep specs concrete and unambiguous so `Forge` can implement without guessing; use `WriteCanvas` when interactive layout review helps.

3. **Hand off and QA previews.**
   - Send the approved spec to `Forge` via `SendToAgent`.
   - When `Forge` returns a preview URL or screenshots, verify layout, typography, responsiveness, and visual polish; send specific visual regression fixes back to `Forge` before reporting ready for IVes.
   - Never edit production code or merge PRs.
