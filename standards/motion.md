# Motion standard

Version 1 · 2026-10-14 · Owner: Web & SEO

House rules. Durations and easing follow Emil Kowalski's skills.

## Order of tools

1. CSS transitions and keyframes.
2. View Transitions API. Same-document is supported in all major browsers; cross-document only as progressive enhancement (no Firefox yet).
3. CSS scroll-driven animations, as progressive enhancement behind `@supports` (no Firefox yet).
4. Motion (`motion` package, vanilla API) inside an island.
5. GSAP, only with a written reason in `direction.md`.

## Profiles

| | Calm (default for health and clinic sites) | Expressive (own brands, by choice) |
|---|---|---|
| Entrances | Fade plus ≤ 16 px move, once | Staggered; scroll-linked allowed |
| Signature moment | One per site: a still, a subtle loop, or one scroll-driven video of objects or places (`capabilities.md`) | One or more; chained clips allowed |
| Video per clip | ≤ 2 MB | ≤ 5 MB |
| Scroll-driven video on phones | Poster image instead | Simplified sequence or poster |
| Parallax | No | Light, one layer at most |
| 3D / WebGL | No | Only with a reason and a performance check |
| Motion JavaScript per page | ≤ 15 KB gzip | ≤ 40 KB gzip |

## Rules for both profiles

- `prefers-reduced-motion: reduce` means opacity-only or no motion. Test it before S7.
- Never animate or delay the LCP element.
- Animate only transform and opacity; never layout properties.
- No scroll-jacking.
- UI durations 100–300 ms. Ease-out by default, `cubic-bezier(0.23, 1, 0.32, 1)`; never ease-in on elements entering.
- Video: muted, `playsinline`, poster image, size per profile. People only in real footage (`imagery.md`).
- The signature moment still works with motion off: poster image plus the same message in text.
- Every animation must answer: what does it explain or reward? If nothing, cut it.

## Review

At S4 exit, run Emil's `review-animations` skill and the reduced-motion check. Record the result in `handoff.md`.

## Changelog

- 2026-10-14: v1.
- 2026-10-22: Calm sites may have one signature moment; video size budgets per profile; motion-off rule.
