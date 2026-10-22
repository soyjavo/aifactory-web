# aifactory-web — Web & SEO department

This repo holds how the department works. Site code lives in each site's own repo (named on the Site record in Notion → Web & SEO → Sites).

## Layout
- `standards/` — source of truth: `stack.md`, `capabilities.md`, `taste.md`, `imagery.md`, `seo.md`, `motion.md`, `s8-cycle.md`. Mirrored to Notion.
- `templates/` — copy into `sites/<slug>/` when a stage starts.
- `sites/<slug>/` — stage artifacts: brief.md (S0), architecture.md (S1), direction.md → concepts.md → storyboard.md → assets.md → tokens.json (S2), copy/*.md (S3), seo-report.md (S5), integrations.md (S6), handoff.md (S7), cycle-YYYY-MM.md (S8).
- `.claude/skills/` — department skills and vendored third-party skills (see `VENDOR.md`).

## Rules
- Before producing a stage artifact, read the previous stage's artifact and the standards for this stage.
- S1 before S2. S2 starts from direction.md, never from a tool's defaults. S3 is written against S1.
- Approach before production: nothing is generated or built until one concept is picked and storyboarded (`standards/capabilities.md`).
- Real people stay real (`standards/imagery.md`).
- After each stage, update the Run in Notion: Stage, Next action, Artifacts.
- Changing a standard: edit the file, add a changelog line, then update the Notion mirror.
- Third-party skills: review first, vendor at a pinned commit, never auto-update.
