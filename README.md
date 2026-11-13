# IVesBot-skills

Shared skills for a personal or academic website and for auditing the bot fleet. Each skill lives at `skills/<slug>/SKILL.md`.

| Skill | Path | Use when |
| --- | --- | --- |
| Site Content Architecture | `skills/site-content-architecture/SKILL.md` | Turning manuscripts, notes, and an existing site into a site map and page briefs before any copy is written. |
| Site Page Draft | `skills/site-page-draft/SKILL.md` | Drafting English page copy (Home, About, Research, Projects) from approved briefs and source manuscripts. |
| Site Editorial Review | `skills/site-editorial-review/SKILL.md` | Proofreading and humanizing a draft, then handing it back for the author's sign-off. |
| Site Design Spec | `skills/site-design-spec/SKILL.md` | Writing UI/UX, typography, layout, responsive, accessibility, and media specs from locked copy, and visually checking PR previews. |
| Site Engineering PR | `skills/site-engineering-pr/SKILL.md` | Implementing approved copy and design specs in a Vite + React repo through CloudAgent pull requests, with build and preview checks. |
| Fleet Audit Rubric | `skills/fleet-audit-rubric/SKILL.md` | Auditing bot transcripts, pull requests, and outputs for truthfulness, role boundaries, gate order, and follow-through. |

Run the first three in that order: architecture, then draft, then editorial review. Each of those skills stops for confirmation before the next one starts. Site Design Spec and Site Engineering PR continue from locked copy into UI specs and a verified pull request. Fleet Audit Rubric is a separate check on transcripts, pull requests, and outputs.
