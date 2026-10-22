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
| 3D / WebGL | Interactive objects | High | Heavy | No | With a reason and a performance check |

## Current tool picks

Recheck every quarter.

| Job | Pick | Reached from Claude Code via |
|---|---|---|
| Stills | GPT Image 2.5, Nano Banana 2.1 | fal MCP |
| Retouch | See `imagery.md` | fal MCP |
| Video | Seedance 2.0 / 2.5 for hero quality; Kling, Wan or MiniMax as alternates | fal or Higgsfield MCP. Confirm which offers Seedance 2.x, and at what price, in the first pilot run. |
| Programmatic video | HyperFrames | Its Claude Code plugin |
| Compression | FFmpeg: H.264 MP4 plus WebM, AVIF/JPG poster, optional frame sequence | Shell |
| Scroll binding | CSS scroll-driven animations where supported; Motion `scroll()`; GSAP only with a written reason | — |

## Hard limits

- No AI-generated people presented as staff, patients or customers (`imagery.md`). Seedance also blocks real faces as a starting frame; don't work around it.
- Real premises get ambient motion only (light, sky, foliage). Nothing added, removed or changed.
- Every signature moment still works with motion off: a poster image and the same message in text.
- Video never autoplays with sound, and never sits in the first screen without a poster.
- Every generated still and clip is logged in `assets.md`: model, prompt, frames used, takes, cost.

## Changelog

- 2026-10-22: v1.
