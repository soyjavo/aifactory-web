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

## Exceptions

A different stack needs a reason written in the Site record's "Stack exception reason".

- **TanStack Start 1.x**: sites that are really apps, or existing healthy TanStack sites (Lovable has generated these since May 2026). Prerender the marketing routes.
- **Next.js**: only app-heavy builds that need it.
- **Existing healthy sites are not migrated** to match the default. A site moves to the default when it enters a redesign run.

## Lovable

- Plan: Free. GitHub sync, existing projects, published apps and already-connected custom domains keep working on Free. New custom domains need a paid plan.
- Allowed: a quick client-facing concept during S2. Re-subscribe to Pro monthly for that sprint only.
- Not allowed: the production code path. Code lives in GitHub and is edited with Claude Code.

## Claude Code setup

- MCP servers: Astro Docs (`https://mcp.docs.astro.build/mcp`) and fal (`https://mcp.fal.ai/mcp-relay`). Template in `.mcp.json`; copy it into each site repo.
- Skills: `.claude/skills/VENDOR.md`.

## Changelog

- 2026-10-14: v1. Default moves from "Lovable + Claude Code → Netlify" to "Claude Code + Astro → Cloudflare". Lovable downgraded to Free.
