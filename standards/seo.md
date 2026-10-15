# SEO standard

Version 1 · 2026-10-14 · Owner: Web & SEO

Evidence tags: [O] official documentation · [S] study · [C] correlation or practitioner consensus.

## Tiers

Each Site has one tier. A tier includes everything in the tiers below it.

### T1 Foundation: every site

- Page text arrives in the server's HTML; no page depends on client-side rendering for its content. [O] AI crawlers (GPTBot, ClaudeBot, PerplexityBot) don't run JavaScript. [S]
- Unique title and meta description per page; one H1; canonical URL; hreflang only for two languages.
- `sitemap.xml` generated at build, plus `robots.txt`.
- `robots.txt` allows Googlebot, Bingbot, OAI-SearchBot, Claude-SearchBot and PerplexityBot. [O] Training crawlers (GPTBot, ClaudeBot, Google-Extended) are decided per site and recorded on the Site. Search Console's "Search generative AI" setting stays on. [O]
- Structured data: Organization or the most specific LocalBusiness subtype, WebSite, BreadcrumbList. [O] Its purpose is entity clarity and rich results; it doesn't raise AI citations. [S]
- Core Web Vitals pass at the 75th percentile: LCP ≤ 2.5 s, INP < 200 ms, CLS < 0.1. [O]
- GA4, Google Search Console, Bing Webmaster Tools with IndexNow. [O]
- A real 404 page; on redesigns, a redirect for every old URL; no orphan pages.

### T2 Local: clinics and local businesses

- Google Business Profile: correct primary and secondary categories, verified address, current hours, real photos, the real business name with no added keywords. One profile per practitioner, separate from the clinic's. [O]
- Review program wired through GHL: steady requests, every review answered. No incentives, no filtering to happy patients, no staff reviews. [O] Recency matters: 74% of consumers only weigh reviews from the last 3 months. [S]
- One page per service, tied to the locations really served. It's the #1 local organic factor. [S]
- City or area pages only where the business is really present. Templated city pages fall under the scaled content abuse policy. [O]
- Clinician pages: name, real photo, credentials (MX: cédula and institution; US: license, board certification, NPI), specialties, locations. Physician or IndividualPhysician plus Person schema. [O]
- Name, address and phone identical across the site, GBP and directories.
- Directories: MX, Doctoralia first, then Topdoctors [S]. US: Zocdoc, Yelp, Healthgrades [S]; Bing Places [O].
- Contact path by market: WhatsApp first in MX, call first in the US, reachable from every page.

### T3 Authority: sites that compete on information

- Health content carries a named medical reviewer and dates, and stays consistent with expert consensus. [O]
- Mentions in local press, medical associations and "best of" lists, the top AI-search factor in Whitespark's 2026 report. [S][C]
- Real refreshes on a schedule, not date bumps. Pages cited by AI tend to be fresher. [S]
- AI-visibility tracking (see `s8-cycle.md`).
- Content at volume belongs to another department; T3 sites state that dependency.

## Not doing

- llms.txt: Google Search doesn't use it (2026-06-15). [O]
- FAQ rich results: removed 2026-05-07. FAQ content stays where it helps people. [O]
- Review stars marked up on our own LocalBusiness pages. [O]
- Keywords added to GBP names. [O]
- Mass-produced location or service pages. [O]
- Rewriting or "chunking" pages for AI. [S]

## Measurement

- Search Console Performance plus its Generative AI report (impressions only).
- Bing Webmaster Tools AI Performance report.
- GA4 referrals from chatgpt.com, perplexity.ai and gemini.google.com.
- Monthly AI-visibility probe (`s8-cycle.md`).

## Changelog

- 2026-10-14: v1.
