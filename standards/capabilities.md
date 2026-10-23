# Capabilities standard

Version 1 · 2026-10-22 · Owner: Web & SEO

What we can produce for a site, what each option costs, and where it's allowed. S2 concepts are built only from this list. Models change fast: review this file every quarter, and whenever a new model tops the leaderboards.

## Approach first

Before any concept, S0 records on the brief and on the Site record:

- **Experience level:** Calm (default for health and clinic sites) or Expressive (own brands, by choice).
- **Production budget:** generation spend and hours.
- **Real assets available:** photos, footage, premises, brand files.

## The catalog

| Option | Good for | Cost and effort | Weight and phones | Calm | Expressive |
|---|---|---|---|---|---|
| CSS effects and View Transitions | Polish; continuity between pages | Free; minutes | ~0 KB | Yes | Yes |
| Motion islands | Reveals, counters, tabs, small interactions | Free | ≤ 15 KB JS on Calm | Yes | Yes |
| AI stills | Environments, objects, textures, visual metaphors | ~$0.01–0.11 per image; several tries | A normal image | Yes, never people as staff or patients | Yes |
| AI retouch of real photos | Consistent light and color across real staff and premises photos | Cents per image | A normal image | Yes | Yes |
| Looping hero video | A cinematic first screen | ~$0.75–1.50 per 5–10 s take at 720p (1080p costs more); 4–5 takes per keeper | ≤ 2 MB Calm, ≤ 5 MB Expressive; poster image with reduced motion or Save-Data | Yes, objects and places only | Yes |
| Scroll-driven video | A short story told by the scroll | Same clips plus build time | Heavy on phones: poster or simplified sequence there | One per site, desktop-first | Yes |
| Chained clips | One continuous camera move across sections (first/last-frame control) | More takes; careful storyboard | Adds up per clip | No | Yes |
| HyperFrames | Exact on-brand animation as video: logo, UI demo, "how it works", data | Free; Claude writes it in HTML | Small | Yes | Yes |
| Interactive tools | Service finders, cost estimators, quizzes | Hours | Small | Yes | Yes |
| 3D / WebGL / shader backgrounds | Interactive objects, live backgrounds | High | Heavy | No | With a reason and a performance check |

## Current tool picks

Recheck every quarter.

| Job | Pick | Reached from Claude Code via |
|---|---|---|
| Stills | GPT Image 2.5, Nano Banana 2.1 | fal MCP |
| Retouch | See `imagery.md` | fal MCP |
| Video | Seedance 2.0 for hero quality; Kling 3.0, Wan or MiniMax as alternates; first/last-frame interpolation for chained clips | Higgsfield: CLI plus its skills in Claude Code (Higgsfield recommends the CLI over its MCP for coding agents; the MCP is for Claude chat). fal or the model's own API per call when Higgsfield doesn't carry a model or costs more. |
| UI components | 21st.dev: React + Tailwind components in shadcn format, installable from Claude Code | Its Claude Code plugin or CLI. Rules below. |
| Programmatic video | HyperFrames | Its Claude Code plugin |
| Compression | FFmpeg: H.264 MP4 plus WebM, AVIF/JPG poster, optional frame sequence | Shell |
| Scroll binding | CSS scroll-driven animations where supported; Motion `scroll()`; GSAP only with a written reason | — |

## Higgsfield

- One account reaches Seedance 2.0, Kling 3.0, Veo 3.1, Sora 2, Wan, MiniMax, Nano Banana Pro and others, billed in credits.
- Paid plan only: the Free plan has no Seedance and no commercial use. Check the output-rights terms before the first client clip.
- Credits don't roll over, so subscribe month to month in production months only, the same way as Lovable.
- Rough cost: about 23 credits per 5 s Seedance 2.0 clip at 720p and 45 at 1080p (Aug 2026), with 4–5 takes per keeper. Per clip this runs higher than calling an API directly; it buys one account, one login and agent skills. Compare after the pilot.
- The CLI session is the account: Claude Code spends real credits. Set the clip count and budget in `storyboard.md` before generating.

## 21st.dev

- A parts bin for interactive patterns once `direction.md` is set (pricing toggles, marquees, tabs, booking steps). Never the design source: browsing it first leads straight to the banned defaults.
- Restyle every component to `tokens.json`. If it needs no state, convert it to an Astro component so it ships no JavaScript.
- Its JavaScript counts against the motion budget. Shader backgrounds follow the 3D / WebGL row.
- Licenses are set per component by each author, and 21st's terms grant no blanket commercial license. Check each one and log it in `assets.md` before it ships in a client site.
- Plan: Free (2 installs a day) to start; Builder ($72 a year) once it's used weekly. The AI generation tier isn't needed: Claude Code writes components.

## Hard limits

- No AI-generated people presented as staff, patients or customers (`imagery.md`). Seedance also blocks real faces as a starting frame; don't work around it.
- Real premises get ambient motion only (light, sky, foliage). Nothing added, removed or changed.
- Every signature moment still works with motion off: a poster image and the same message in text.
- Video never autoplays with sound, and never sits in the first screen without a poster.
- Every generated still and clip is logged in `assets.md`: model, prompt, frames used, takes, cost.

## Changelog

- 2026-10-22: v1.
- 2026-10-22: Higgsfield (video) and 21st.dev (UI components) added, with rules.
