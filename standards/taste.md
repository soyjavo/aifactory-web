# Taste standard

Version 1 · 2026-10-14 · Owner: Web & SEO

Taste here is a written set of decisions made before any tool generates anything. Tools and skills carry out a direction; they never supply it.

## The S2 method

1. **The one thing.** One sentence: what this business must make a visitor believe that the competitor down the street doesn't. It comes from `brief.md`. If it can't be written, S0 isn't done.
2. **References.** 3–4 sites, at least one from outside the client's industry. Competitors are context, not references. Screenshots go to Drive.
3. **Dissection.** A table of moves (layout, type, color, imagery, motion, copy voice), with a count of how many references use each.
   - 3–4 references: territory signature. Adopt unless it conflicts with the one thing.
   - 1–2 references: candidate. Adopt only with a brand-fit reason.
   - Used by every site in the client's industry: question it. It's probably the default we're escaping.
4. **Concepts.** Three concepts built only from `capabilities.md`, within the brief's experience level and budget. Each has one signature moment that makes the one thing visible, a scroll narrative, and its cost, page weight and risks. Francisco picks; the client approves.
5. **Storyboard.** The picked concept, scene by scene: what each section explains, the medium, start and end frame prompts, video prompt, length, phone fallback, size budget.
6. **Produce.** Stills, then video, then compression. Everything logged in `assets.md`.
7. **Tokens.** Type scale, color roles, spacing, radius, shadow, motion profile → `tokens.json`.
8. **Comps.** Claude Design (`/design`, `/design-sync` against the repo) for the home page and one interior page, using the real produced assets. Iterate there, lock, then build.
9. **Pre-flight** (below), when S2 closes and again at S7.

Written in `sites/<slug>/`: `direction.md`, `concepts.md`, `storyboard.md`, `assets.md`.

## House principles

1. Specific beats generic. No section should fit a competitor's site unchanged.
2. Typography carries the identity. Two families at most: one with character for display, one workhorse for text.
3. Color is a role system. Neutrals carry the page; the brand color is an accent with a job (action, emphasis), not a wash.
4. Real over stock: real people, real place (`imagery.md`).
5. Rhythm varies. Section layouts don't repeat back to back; density changes on purpose.
6. In health, calm signals competence. Trust before flash: credentials, real faces, address and hours visible early.
7. Motion explains or rewards; it never decorates (`motion.md`).
8. The first phone screen says who, what, where, and the next step.
9. Accessibility is part of taste: WCAG 2.2 AA contrast, visible focus, 44 px targets, reduced motion.
10. The main CTA matches the market: WhatsApp first in Mexico, phone first in the US.

## Banned defaults

Allowed only when `direction.md` names the exception and the reason.

- Inter, Roboto or the system font as the display face; the current AI-default display faces (Fraunces, Instrument Serif).
- Purple-to-blue gradients, glows, blurred color blobs, glassmorphism cards.
- Beige-and-brass "luxury" or "medical blue and white" as a starting palette.
- Rows of three identical icon cards, repeated down the page.
- Centered hero with a gradient headline, two buttons and a floating dashboard screenshot.
- Full-viewport (`h-screen`) heroes that crop on phones; a hero that doesn't fit the first screen.
- Emoji as icons; generic line icons used as decoration.
- Stock people presented as staff or patients.
- Testimonial carousels without real names or a source.
- Filler copy: "Welcome to…", "We are passionate about…", "Your health is our priority".

## Pre-flight checklist

- [ ] The one thing is visible above the fold on a phone.
- [ ] No banned default without a written reason.
- [ ] Two type families at most; body text ≥ 16 px; line length 60–75 characters.
- [ ] AA contrast on all text and every CTA state; visible focus states.
- [ ] Tap targets ≥ 44 px; the main CTA reachable with one thumb.
- [ ] Every image is real, or labeled per `imagery.md`.
- [ ] No two adjacent sections share a layout.
- [ ] Forms: visible labels (not placeholder-only), inline errors, minimal fields.
- [ ] Motion profile respected; reduced motion tested.
- [ ] Empty, loading and error states designed (booking widget, blog list).

## Tools

| Tool | Role |
|---|---|
| Claude Design | S2 comps; `/design-sync` pulls in the repo's design system. |
| `frontend-design` skill | Primary design skill in Claude Code. |
| Emil Kowalski skills (web subset) | Motion craft and review. |
| Taste skill | Not installed. Its rules are folded into this standard. |
| ui-ux-pro-max | Reference only: its UX guidelines and landing-page patterns. Never its industry style or palette picks. |

## Brand notes

- InteliMX: blue palette, decorative curves.
- AI Factory Systems: purple, used as flat color (no glows, no gradients), straight-line geometry.
- AIFactory Health: provisional; keep it portable.
- Clients: derived from their own brand assets in Drive.

## Changelog

- 2026-10-14: v1.
- 2026-10-22: Concepts, storyboard and production steps added to the S2 method.
