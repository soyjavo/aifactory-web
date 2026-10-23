# Brief — drafernandasolis.com
S0 Discovery · Run: [drafernandasolis.com: Redesign](https://app.notion.com/p/3fae2e0b1cc7811bbaf2c1154cee4e81) · Date: 2026-10-23 · Status: **draft — open items in §Open questions**

Sources: Notion Site/Run records; UMER KB-03 v2.1 (8 oct 2026); PH implementation page in Notion (phone per location); the doctor's own intake form "Dra Fernanda Solis - Formato para Medico.pdf" (Drive, Aug 2025); site repo `soyjavo/dra-fernada-solis-website` @ `51b5183` (2026-02-01); live site read 2026-10-23 (HTTP status + headers per URL, raw HTML, rendered DOM); Google Maps, both practitioner profiles (2026-10-23); Search Console domain property (2026-10-23); public DNS (2026-10-23); Doctoralia "Oftalmólogos en Tepic" list; Top Doctors pediatric ophthalmology list; `sites/umer/brief.md`; Francisco's answers (2026-10-23, after reading the draft). Facts marked **(confirm)** are unverified with the client.

## Business
- **Who:** Dra. María Fernanda Solís Rendón, Cirujana Oftalmóloga. Clinical and surgical ophthalmology, adults and children/adolescents (KB-03; her intake form). Co-owner of UMER with Dr. Rentería.
- **What she sells (client-decided, not ours):** her intake form lists clinical, surgical and preventive services. Surgical: catarata con LIO, refractiva (LASIK/PRK), glaucoma, **estrabismo en niños y adultos**, **pterigión**, plástica ocular (párpados, vías lagrimales), láser (retina, glaucoma). Preventive: tamiz visual infantil, revisiones. The live site has pages for only five of these. KB-04 v1.1 holds her 9 priced services for UMER — reconcile both lists in S1. She answered **"No"** to showing prices.
- **Market · language:** MX · es. English: open decision shared with UMER (see Gates).
- **Locations:**

| Location | Address | Phones (Francisco, 2026-10-23) | Hours |
|---|---|---|---|
| UMER Puerta de Hierro | Hospital Puerta de Hierro, Av. de la Salud 221, Piso 4, Consultorio 407, Ciudad Industrial, 63175 Tepic (GBP, site schema). HuliHealth lists the hospital as Av. Emilio M. González 221, same CP — **confirm the official street name.** | 311 980 1034 — exclusive to Dra. Solís · 311 170 2521 — consultorio 407's main line · 311 910 0090 — Puerta de Hierro human assistance | **Not published: they vary** (Francisco). The consultorio usually opens Mon/Wed/Thu 10–17, Tue 10–14, which matches the Tepic GBP. |
| UMER La Peñita | Gral. Lázaro Cárdenas 8-A, Centro, 63720 La Peñita de Jaltemba, Compostela (GBP, KB-02) | 322 308 0404 — clinic general line, books her · 322 158 2021 — La Peñita human assistance | Not published. Her La Peñita days per KB-03: Tue, Fri, Sat. |

- **Proposed public numbers (confirm):** one per location on the site and on its GBP. Tepic: **311 980 1034**, the line exclusive to her, which fits her own site and her practitioner profile (the Tepic GBP changes from 311 910 0090 in S6). If staff only reliably answer 311 170 2521, use that instead — but one number, everywhere. La Peñita: **322 308 0404**. Human-assistance lines stay inside the agent flows, off the site. Still needed: which of these numbers take WhatsApp.

- **Who approves:** the doctor **(confirm)**. Fany handles clinic logistics.
- **Existing AIFS work touching this site:** GHL chat widget (`694db15d…`) on every page; GHL booking calendar for Puerta de Hierro on `/agendar` (`links.intelvec.com`, calendar `xiBnmXD945J9uIdWcLhZ`); Leticia/Alicia (PH) and Sofía (La Peñita) WhatsApp agents. Delivery owns those; this site only wires to them.
- **Second purpose:** HQ wants this site as a showcase to sell websites to other specialists. That raises the craft bar and puts a requirement on the photo release; it doesn't add scope.

## Goals
- **Primary conversion:** WhatsApp conversation that becomes a booked appointment, routed by location (Tepic vs La Peñita). Today the hero offers "Agenda tu Cita" (GHL calendar, PH only) and "Llama Ahora" (`tel:3119801034`); WhatsApp is only a footer icon (`wa.me/523119801034`). La Peñita has a phone number only.
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
- **First candidate rejected by the doctor (2026-10-23):** *"La misma cirujana oftalmóloga para toda la familia, niños incluidos, en el Hospital Puerta de Hierro de Tepic y en La Peñita."* Too much logistics, too little meaning about caring for sight.
- **New candidates (sent to her for a pick):**
  1. *"Ver con claridad, en cada etapa de la vida: del tamiz visual del recién nacido a la cirugía de catarata."* **Recommended.** Keeps both real differentiators (children to older adults; clinical to surgical) inside a care framing, and it is exactly what the blur-to-focus moment shows.
  2. *"Detectar a tiempo para seguir viendo bien."* Prevention and follow-up: tamiz, routine checks, diabetes and hypertension (her form lists all three). Strong for parents and chronic patients; weaker for surgery.
  3. *"Que salgas de consulta entendiendo tus ojos: qué tienes, qué opciones hay y qué sigue."* Clarity of explanation. Only true if she owns it as how she practices.
- **Evidence for the life-stage angle:** people already search for it: about 50 impressions in 3 months on pediatric eye queries in Tepic, with no page to land on (GSC). None of the 20 ophthalmologists on Doctoralia's Tepic list mentions pediatric ophthalmology; Top Doctors' nearest pediatric ophthalmologists are in Guadalajara. She treats children and operates strabismus in children and adults (her form). The two locations are real and the competitors' are not on the coast.
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
| Hero, about, footer | "5000+ pacientes", "más de 15 años", "Presidenta, Sociedad de Oftalmólogos de Nayarit 2020–2022", "Certificada" | Not in her own intake form or KB-03. Her form says: UdeG; certificación vigente "colegio mexicano de oftalmólogos"; member of SMO and Sociedad de Oftalmólogos de Nayarit. **Presidenta is wrong: she's a member** (Francisco) | Unbacked claims. Board certification in Mexico is issued by the Consejo Mexicano de Oftalmología — get the certificate and quote its exact name. 5000+ and 15 años asked. |
| `/sobre-mi` timeline | 2005 Licenciatura (UdeG), 2009 Especialidad (Hospital Civil de Guadalajara), 2010 Certificación | Not in any record | Asked; remove whatever she doesn't confirm |
| `/privacidad` | Cédulas 4945849 / 6641452 | Footer and her form: 11984010 / 13206835 | Wrong cédula on a legal page (LGS Art. 83) |
| Phones | La Peñita shown as 327-690-2540 everywhere on the site | Not in any record | Fixed in the hotfix (322-308-0404) |
| Schema | `MedicalBusiness` with two addresses and one geo; `Physician` with no cédula, no `sameAs`; La Peñita address is a name, not a street | — | Rebuild as Person/Physician + two places (S1) |
| Content | Rendered H1 "Cuidamos tu Salud Visual" (banned filler); EN toggle is client-side only, not indexable; "Consulta General" has no page | — | — |
| `/privacidad` | "Última actualización: 25 de diciembre de 2024"; written by us (she answered N/A) | A new LFPDPPP was published in 2025 | Route to counsel |
| Chat widget | GHL widget on every page | If an AI answers, nothing on the site says so | AI disclosure |

**What works:** PH booking calendar (once the route resolves); GA4 installed; a real photo of her; cédulas in the footer; canonical on home; footer social links.

**Phone numbers:** resolved by Francisco (2026-10-23); roles in the Locations table under Business. 327 690 2540 belonged to nobody and is gone from the site.

**Search Console** (domain property, read 2026-10-23; data starts 2026-02-01):

| Window | Clicks | Impressions | CTR | Avg. position |
|---|---|---|---|---|
| Last 3 months (Jul 21 – Oct 20) | 77 | 2,493 | 3.1% | 7.2 |
| All data (Feb 1 – Oct 20) | 185 | 4,444 | 4.2% | 6.8 |

- **Pages:** `/` is the only URL with impressions, and the only page indexed (1 indexed; 1 excluded as "page with redirect"). No sitemap has ever been submitted, so Google hasn't even recorded the 404s. **No URL other than `/` carries search equity.** The old paths still get 301s in S1 (cheap; catches stray links and shares), but nothing ranks to protect.
- **Trend:** impressions rose (about 2,500 in the last 3 months vs about 1,950 in the 5.6 months before), clicks fell (77 vs 108). One page answering every query.
- **Top queries (3 months, 104 total):** "fernanda solis" 394 impressions, 0 clicks, pos 6.2 — the name is shared with other people (several queries are Instagram handles), so the site must say *Dra.* and *oftalmóloga* wherever her name appears. "oftalmologo tepic" 65 impr., pos 10.3, the only generic query with a click. **Pediatric queries total about 50 impressions** ("oftalmólogo pediatra", "oftalmologo pediatra en tepic", "oftalmopediatria", "oftalmólogo pediátrico"…) at positions 1–12 with no page to land on. Smaller: "puerta de hierro oftalmología" (6), "tamiz oftalmológico", "estrabismo", "umer la peñita" (2).

**GBP (2026-10-23):** two practitioner profiles, both named "Dra. Fernanda Solis Rendon - Cirujana Oftalmóloga", both linking to drafernandasolis.com, no reviews shown on either. Ownership and verification unknown.
- Tepic: Av. de la Salud 221, Piso 4, Consultorio 407, 63175; +52 311 910 0090 (Puerta de Hierro human assistance); Mon/Wed/Thu 10–17, Tue 10–14 (the consultorio's usual hours); 5 photos; "Located in" points to a Center for Innovation and Technology Transfer, not the hospital.
- La Peñita: Gral. Lázaro Cárdenas 8-A, 63720; +52 322 308 0404; Fri 17–21, Sat 10–20 (KB-03: also Tuesday, and Saturday until 21:00); 14 photos.
- The " - Cirujana Oftalmóloga" suffix: review against the no-keywords-in-names rule in S6.
- Social: Facebook `facebook.com/oftalmologiatepic` (confirmed by Francisco), Instagram `@drafernandasolis` (her form).

## Existing assets
| Asset | State | Gap |
|---|---|---|
| Portraits | One desk photo (`Desk_Dra_Fernanda_solid`) plus Lovable uploads; Francisco has more | Release unknown. These launch the site; a future session replaces them |
| Logo / brand kit | Only a small PNG used as favicon and og:image | No vector, no brand kit in Drive. Identity is designed in S2 (her own brand, not UMER's) |
| Premises | None of consultorio 407. La Peñita: existing clinic photos in UMER's Drive (`09 - Web umermedical.com / 01`) | No generated premises; real photos or none |
| Credentials | Cédulas from her form; no certificate copies | Certificate name, institution for the specialty, residency — from her |
| Content source | Her intake form (Aug 2025), KB-03, KB-04 | Bio is two lines; experience and training "pendiente" in KB-03 |
| Drive | [`Dra Fernanda Solis - Oftalmologa / Web drafernandasolis.com`](https://drive.google.com/drive/folders/1DFB-_ZuaX67EQ13MOtPnaPTo7m96pMNc), created 2026-10-23: `01 - Fotos reales existentes`, `02 - Generadas con IA`, `03 - Logo y marca`, `04 - Sesión de fotos (pendiente)` | Francisco drops her existing photos into 01 |

### Photo plan (Francisco, 2026-10-23)
- **No photo session soon.** The site launches on her existing real photos plus AI-generated imagery; a session later replaces what it can.
- **The line that doesn't move (`imagery.md`):** she, staff, patients and both premises are never generated — not from scratch and not "based on" her existing photos. Her real photos may be retouched (light, background, color, upscale), never her face, body or age.
- **What gets generated:** objects and places only — the eye, lenses, light, instruments, textures, the blur/focus frames, service illustrations (an intraocular lens, a slit lamp as an object). Nothing presented as her consultorio or as UMER. Every generated image is logged in `assets.md` with model, prompt and cost.
- **Release:** her existing photos still need a signed release before the site is shown to other clinics as AIFS work.

## Coordination with umermedical.com
Same Account, parallel run. These rules hold for both sites; the UMER brief should carry the same lines.

| Topic | Rule |
|---|---|
| Photo session | **Postponed** (Francisco, 2026-10-23): both sites launch on existing photos plus generated objects and places. When it happens: one session, one shot list for both sites (each site's S2 `assets.md` written together). Portraits (formal and environmental), working shots (slit lamp, no patient faces), consultorio 407 and C2, equipment details. UMER's brief books it for a Tuesday or Saturday morning in La Peñita; consultorio 407 needs its own slot in Tepic. Originals and releases go to UMER's Drive folder `09 - Web umermedical.com / 02 - Sesión de fotos doctores`, with a copy of her set in her own folder. |
| Page structure | UMER's brief builds a reusable skeleton (page types, content model, schema, integrations, compliance blocks) and names this site as its second shape, a solo practice. This run consumes it. Since `stack.md` keeps one repo per site, this run is the trigger to extract the skeleton into a starter: decide in both S1s. Skeleton shared, skin never. |
| Release | Signed by the doctor and anyone else in frame. Covers: use on both sites; AI retouch without changing identity; showing both sites to other clinics as AIFS work. Draft it; HQ/counsel reviews (not legal advice). Anyone in the patient chair signs too, faceless or not — use staff or a volunteer, never a real patient. Hospital Puerta de Hierro's permission to photograph on its premises and to name it **(confirm)**. |
| Copy | Her full bio, credentials and ophthalmology services live here. UMER gets a short profile (≤ 80 words) that links here. No shared paragraphs. |
| Search intent | **Changed by UMER's approved S1 (2026-10-23):** umermedical.com now has its own ophthalmology section for La Peñita (`/oftalmologia/`, tamiz visual, OCT, inyección) and targets "oftalmólogo en La Peñita" and pediatric/tamiz queries for Nayarit. Its Dra. Solís page defers her name to this site. So this site owns her name, her surgery, Tepic / Puerta de Hierro, and her full service list; for La Peñita-specific services it links to UMER's pages instead of duplicating them. Our S1 maps the split query by query so the two sites don't compete. |
| Entity | One Person/Physician entity with `@id` `https://drafernandasolis.com/#dra-solis`; UMER's profile references that `@id`. `sameAs`: both GBPs, Doctoralia, her Facebook and Instagram, UMER's profile URL. |
| NAP | One canonical row per location, used verbatim on both sites, both GBPs and Doctoralia. Values in §Open questions. |
| Design | Separate identities; shared component library, build setup and Cloudflare deploy pattern. Whatever UMER's run builds first, this run reuses. |

## Constraints and gates
**Gates — decisions this department doesn't own:**
1. **NAP (client):** phone roles answered; still open: which number is public per location (proposal above) and the official street name. Hours are not published. Blocks S1 schema and S3.
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
- **Hotfix shipped 2026-10-23** (site repo `e1fc349`): `public/_redirects` SPA fallback (every route now 200), testimonials and review schema removed, La Peñita phone set to 322-308-0404, privacy-page cédulas corrected. Side effect: unknown URLs now return 200 with the in-app 404 page (soft 404) until the redesign ships a real 404. Follow-up shipped the same night (`c5b0f61`): every emergency mention (FAQ, contact, cataract, terms) now says call 911 or go to Hospital Puerta de Hierro's 24 h ER; neither the consultorio nor UMER La Peñita handles emergencies (Francisco, 2026-10-23). A third copy patch shipped (`e0509e1`): hours removed everywhere (footer, contact, booking, schema), Presidenta → Miembro activo, and post-op patients told to reach her through their discharge instructions. Still live and unbacked: 5000+, 15+ años, the About timeline years.
- Her form says "yes" to a blog (eye care, check-ups, tamiz visual). Beyond the bounded page copy, that's content production: S8 quota or the future content department.

## SEO tier
- **T2 Local**, as on the Site record. Two locations, two GBPs, Doctoralia, one page per service tied to both locations. T3 isn't justified: no content operation.
- Training crawlers: recommend **Allowed**; decide in S1 and record on the Site.

## Approach
- **Experience level: Calm** — Site record, and the `motion.md` default for clinics.
- **Signature moment:** "ver con claridad", scroll from blur to focus, objects and places only. The cheapest compliant build is two versions of one frame (blurred and sharp) crossfaded with a CSS scroll-driven animation: opacity only, as `motion.md` requires, no JavaScript, and the sharp frame with the same line in text when motion is off. Animating `filter: blur()` directly breaks the transform/opacity rule and stutters on phones. A generated clip (≤ 2 MB, desktop-first) is possible but not needed.
- **Production budget:** about $30 of generation, through fal per call. With no session, generation now covers every non-portrait image: still cents each at the GPT Image / Nano Banana tier, so it fits. A Higgsfield month only makes sense if UMER's run uses it the same month.
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
- **Real assets for motion:** her existing photos only. The signature moment uses generated objects and places.
- **Sites the client points to:** the Webflow "Dental Health Clinic" template (`dental-health-clinic-template.webflow.io/homepage/home-b`). What she values in it: **simplicity**. The current site was already built from it, so in `direction.md` it counts as one reference for simplicity, alongside references from outside health (`taste.md`); the rest is our call: modern, with animations and transitions inside the Calm profile (Francisco).

## Open questions
| # | Question | Who answers | Blocks |
|---|---|---|---|
| 1 | Public number per location (proposal under Business), and which numbers take WhatsApp | Francisco | S1 |
| 2 | Official street name of the hospital (Av. de la Salud vs Av. Emilio M. González) | Client | S1 |
| 3 | Certificate (exact body and name, photo), specialty institution, pediatric subspecialty | Client (Francisco asks 2026-10-24) | S3 |
| 4 | Surgeries she performs herself and where (LASIK/PRK platform) | Client (Francisco asks 2026-10-24) | S1 |
| 5 | 5000+ pacientes, 15+ años, and the About timeline years: keep or remove | Client (Francisco asks 2026-10-24) | S3 |
| 6 | Pick the one-thing sentence from the three candidates | Client | S2 |
| 7 | Final service list (form vs KB-04 vs site) | Client | S1 |
| 8 | WhatsApp: which agent answers each number (AI disclosure) | Francisco (delivery) | S1 conversion paths |
| 9 | English: in or out (same answer as UMER) | Francisco (HQ) + client | S1 |
| 10 | Which Netlify account hosts the site, and which Cloudflare account holds the zone (same as UMER's)? | Francisco / client | S4 |
| 11 | Who manages both GBPs and the Doctoralia profile? | Francisco / client | S6 |
| 12 | Showcase: her consent to be a named reference; footer-credit brand (same HQ gate as UMER) | HQ | Showcase |
| 13 | Redesign terms and retainer | HQ | S4 |
