# Stack standard

Version 1 · 2026-10-14 · Owner: Web & SEO

## Default stack (marketing sites)

| Layer | Default | Notes |
|---|---|---|
| Build tool | Claude Code | Lovable is not in the production path. |
| Framework | Astro 7, static output | Zero JS by default; islands only where a component needs it. |
| Styling | Tailwind CSS 4, tokens from `tokens.json` as CSS variables | |
| Interactive islands | React, `client:visible` | Only when a component needs state. |
| Motion | CSS → View Transitions → Motion (`motion`, vanilla API) → GSAP | See `motion.md`. |
| Languages | Astro i18n routing | Only when one site serves two markets. Separate content, not translation. |
| Images | Astro `<Picture>` (AVIF/WebP, responsive) | Sources and provenance per `imagery.md`. |
| AI images and video | fal MCP for stills and retouching; Higgsfield (CLI + skills) for video | Picks, costs and rules in `capabilities.md`. |
| UI components | 21st.dev (Claude Code plugin or CLI) | Parts bin only, after `direction.md`; rules in `capabilities.md`. |
| Client-editable content | Keystatic + Keystatic Cloud | Free up to 3 editors per team; content stays in the repo. The admin route needs the Cloudflare adapter; marketing pages stay prerendered. |
| Forms, booking, reviews | GoHighLevel forms and widgets from the client's sub-account | No custom form backends. |
| App data (only if needed) | Supabase | Portals, dashboards, auth. |
| Hosting | Cloudflare Workers, static assets | Auto-deploy from `main`. |
| Analytics and search | GA4, Google Search Console, Bing Webmaster Tools + IndexNow | |
| Code repo | One repo per site under `soyjavo/` | Named on the Site record. Stage artifacts live in `aifactory-web/sites/<slug>/`. |

## Hosting accounts

Cloudflare's self-serve terms forbid signing up on behalf of a third party.

- Own brands (AI Factory Systems, InteliMX, AIFactory Health): the company Cloudflare account.
- Client sites: the client's own Cloudflare account with us invited, or the Cloudflare Self-Serve Agency program. Never a client site on the company account.
- Vercel Hobby is never used for paid work: its terms count consultant-built and paid-hosting sites as commercial.
- Netlify: legacy only, no new sites. On Netlify's credit-based Free plan, one project going over its limit pauses every project on the account until the next cycle, so client sites never sit on a Free account. A Netlify site moves to Cloudflare when it enters a redesign run.

## Exceptions

A different stack needs a reason written in the Site record's "Stack exception reason".

- **TanStack Start 1.x**: sites that are really apps, or existing healthy TanStack sites (Lovable has generated these since May 2026). Prerender the marketing routes.
- **Next.js**: only app-heavy builds that need it.
- **Existing healthy sites are not migrated** to match the default. A site moves to the default when it enters a redesign run.

## Lovable

- Plan: Free. GitHub sync (all plans), existing projects, published pages and already-connected custom domains keep working on Free. New custom domains need a paid plan.
- **Lovable Cloud and AI features run on credits.** A project using Lovable Cloud (database, auth, storage, server functions) or AI at runtime depends on Lovable credits even when its front end is hosted elsewhere. Free grants 20 Cloud and 4 AI credits a month; when they run out, the backend and AI pause until the 1st of the month. Pages keep serving; data is kept but can't be exported while paused. Move such backends to our own Supabase before downgrading.
- Allowed: a quick client-facing concept during S2. Re-subscribe to Pro monthly for that sprint only.
- Not allowed: the production code path. Code lives in GitHub and is edited with Claude Code.

## Claude Code setup

- MCP servers: Astro Docs (`https://mcp.docs.astro.build/mcp`) and fal (`https://mcp.fal.ai/mcp-relay`). Template in `.mcp.json`; copy it into each site repo.
- Higgsfield: `npm i -g @higgsfield/cli`, then `higgsfield auth login`. Its skills (`higgsfield-ai/skills`) are reviewed and pinned first, per `VENDOR.md`.
- 21st.dev: the Claude Code plugin (`/plugin marketplace add 21st-dev/claude-code-plugin`, then `/plugin install 21st@21st`) or `npm i -g @21st-dev/cli` and `21st login`.
- Skills: `.claude/skills/VENDOR.md`.

## Changelog

- 2026-10-14: v1. Default moves from "Lovable + Claude Code → Netlify" to "Claude Code + Astro → Cloudflare". Lovable downgraded to Free.
- 2026-10-22: Added the Lovable Cloud credit dependency and the Netlify legacy-hosting rule.
- 2026-10-22: Added AI images and video (fal, Higgsfield) and UI components (21st.dev).
