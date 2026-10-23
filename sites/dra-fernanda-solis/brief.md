# Brief — drafernandasolis.com
S0 Discovery · Run: [drafernandasolis.com: Redesign](https://app.notion.com/p/3fae2e0b1cc7811bbaf2c1154cee4e81) · Date: 2026-10-23 · Status: **draft — open items in §Open questions**

Sources: Notion Site/Run records; UMER KB-03 v2.1 (8 oct 2026); PH implementation page in Notion (phone per location); the doctor's own intake form "Dra Fernanda Solis - Formato para Medico.pdf" (Drive, Aug 2025); site repo `soyjavo/dra-fernada-solis-website` @ `51b5183` (2026-02-01); live site read 2026-10-23 (HTTP status + headers per URL, raw HTML, rendered DOM); Google Maps, both practitioner profiles (2026-10-23); Search Console domain property (2026-10-23); public DNS (2026-10-23); Doctoralia "Oftalmólogos en Tepic" list; Top Doctors pediatric ophthalmology list; `sites/umer/brief.md`. Facts marked **(confirm)** are unverified with the client.

## Business
- **Who:** Dra. María Fernanda Solís Rendón, Cirujana Oftalmóloga. Clinical and surgical ophthalmology, adults and children/adolescents (KB-03; her intake form). Co-owner of UMER with Dr. Rentería.
- **What she sells (client-decided, not ours):** her intake form lists clinical, surgical and preventive services. Surgical: catarata con LIO, refractiva (LASIK/PRK), glaucoma, **estrabismo en niños y adultos**, **pterigión**, plástica ocular (párpados, vías lagrimales), láser (retina, glaucoma). Preventive: tamiz visual infantil, revisiones. The live site has pages for only five of these. KB-04 v1.1 holds her 9 priced services for UMER — reconcile both lists in S1. She answered **"No"** to showing prices.
- **Market · language:** MX · es. English: open decision shared with UMER (see Gates).
- **Locations:**

| Location | Address | Phone of record | Hours |
|---|---|---|---|
| UMER Puerta de Hierro | Hospital Puerta de Hierro, Av. de la Salud 221, Piso 4, Consultorio 407, Ciudad Industrial, 63175 Tepic (GBP, site schema). HuliHealth lists the hospital as Av. Emilio M. González 221, same CP — **confirm the official street name.** | +52 311 980 1034 (KB-03, PH implementation, her form) | **Three versions — confirm.** Site: Mon/Wed 10:00–13:30 + 17:00–19:30, Thu 10:00–12:30. GBP: Mon/Wed/Thu 10–17, Tue 10–14. Her form (Aug 2025): Mon–Sat 8–21 (likely the hospital's hours). |
| UMER La Peñita | Gral. Lázaro Cárdenas 8-A, Centro, 63720 La Peñita de Jaltemba, Compostela (GBP, KB-02) | +52 322 308 0404 (GBP; PH implementation page, "LP number corrected 2026-10-06") **(confirm vs UMER's line 322 158 2021)** | Tue 10–14 + 16–18, Fri 17–21, Sat 10–14 + 16–21 (KB-03) |

- **Who approves:** the doctor **(confirm)**. Fany handles clinic logistics.
- **Existing AIFS work touching this site:** GHL chat widget (`694db15d…`) on every page; GHL booking calendar for Puerta de Hierro on `/agendar` (`links.intelvec.com`, calendar `xiBnmXD945J9uIdWcLhZ`); Leticia/Alicia (PH) and Sofía (La Peñita) WhatsApp agents. Delivery owns those; this site only wires to them.
- **Second purpose:** HQ wants this site as a showcase to sell websites to other specialists. That raises the craft bar and puts a requirement on the photo release; it doesn't add scope.

## Goals
- **Primary conversion:** WhatsApp conversation that becomes a booked appointment, routed by location (Tepic vs La Peñita). Today the hero offers "Agenda tu Cita" (GHL calendar, PH only) and "Llama Ahora" (`tel:3119801034`); WhatsApp is only a footer icon (`wa.me/523119801034`). No path to La Peñita except a phone number that isn't on record (below).
- **Secondary:** PH online booking (exists), call, directions from either GBP.
- **How we'll know it worked:** WhatsApp click-throughs, calls and bookings per location per month (GA4 events); GSC clicks and impressions for her name, "oftalmólogo Tepic", "cirugía de catarata Tepic", "oftalmólogo para niños Tepic", "oftalmólogo La Peñita"; GBP actions on both profiles.
- **Showcase measurement:** same rules as UMER's "Showcase for clinic sales" section, so the two case studies read alike: a tagged WhatsApp link per location, GA4 events on WhatsApp, call and booking clicks, measured the same way before and after launch. Patients first; nothing goes on the site only for the demo.
- **Baseline:** Search Console, last 3 months: 77 clicks, 2,493 impressions, all on `/` (detail under Current site). GA4 is installed (`G-XF18KGEHHY`), event setup unknown; no WhatsApp, call or booking events confirmed, so site-attributed inquiries start at zero by construction. GA4 traffic not pulled yet.

## Audience
| Segment | What they're trying to do | What worries them |
|---|---|---|
| Adults 55+ with cataract or glaucoma (Tepic and the rest of Nayarit) | Find out whether they need surgery, where it's done, cost, recovery | Surgery risk, who actually operates, travel to Tepic |
| Parents | Tamiz visual for a newborn, a child's eye exam, strabismus, first glasses | Whether she sees children, how a child's exam works, consent for minors |
| Adults wanting to drop glasses | LASIK/PRK candidacy, where it's done | Safety; whether she performs it herself and where **(confirm)** |
| Coast residents (La Peñita–Guayabitos–Compostela), incl. winter residents from US/Canada | An ophthalmologist without driving to Tepic or Vallarta | Which days she's there, which number, language |
| Patients and referring doctors who know her from the hospital | Book, find consultorio 407 | Which number for which location |

## The one thing
- **Candidate (needs Francisco + doctor sign-off):** *"La misma cirujana oftalmóloga para toda la familia, niños incluidos, en el Hospital Puerta de Hierro de Tepic y en La Peñita."*
- **Why this one:** people already search for it: about 50 impressions in 3 months on pediatric eye queries in Tepic, with no page to land on (GSC). None of the 20 ophthalmologists on Doctoralia's Tepic list mentions pediatric ophthalmology; Top Doctors' nearest pediatric ophthalmologists are in Guadalajara. She treats children and operates strabismus in children and adults (her form). The two locations are real and the competitors' are not on the coast.
- **Guardrail:** unless she holds a pediatric ophthalmology subspecialty certificate, copy says she *atiende niños* — never *oftalmóloga pediatra* **(confirm)**.
- **Signature moment:** "ver con claridad" (blur to focus) is the visual form of this promise, not the promise itself.
- Per `taste.md`, S0 isn't done until this sentence is agreed.

## Competitors
| Site / listing | What they do well | Gap we can own |
|---|---|---|
| Dr. Ricardo Rodríguez Ascencio — Doctoralia, 650 opinions; Centro Oftalmológico La Loma + Óptica Roma | Review volume; catarata, glaucoma, refractive laser; prices published ($900 first visit) | Adults only on his listing; Tepic only |
| Dr. Juan Carlos Miramontes González — Doctoralia, 554 opinions | Review volume; catarata, refractive laser | Same |
| Dr. Alejandro Carro Hernández — Doctoralia, 325 opinions; Paseo de la Loma 231 | Catarata, glaucoma surgery, laser; from $1,000 | Same |
| Dres. Ballesteros / Peña Martínez — Núcleo Diagnóstico Innovare | $900 first visit, online payment | Few reviews (15, 29) |
| Dr. Héctor Nuño Moya — Brasilia 22, oculoplastics | The oculoplastics niche | Competes with her plástica ocular page; keep her claims to what she does |

No competitor surfaced with a strong website. Visibility is decided on Doctoralia and GBP, where she has almost nothing: a bare Doctoralia profile (Hospital Puerta de Hierro, no consultorio, 0 opinions) and two GBPs with no reviews. That is where T2 work pays.

## Current site
- **Stack · hosting · repo:** Lovable-generated Vite + React SPA (shadcn, framer-motion), Lovable project `88729961…`. Repo `soyjavo/dra-fernada-solis-website` **confirmed**; last commit 2026-02-01, edited with Claude Code. **Hosted on Netlify** (`server: Netlify`, `x-nf-request-id`, Netlify Edge cache) — legacy hosting under `stack.md`. No Lovable Cloud or Supabase dependency. Netlify site `dra-fernanda-solis-website` (`www` CNAME), apex A record 75.2.60.5 (Netlify). Netlify account and plan unknown: if it's a Free account shared with other client sites, one overage pauses all of them.
- **DNS:** on Cloudflare, nameservers `keanu` / `rachel` — the same pair as umermedical.com, whose zone sits in an account under an email other than Francisco's (UMER brief), so very likely that same account. No MX records (her email is on outlook.com), so the cutover touches no mail. The TXT `google-site-verification` record verifies the Search Console domain property: it must survive the cutover.
- **Rendering:** `index.html` holds a static copy of the home content for crawlers (that's the "full content in HTML"); React replaces it on load. Only the home page has it.

**What's live and wrong** — two of these are urgent:

| Where | Says / does | Reality (source) | Risk |
|---|---|---|---|
| **Every URL except `/`** | Netlify "Page not found", HTTP 404: `/servicios` and its 5 service pages, `/sobre-mi`, `/contacto`, `/agendar`, `/preguntas-frecuentes`, `/privacidad`, `/terminos-y-condiciones` | No SPA fallback (`_redirects`) in the repo. In-app navigation works; direct visits, shared links, refreshes and Googlebot get 404. 10 of the 11 sitemap URLs 404. | GSC: only `/` is indexed. Nothing but the home page has ever ranked. |
| **Home testimonials + review schema** | Six named patients (María González, Carlos Ramírez…) and `aggregateRating` 5.0 / 6 reviews in JSON-LD | Her form lists no authorized testimonials; the earlier redesign's `REDESIGN_SUMMARY.md` only says they were carried over from the previous version. No source anywhere | Fabricated testimonials in health advertising; self-serving review markup (`seo.md`, Google policy) |
| Hero, about, footer | "5000+ pacientes", "más de 15 años", "Presidenta, Sociedad de Oftalmólogos de Nayarit 2020–2022", "Certificada" | Not in her own intake form or KB-03. Her form says: UdeG; certificación vigente "colegio mexicano de oftalmólogos"; member of SMO and Sociedad de Oftalmólogos de Nayarit | Unbacked claims. Board certification in Mexico is issued by the Consejo Mexicano de Oftalmología — get the certificate and quote its exact name. |
| `/privacidad` | Cédulas 4945849 / 6641452 | Footer and her form: 11984010 / 13206835 | Wrong cédula on a legal page (LGS Art. 83) |
| Phones (below) | La Peñita shown as 327-690-2540 everywhere on the site | Not in any record | Patients call a number nobody tracks |
| Schema | `MedicalBusiness` with two addresses and one geo; `Physician` with no cédula, no `sameAs`; La Peñita address is a name, not a street | — | Rebuild as Person/Physician + two places (S1) |
| Content | Rendered H1 "Cuidamos tu Salud Visual" (banned filler); EN toggle is client-side only, not indexable; "Consulta General" has no page | — | — |
| `/privacidad` | "Última actualización: 25 de diciembre de 2024"; written by us (she answered N/A) | A new LFPDPPP was published in 2025 | Route to counsel |
| Chat widget | GHL widget on every page | If an AI answers, nothing on the site says so | AI disclosure |

**What works:** PH booking calendar (once the route resolves); GA4 installed; a real photo of her; cédulas in the footer; canonical on home; footer social links.

**Phone numbers in play** (resolve to one per location before S1):

| Number | Appears in | Status |
|---|---|---|
| 311 980 1034 | Site (Tepic), footer WhatsApp link, KB-03, PH implementation, her form | Tepic line — consistent |
| 311 170 2521 | Her form (Aug 2025), an unused hero component | Unknown |
| 311 910 0090 | Tepic GBP | Not in any record |
| 327 690 2540 | Site (La Peñita): footer, contact, booking, schema, privacy | Not in any record |
| 322 308 0404 | La Peñita GBP; PH implementation page | Likely La Peñita's line **(confirm)** |
| 322 158 2021 | UMER human line (KB-03) | UMER's clinic line |

**Search Console** (domain property, read 2026-10-23; data starts 2026-02-01):

| Window | Clicks | Impressions | CTR | Avg. position |
|---|---|---|---|---|
| Last 3 months (Jul 21 – Oct 20) | 77 | 2,493 | 3.1% | 7.2 |
| All data (Feb 1 – Oct 20) | 185 | 4,444 | 4.2% | 6.8 |

- **Pages:** `/` is the only URL with impressions, and the only page indexed (1 indexed; 1 excluded as "page with redirect"). No sitemap has ever been submitted, so Google hasn't even recorded the 404s. **No URL other than `/` carries search equity.** The old paths still get 301s in S1 (cheap; catches stray links and shares), but nothing ranks to protect.
- **Trend:** impressions rose (about 2,500 in the last 3 months vs about 1,950 in the 5.6 months before), clicks fell (77 vs 108). One page answering every query.
- **Top queries (3 months, 104 total):** "fernanda solis" 394 impressions, 0 clicks, pos 6.2 — the name is shared with other people (several queries are Instagram handles), so the site must say *Dra.* and *oftalmóloga* wherever her name appears. "oftalmologo tepic" 65 impr., pos 10.3, the only generic query with a click. **Pediatric queries total about 50 impressions** ("oftalmólogo pediatra", "oftalmologo pediatra en tepic", "oftalmopediatria", "oftalmólogo pediátrico"…) at positions 1–12 with no page to land on. Smaller: "puerta de hierro oftalmología" (6), "tamiz oftalmológico", "estrabismo", "umer la peñita" (2).

**GBP (2026-10-23):** two practitioner profiles, both named "Dra. Fernanda Solis Rendon - Cirujana Oftalmóloga", both linking to drafernandasolis.com, no reviews shown on either. Ownership and verification unknown.
- Tepic: Av. de la Salud 221, Piso 4, Consultorio 407, 63175; +52 311 910 0090; Mon/Wed/Thu 10–17, Tue 10–14 (Tuesday clashes with her La Peñita schedule); 5 photos; "Located in" points to a Center for Innovation and Technology Transfer, not the hospital.
- La Peñita: Gral. Lázaro Cárdenas 8-A, 63720; +52 322 308 0404; Fri 17–21, Sat 10–20 (KB-03: also Tuesday, and Saturday until 21:00); 14 photos.
- The " - Cirujana Oftalmóloga" suffix: review against the no-keywords-in-names rule in S6.
- Social: footer links `facebook.com/oftalmologiatepic`; her form gives Facebook "drafernandasolis" and Instagram `@drafernandasolis` — **confirm which Facebook page is hers.**

## Existing assets
| Asset | State | Gap |
|---|---|---|
| Portraits | One desk photo (`Desk_Dra_Fernanda_solid`) plus Lovable uploads | Release unknown; replaced by the shared session |
| Logo / brand kit | Only a small PNG used as favicon and og:image | No vector, no brand kit in Drive. Identity is designed in S2 (her own brand, not UMER's) |
| Premises | None | Shared session |
| Credentials | Cédulas from her form; no certificate copies | Certificate name, institution for the specialty, residency — from her |
| Content source | Her intake form (Aug 2025), KB-03, KB-04 | Bio is two lines; experience and training "pendiente" in KB-03 |
| Drive | Folder "Dra Fernanda Solis - Oftalmologa" (form + empty UMER ficha); Account record has no Drive link | Create a media/brand folder before the session |

## Coordination with umermedical.com
Same Account, parallel run. These rules hold for both sites; the UMER brief should carry the same lines.

| Topic | Rule |
|---|---|
| Photo session | One session, one shot list for both sites (each site's S2 `assets.md` written together). Portraits (formal and environmental), working shots (slit lamp, no patient faces), consultorio 407 and C2, equipment details. UMER's brief books it for a Tuesday or Saturday morning in La Peñita; consultorio 407 needs its own slot in Tepic. Originals and releases go to UMER's Drive folder `09 - Web umermedical.com / 02 - Sesión de fotos doctores`, with a copy of her set in her own folder. |
| Page structure | UMER's brief builds a reusable skeleton (page types, content model, schema, integrations, compliance blocks) and names this site as its second shape, a solo practice. This run consumes it. Since `stack.md` keeps one repo per site, this run is the trigger to extract the skeleton into a starter: decide in both S1s. Skeleton shared, skin never. |
| Release | Signed by the doctor and anyone else in frame. Covers: use on both sites; AI retouch without changing identity; showing both sites to other clinics as AIFS work. Draft it; HQ/counsel reviews (not legal advice). Anyone in the patient chair signs too, faceless or not — use staff or a volunteer, never a real patient. Hospital Puerta de Hierro's permission to photograph on its premises and to name it **(confirm)**. |
| Copy | Her full bio, credentials and ophthalmology services live here. UMER gets a short profile (≤ 80 words) that links here. No shared paragraphs. |
| Search intent | This site owns her name and ophthalmology queries. umermedical.com owns UMER and its other specialties; any ophthalmology mention there links here rather than duplicating service pages. Settle in both S1s together. |
| Entity | One Person/Physician entity with `@id` `https://drafernandasolis.com/#dra-solis`; UMER's profile references that `@id`. `sameAs`: both GBPs, Doctoralia, her Facebook and Instagram, UMER's profile URL. |
| NAP | One canonical row per location, used verbatim on both sites, both GBPs and Doctoralia. Values in §Open questions. |
| Design | Separate identities; shared component library, build setup and Cloudflare deploy pattern. Whatever UMER's run builds first, this run reuses. |

## Constraints and gates
**Gates — decisions this department doesn't own:**
1. **NAP (client):** phone per location, Tepic hours, official street name. Blocks S1 schema and S3.
2. **Credentials (client):** certificate name and body, specialty institution, which surgeries she performs and where (LASIK/PRK platform), pediatric subspecialty or not. Blocks S3 claims and the Physician schema.
3. **Service list (client):** reconcile her form, KB-04 and the current five pages. Blocks S1.
4. **English (HQ + client):** same decision as UMER. Default: Spanish only; the current client-side toggle goes.
5. **WhatsApp routing (Francisco + delivery):** which number per location, and whether Leticia (PH) or Sofía (La Peñita) answers first. Drives CTAs and AI disclosure.
6. **Commercial (HQ):** Site record shows no retainer. Redesign terms and the S8 retainer before S4.

**Compliance (flag and route; not legal advice):**
- Cédula profesional, cédula de especialidad and institution on every page that promotes her (LGS Art. 83); fix the wrong numbers on `/privacidad`.
- Remove the fabricated testimonials and the review markup now.
- COFEPRIS aviso de publicidad: confirm whether needed (`imagery.md`).
- Aviso de privacidad: rewrite against the 2025 LFPDPPP; GHL as processor.
- AI disclosure wherever a CTA or the chat widget reaches an AI agent.
- Minors: booking copy follows KB-08 (a guardian books; a human handles every minor).

**Operational:**
- Stack moves to the default in this run: Astro → Cloudflare, on the client's own Cloudflare account or the agency program, never the company account. Off Netlify. The DNS zone sits in the same Cloudflare account as umermedical.com's: identify it once for both; if it's the company account, both zones move together. Registrar unknown.
- **Hotfix shipped 2026-10-23** (site repo `e1fc349`): `public/_redirects` SPA fallback (every route now 200), testimonials and review schema removed, La Peñita phone set to 322-308-0404, privacy-page cédulas corrected. Side effect: unknown URLs now return 200 with the in-app 404 page (soft 404) until the redesign ships a real 404. Follow-up shipped the same night (`c5b0f61`): every emergency mention (FAQ, contact, cataract, terms) now says call 911 or go to Hospital Puerta de Hierro's 24 h ER; neither the consultorio nor UMER La Peñita handles emergencies (Francisco, 2026-10-23). Still live and unbacked: the hero/about claims (5000+, 15+ años, Presidenta).
- Her form says "yes" to a blog (eye care, check-ups, tamiz visual). Beyond the bounded page copy, that's content production: S8 quota or the future content department.

## SEO tier
- **T2 Local**, as on the Site record. Two locations, two GBPs, Doctoralia, one page per service tied to both locations. T3 isn't justified: no content operation.
- Training crawlers: recommend **Allowed**; decide in S1 and record on the Site.

## Approach
- **Experience level: Calm** — Site record, and the `motion.md` default for clinics.
- **Signature moment:** "ver con claridad", scroll from blur to focus, objects and places only. The cheapest compliant build is two versions of one frame (blurred and sharp) crossfaded with a CSS scroll-driven animation: opacity only, as `motion.md` requires, no JavaScript, and the sharp frame with the same line in text when motion is off. Animating `filter: blur()` directly breaks the transform/opacity rule and stutters on phones. A generated clip (≤ 2 MB, desktop-first) is possible but not needed.
- **Production budget:** about $30 of generation, through fal per call. A Higgsfield month only makes sense if UMER's run uses it the same month. Plus the shared photo session.
- **Hours: about 8**, read as in UMER's brief: Francisco's hands-on time, agents doing the production. Realistic only because UMER's run builds the skeleton, deploy pattern and session logistics first.

| Stage | Hours | Agents do | Francisco does |
|---|---|---|---|
| S1 Architecture | 1 | Sitemap on the shared skeleton, keyword map, schema, redirects | Signs off |
| S2 Design | 2.5 | Direction, three concepts, storyboard, the blur/focus frames, comps | Picks the concept, locks comps |
| S3 Copy | 1.5 | Copy from her form and KB, service pages | Reviews, sends to her |
| S4 Build | 1.5 | Astro build on the skeleton | Phone review, fixes |
| S5–S7 | 1.5 | Schema, GA4 events, tagged links, checklist | GSC, both GBPs, Doctoralia, cutover |
| **Total** | **8** | | |

  Not counted: client coordination over WhatsApp, the session day, the hotfix. If UMER's S1–S2 slip, this run waits rather than building the skeleton twice.
- **Real assets for motion:** the shared session. Real premises get ambient motion only.
- **Sites the client points to:** none recorded. The earlier redesign (`REDESIGN_SUMMARY.md`) copied a Webflow dental template; that is not a reference for this run (`taste.md`).

## Open questions
| # | Question | Who answers | Blocks |
|---|---|---|---|
| 1 | One phone per location (table above); what are 311 910 0090, 311 170 2521 and 327 690 2540? | Francisco + client | S1 |
| 2 | Her Tepic consulting hours; official street name of the hospital | Client | S1 |
| 3 | Certificate (exact body and name), specialty institution, surgeries she performs and where, pediatric subspecialty | Client | S3 |
| 4 | Final service list (form vs KB-04 vs site) | Client | S1 |
| 5 | Agree the one-thing sentence | Francisco + client | S2 |
| 6 | WhatsApp number per location and which agent answers | Francisco (delivery) | S1 conversion paths |
| 7 | English: in or out (same answer as UMER) | Francisco (HQ) + client | S1 |
| 8 | Which Netlify account hosts the site, and which Cloudflare account holds the zone (same as UMER's)? Can she or UMER open their own? | Francisco / client | S4 |
| 9 | Who manages both GBPs and the Doctoralia profile? | Francisco / client | S6 |
| 10 | Which Facebook page is hers (`oftalmologiatepic` vs `drafernandasolis`)? | Client | S1 `sameAs` |
| 11 | Which sites does she like, and why? | Client | S2 |
| 12 | Showcase: her consent to be a named reference; which AIFS brand gets the footer credit (same HQ gate as UMER) | HQ | Showcase |
| 13 | Redesign terms and retainer | HQ | S4 |
