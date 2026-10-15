# S8 monthly cycle

Version 1 · 2026-10-14 · Owner: Web & SEO

Until a content department exists, every site with an active retainer gets this fixed amount of work each month. Output: `sites/<slug>/cycle-YYYY-MM.md`, plus a summary sent to the client in their channel (WhatsApp in MX, email in the US).

| # | Work | T1 | T2 | T3 |
|---|---|---|---|---|
| 1 | Crawl changes: new 404s, redirects, indexability, sitemap | ✓ | ✓ | ✓ |
| 2 | Search Console and Bing changes: clicks, impressions, queries gained and lost | ✓ | ✓ | ✓ |
| 3 | Core Web Vitals (field data where available) | ✓ | ✓ | ✓ |
| 4 | AI-visibility probe | 5 prompts | 10 prompts | 15 prompts |
| 5 | GBP check: hours, categories, photos, practitioner profiles | — | ✓ | ✓ |
| 6 | Review report: new reviews, rating, unanswered | — | ✓ | ✓ |
| 7 | Real page refresh (facts, photos, services, FAQs) | — | 1 page | 2 pages |
| 8 | Directory and NAP spot check | — | Quarterly | Quarterly |

## AI-visibility probe

- The prompt set is fixed per site in `sites/<slug>/ai-probe.md`, in the market's language (e.g. "mejor oftalmólogo en Tepic").
- Run it in ChatGPT with search on, Perplexity, Gemini and Google AI Mode.
- Log per prompt: was the site cited (yes/no), where it appeared, and which sources were cited instead.
- Change the prompt set only once a quarter so months stay comparable.

## Report

- Client: five lines at most. What moved, what we did, what's next, anything we need from them.
- Internal: the full cycle file.

## Changelog

- 2026-10-14: v1.
