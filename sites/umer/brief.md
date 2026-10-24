# Brief — umermedical.com
S0 Discovery · Run: [umermedical.com: Redesign](https://app.notion.com/p/3fae2e0b1cc7819e9eb3c320130ec9a0) · Date: 2026-10-22 · Updated 2026-10-23 (showcase goal, baseline, approach, reusable structure; doctors' answers) · Status: **draft — open items in §Open questions**

Sources: Notion Site/Run records; UMER Knowledge Base (KB-02 v1.0, KB-03 v2.1, KB-04 v1.1); site repo `soyjavo/umer-salud-nayarit-web` @ `bc68b24`; live site read 2026-10-22 (raw HTML + rendered DOM); Google Maps listings 2026-10-22; Doctoralia directory page for Rincón de Guayabitos; UMER Supabase project, aggregate counts only (2026-10-23); public DNS records for umermedical.com (2026-10-23). Facts marked **(confirm)** are unverified with the client.

## Business
- **Who:** Unidad Médica de Especialidades Rentería (UMER). Private multi-specialty outpatient unit, more than 20 years operating (KB-02).
- **Owners / lead clinicians:** Dr. Alfredo Rentería García — Ginecólogo Oncólogo y Obstetra. Dra. María Fernanda Solís Rendón — Cirujana Oftalmóloga (incl. pediatric). Both also consult at Hospital Puerta de Hierro, Tepic (consultorio 407). Other specialists rent consultorios C3–C6. **The site shows only the two owners for now** (doctors, 2026-10-23), matching what Sofía and Jessica can confirm.
- **What they sell (client-decided, not ours):** KB-04 v1.1 is the source of truth for the two owners' services: 36 gynecology + 9 ophthalmology services with prices and prep. **No prices on the site** (doctors, 2026-10-23): patients ask over WhatsApp.
- **Market · language:** MX · es, plus **one English page** for foreign residents (Francisco, 2026-10-23). It has its own content, not a translation, and no hreflang because no Spanish page is its alternate.
- **Contact numbers (Francisco, 2026-10-23):** the site's WhatsApp CTA goes to **322 308 0404**, the main number of the two AI assistants (Sofía and Jessica). The human assistants' line is not published; the AI assistants hand it out. Every chat from the site therefore starts with an AI, so the AI disclosure next to the CTA is mandatory.
- **Locations served:** La Peñita de Jaltemba, Compostela, Nayarit — Gral. Lázaro Cárdenas 8-A, Centro, 63720. The only active UMER location. Not Tepic. A future UMER Tepic branch is planned but not operating.
- **Hours:** Mon–Sat 8:00–21:00, Sun closed (KB-02; matches GBP). Each doctor works specific days.
- **Who approves on the client side:** the doctors directly, Dra. Solís and Dr. Rentería. Fany has left the team (Oct 2026), and there's no admin contact.
- **Existing AIFS work on this account:** Sofía (GHL Conversation AI on WhatsApp), the doctor portal `umer-doctor-hub`, Supabase scheduling. Those belong to delivery; this site only wires to them.

## Goals
- **Primary conversion:** WhatsApp conversation that becomes a booked appointment. MX is WhatsApp-first; today the live home page has no WhatsApp link at all, only `tel:` links.
- **Secondary:**
  - Phone call; directions (GBP); English-language enquiry from foreign residents (if in scope).
  - **Showcase for clinic sales** (Francisco, 2026-10-23). AIFS shows this site, and the numbers it produces, to other clinics. See below.
- **How we'll know it worked:** site-attributed WhatsApp conversations and calls per month, the bookings that came from them, GBP actions (calls, directions, website clicks), and GSC clicks and impressions on local queries ("ginecólogo/oftalmólogo La Peñita"). Everything measured the same way before and after launch.

### Showcase for clinic sales
Patients come first. Where the two goals conflict, the patient goal wins: nothing goes on the site only for the demo, and the site makes no claim AIFS can't back.

What the showcase needs that the site alone wouldn't:

| Need | Why | Owner |
|---|---|---|
| A before measured now, and the same measures after launch | The before/after is the sales story. It only holds if both sides are measured alike | This department (baseline below) |
| Site-attributed inquiries: a tagged WhatsApp link, GA4 events on WhatsApp and call clicks | Total bookings will likely rise in the winter-resident season (Nov–Apr) whatever the site does. Only attributed numbers show what the site did | This department (S6) |
| Booking channel recorded in the data | `appointments.source` is "receptionist" on every row and first visits aren't flagged, so no booking can be traced to the site today | **Delivery** (GHL ↔ Supabase sync) |
| A demo path that doesn't touch UMER's live patient line | Demoing site → WhatsApp → Sofía live puts fake conversations and bookings in the client's CRM | **Delivery** (a demo Sofía and number); this department points a staging copy of the site at it |
| Client consent to be a named reference and to share aggregate numbers | Their volume is their business data | **HQ** (client agreement) |
| Which AIFS brand gets the footer credit | Blocked by the open HQ gate: InteliMX or AIFactory Health sells to Mexican clinics | **HQ** |

The strongest demo is the whole chain: site → WhatsApp → Sofía → booking. Sofía stays with delivery; the site only wires to it, with AI disclosure.

### Baseline (captured 2026-10-23)
UMER La Peñita only: the Supabase project also holds Hospital Puerta de Hierro and a test clinic, both excluded. Aggregate counts only, no patient data. The scheduling system went live 2026-05-13, so May is partial and there's no year-over-year.

| Metric | Jun | Jul | Aug | Sep | Oct 1–22 | Source and caveat |
|---|---|---|---|---|---|---|
| Bookings created, all channels | 449 | 442 | 428 | 382 | 289 (~400 pace) | `appointments` by `created_at` |
| Distinct patients booked | 334 | 327 | 314 | 274 | 233 | Same |
| Appointments not cancelled and not no-show, by visit month | — | 451 | 352 | 314 | 245 | By `scheduled_start`, past visits only. Attendance marking is unreliable (past visits left "confirmed"), so read this as "not cancelled", not "attended" |
| New patient records | 340 | 304 | 285 | 212 | 177 | Inflated in early months: returning patients entered the new system for the first time. Not a clean new-patient count yet |

| Metric | Baseline | Note |
|---|---|---|
| Bookings by channel (WhatsApp AI, reception, phone, web) | **Not measurable** | `source` = "receptionist" on 100% of rows; `is_follow_up` is never true. Delivery fix, see the showcase table |
| WhatsApp conversations per month | **Pending: Francisco pulls from GHL** | Not in Supabase (`conversation_logs` is empty) and no GHL connector here. Needed: conversations started per month, Jul–Oct, on 322 308 0404 (main) and the human lines |
| Site-attributed WhatsApp and calls | **0 by construction** | The live site has no WhatsApp link and no analytics. Measurement starts the day a tagged link ships |
| Site traffic | **Not available** | No GA4. Lovable's own analytics exist but need the Lovable login, which the built-in browser doesn't have |
| Search Console | **One day of data (2026-10-22): 28 impressions, 0 clicks, average position 2.0.** Queries: "umer" (9 impressions, position 1.8), "umer la peñita" (4, 1.0), and one impression each for "consultorio médico cerca de mi", "cita con el ginecologo", "especialidades", "oftalmologo", "oncologo", "urologo". Only page: `https://www.umermedical.com/` | Read 2026-10-24. No history before 2026-10-22, even on the 16-month range: the property was new, so the before period starts there. Only the home page gets impressions, consistent with the client-side rendering. Google indexes the **www** host; www and apex both serve the site with no redirect or canonical (S1 fixes this). Domain property verified by Francisco through the `google-site-verification` TXT record in DNS; that record must stay |
| GBP | UMER 5.0 ★, 11 reviews. Practitioner profiles: 0 reviews | Google Maps, 2026-10-22. Insights (calls, directions, clicks) need manager access |

**Reading:** the totals are healthy, about 400 bookings a month. But the numbers a website moves (new inquiries, first visits, channel) are exactly the ones not recorded. Unless the measurement is fixed before launch, the case study rests on totals the season moves anyway.

## Audience
| Segment | What they're trying to do | What worries them |
|---|---|---|
| Local women, La Peñita–Guayabitos–Lo de Marcos–Las Varas corridor | Prenatal control, pap/colposcopy, ultrasound, IUD, a gynecologist without driving to Tepic or Vallarta | Cost, privacy, whether the specialist is actually there that day |
| Parents | Newborn eye screening (tamiz visual), pediatric eye exam | Whether the doctor sees children; what to bring; consent rules for minors |
| Adults and older adults | Eye exam, prescription, OCT, eye injections | Being sent elsewhere for equipment; needing a companion after dilation |
| Foreign residents and winter visitors (US/Canada) | A doctor who explains in English, clear price before the visit, insurance paperwork | Language; surprise charges — competitor reviews show this is the live fear in town |
| Patients who know the doctors from Tepic | Book with Dr. Rentería or Dra. Solís | Which location and which number; KB-02 documents this confusion |

Evidence for the foreign segment: KB-04 has a "Consulta extranjero" tier (gyn and ophthalmology); Fase 1.7 classifies foreign patients for Sofía; Google reviews of nearby clinics and opticians are full of Canadian and US winter residents. Winter season starts about now **(confirm with client how much of the patient base this is)**.

## The one thing
- **Candidate (needs Francisco + client sign-off):** *"The specialists who consult in Tepic's Hospital Puerta de Hierro see patients in La Peñita — the owners themselves, with the ultrasound included in the gynecology consult."*
- Why this one: it separates UMER from the IMSS UMF 16, from small general practices, and from Hospital Joya (a full hospital, not owner-specialists). It's true from KB-03/KB-04 and needs no claim we can't back.
- Per `taste.md`, S0 isn't done until this sentence is agreed.

## Competitors
| Site / listing | What they do well | Gap we can own |
|---|---|---|
| Hospital Joya La Peñita (Hospitales Joya network; directory listing, no own site found) | Full hospital: urgencias, imaging, lab; English spoken; tourist-facing | Not owner-specialists; no subspecialty depth in gyn-oncology or ophthalmic surgery |
| Clínica Rentería, Bahía de Acapulco Nte. 8 (GBP 4.0, 77 reviews, open 24 h) | 24 h, review volume, serves foreigners | **No relation to UMER** (doctors, 2026-10-23). Same surname in the name, a block away, open 24 h, with reviews about surprise charges: a real confusion risk. UMER's naming and NAP stay distinct everywhere; consider an FAQ line for patients who mix them up (S1/S3) |
| CIU Centro Integral de Ultrasonido, La Peñita (GBP 5.0, 7 reviews) | Dedicated ultrasound, report with photos/video | UMER's ultrasound is done by the gyn-oncologist and bundled in the consult |
| Dra. Sandra Llerena Legaspi (Doctoralia; Sayulita, Punta Mita, Nuevo Vallarta; 681 opinions) | Review volume, online booking, published prices, English | Regional, not local to La Peñita |
| Consultorio Vital, La Peñita (GBP 4.9, 9 reviews) | Known among expats as bilingual | General practice only |

Local search is thin: no competitor in town has a strong website. Visibility is decided on GBP, Doctoralia and Facebook, which is where T2 work pays.

## Current site
- **Stack · hosting · repo:** Lovable (Vite + React SPA, shadcn). Repo `soyjavo/umer-salud-nayarit-web` confirmed (Lovable project `d644f7ae…`). Hosted on Lovable's hosting (Cloudflare edge, `x-deployment-id`, Lovable analytics scripts). **The live build is older than the repo:** the 2026-06-01 commit that fixed "Tepic" → "La Peñita" in the meta tags was never published.
- **Rendering:** raw HTML is 2.2 KB with an empty `<div id="root">`. Non-JS crawlers and AI crawlers see the title and description only. Fails T1.
- **Technical:** no sitemap (404), no canonical, no structured data, unknown URLs return 200 (soft 404), the H1 is "Tu salud es nuestra prioridad / Excelencia médica comprobada" (banned filler), share image and `twitter:site` are Lovable's defaults, `gptengineer.js` in the page.
- **Live routes (for S1 redirects):** `/`, `/especialidades`, `/casos-de-exito`, `/agendar-cita`, `/preguntas-frecuentes`, `/contacto`, `/politica-de-privacidad`, `/terminos-y-condiciones`. Unrouted in code: `EquipoMedico`, `Reviews`.

**What's live and wrong** — this is the main finding:

| Where | Says | Reality (source) | Risk |
|---|---|---|---|
| Title, hero, about | "Tepic, Nayarit" | La Peñita de Jaltemba (KB-02, GBP) | Wrong local entity for search and patients |
| Hero, CTA | "más de 15 años", "22+ especialistas certificados" | 20+ years (KB-02); roster unconfirmed (KB-03) | Unbacked claims |
| Footer | "Urgencias 24/7" | Mon–Sat 8–21, Sun closed; urgencias go to a human first (KB-02/05) | Patient-safety claim |
| `/casos-de-exito` (in header + footer nav) | Clinical cases with invented doctors (Dra. Méndez, Dr. Jiménez, Dr. Soto, Dr. Ramírez, Dra. López, Dra. Morales) and invented patient testimony, incl. surgery UMER doesn't confirm | None of these doctors are on UMER's roster | Fabricated health advertising; banned by `imagery.md` and `taste.md` |
| Home testimonials | "María L.", "Carlos R.", "Ana M." | No source | Same |
| FAQ | Phone (311) 123-4567; hours L–V 9–19, Sáb 9–14; 24 h cancellation rule; "servicios básicos de laboratorio"; "principales aseguradoras" | Number is a placeholder; real hours above; no cancellation penalty today; lab and insurers unconfirmed (KB-03, KB-06) | Wrong information |
| `/agendar-cita` | Booking form shows "Solicitud enviada con éxito" | Submit only `console.log`s — every request is lost | Lost patients |
| `/especialidades` | 17 specialties with Unsplash and generated images; Medicina Interna, Cirugía Bariátrica and Nutrición Clínica appear on no KB list; "Estética Vaginal" is claimed | KB tells Sofía *not* to affirm these; the new site shows only the two owners | Unbacked claims; stock people as staff |
| Clinician info | No names, cédulas or photos per doctor | LGS Art. 83 requires cédula + institution on health promotion (`imagery.md`) | Compliance gap |
| Privacy notice | "Última actualización: Enero 2024" | A new LFPDPPP was published in 2025 | Route to counsel |

**Search Console (last 3 months):** see Baseline under Goals.

**GBP and directories (2026-10-22):**
- UMER profile: 5.0 ★, 11 reviews, hours match KB-02, phone +52 322 158 2021. Verification status unknown.
- Practitioner profiles exist for Dr. Rentería and Dra. Solís: 0 reviews, phone +52 322 308 0404 (a number not in KB-02), and hours that don't match KB-03 (Rentería Fri/Sat start 10:00 vs 8:40; Solís missing Tuesday, Sat ends 20:00 vs 21:00). NAP fix for S6.
- Doctoralia: no clinic profile. Two specialists list UMER as their practice: Dr. Jorge Vargas Naranjo (69 opinions) and Dr. Omar García Serrano, Traumatología (13). A UMER Google review names a dermatologist, Araceli — evidence some of the C3–C6 roster is active.

## Existing assets
| Asset | State | Gap |
|---|---|---|
| Logo | Raster PNG 1280×466 (blue + green wave, full name) from the current site | No vector found in Drive. Need SVG/AI. |
| Brand kit | None found | Palette can be derived from the logo in S2 |
| Photos of clinicians | The current hero photo is being replaced (doctors, 2026-10-23). The doctors have other real photos; Francisco shared one on 2026-10-23: both owners in white coats against a wood-slat wall, sharp and well lit | The session is deferred, so existing photos carry the site for now. On the shared photo: Dr. Rentería's coat carries the Hospitales Puerta de Hierro logo, a third-party brand on UMER's site. Retouch it out (`imagery.md` allows this; identity is untouched) or pick another photo. It's a pair shot, so clinician pages need crops or individual photos. Every photo needs a written OK from each doctor and the photographer's permission. Originals go to [`09 - Web umermedical.com / 02`](https://drive.google.com/drive/folders/1cof_YEEnis5HWGgZlkHipXvgtGyvBTZc) |
| Photos of premises | Francisco has existing clinic photos and is placing them in [`09 - Web umermedical.com / 01 - Fotos existentes de la clínica`](https://drive.google.com/drive/folders/1vvCqmtdiK1SUsfF6McuJ1M42bQWZs37C) | S2 inventories them in `assets.md` against `imagery.md`: usable as is, retouch only, or unusable. Anyone identifiable in frame needs a release (staff) or written consent (patients) |
| Specialty images | Unsplash stock + generated | All replaced. New ones are AI-generated objects and settings (Francisco, 2026-10-23), produced in S2 after the concept is picked. No people. Only equipment and services UMER really has (ultrasound, eye exam equipment, OCT); never X-ray, mammography, CT or MRI, which are on KB-03's list of what UMER doesn't have |
| Credentials | Cédulas, training, experience "pendiente" in KB-03 | Blocks clinician pages |
| Content source | Notion KB-02…KB-08, written for Sofía | Reuse as the site's fact source — one place to update |
| Drive | "UMER Clinica" shared drive (legal, meetings, operations, specialists, config) | Web folder created 2026-10-23: [`09 - Web umermedical.com`](https://drive.google.com/drive/folders/1i5p3DxiWdlz2b4Sj8rXbDRmXQcifm3Bl). No brand folder yet |
| Social | Facebook @umerenteria; Instagram unconfirmed | — |

## Constraints and gates
**Gates — decisions this department doesn't own (1, 2, 4 and 5 closed 2026-10-23; S1 can proceed):**
1. **Specialty roster — closed:** the site shows only Dra. Solís and Dr. Rentería and their services. Other specialists stay off until the doctors say otherwise.
2. **UMER ↔ Clínica Rentería — closed:** no relation. It becomes an entity-disambiguation task for S1 and S5: distinct naming and NAP, schema `sameAs` pointing only to UMER's own profiles, no "urgencias" claim.
3. **Tepic (client):** how to present Puerta de Hierro consultorio 407 (KB-03 v2.1 calls it "UMER Puerta de Hierro") and the future UMER Tepic. No Tepic location page until UMER really operates there.
4. **English for foreign patients — closed:** one English page with its own content (Francisco, 2026-10-23). No prices, so the nationality-based price question doesn't arise on the site.
5. **Published prices — closed:** no prices on the site. Service pages send price questions to WhatsApp. This also keeps the nationality-based "Consulta extranjero" price off the site.
6. **Commercial (HQ):** Site record shows no retainer. Redesign terms and the S8 retainer need to be settled before S4.
7. **Showcase (HQ):** client consent to be a named reference and to share aggregate numbers; which AIFS brand is credited (blocked by the open InteliMX / AIFactory Health gate). If the next clinic competes locally with UMER, HQ decides whether that conflicts with using UMER as the reference.

**Dependencies on delivery:** the GHL ↔ Supabase sync records each booking's channel and flags first visits; a demo Sofía and number for sales demos. Both needed before launch for the showcase to hold.

**Compliance (flag and route; not legal advice):**
- Cédula profesional + issuing institution on every clinician page (LGS Art. 83).
- COFEPRIS aviso de publicidad: confirm whether needed (`imagery.md`).
- Aviso de privacidad: review against the 2025 LFPDPPP; name the responsible party.
- Remove all fabricated cases, testimonials and stock "staff" (see table).
- AI disclosure: if the WhatsApp CTA reaches Sofía, the site says the first reply may come from an AI assistant.
- Minors: booking copy follows KB-08 (adult with ID; a human books every minor).

**Operational:**
- Stack: moves to the default (Astro → Cloudflare) in this run; no exception needed. The site needs its own Cloudflare account (client's, with us invited, or the agency program) — never the company account (`stack.md`).
- The domain is **registered** with Cloudflare Registrar (registered 2025-06-26, expires 2027-06-26) and its DNS runs there too. Both sit in another of Francisco's own Cloudflare accounts, so UMER doesn't own its domain today. Recommended: before launch, move the domain to a Cloudflare account UMER owns, with Francisco invited as administrator (or use the agency program). Registrar domains need Cloudflare's manual inter-account transfer, not the normal re-add. Do it about a week before launch with the site unchanged, so a DNS problem can't tangle with the new site. The A record points at Lovable. The domain's email runs on Google Workspace (MX + SPF): the cutover must not touch those records.
- Dra. Solís has her own site (`dra-fernanda-solis` run). Her clinician page here and her own site must link to each other without competing for the same queries — settle in S1 for both.
- Content should read from the KB, so a change to hours or services is made once.

## SEO tier
- **T2 Local**, as on the Site record. A local clinic competing on GBP, service pages and directories. T3 isn't justified: no content operation, and content at volume belongs to another department.
- Training crawlers: undecided. Recommend **Allowed** (a local clinic gains nothing from blocking them) — decide at S1 and record on the Site.

## Approach
Francisco, 2026-10-23.

- **Experience level: Calm, with one strong signature moment.** Already on the Site record. Calm is the house default for clinics, and in health calm signals competence (`taste.md`, principle 6).
  - Per `motion.md`, the one moment is a still, a subtle loop, or one scroll-driven video of objects or places.
  - It makes the one thing visible, and it still works with motion off: a poster image plus the same message in text.
  - No people in generated media. Real footage of the doctors needs a signed release.
- **Production budget:**

| Item | Budget | What it buys (`capabilities.md`) | Watch |
|---|---|---|---|
| AI generation | ~$70 | Stills and retouching cost cents each, so they barely touch it. A hero clip at 720p runs ~$0.75–1.50 per take with 4–5 takes per keeper: called per take through fal, one signature clip is roughly $3–8, which leaves room for retakes or a second variant | Higgsfield needs a paid monthly plan. Before picking it over per-call fal, check that its plan price fits inside $70 |
| Photo session | One real session for the doctors | Portraits of Dr. Rentería and Dra. Solís, together and at work (ultrasound, eye exam), plus the premises in the same light. Releases signed before anything is published | **Deferred** (doctors, 2026-10-23): may not happen soon, so existing photos carry the site meanwhile. When it happens: a Tuesday or Saturday morning, when both owners are in La Peñita (KB-03), and 10–20 s of real premises footage as a zero-cost signature-moment candidate |
| Hours | 10 | Allocation below | |

- **Hours** are read as Francisco's hands-on time, with agents doing the production work:

| Stage | Hours | Agents do | Francisco does |
|---|---|---|---|
| S1 Architecture, incl. the reusable page model | 1.5 | Sitemap, keyword map, schema plan, content model | Reviews and signs off |
| S2 Design | 2.5 | Direction draft, three concepts, storyboard, generation, comps | Picks the concept, judges assets, locks comps |
| S3 Copy | 1 | Copy drafted from the KB | Reviews, sends to the client |
| S4 Build | 2 | Astro build | Reviews on a phone, fixes |
| S5–S6 SEO and integrations | 1.5 | Schema, sitemap, GA4 events, tagged WhatsApp link | GSC, GBP fixes, GHL access |
| S7 Launch and QA | 1.5 | Checklist, redirects | DNS and Cloudflare cutover, handoff |
| **Total** | **10** | | |

  Not counted: client coordination over WhatsApp (the gates), the photo session day, and any hotfix on the current site. Tightest spots: S2, where three concepts plus comps fit in 2.5 h only if direction settles fast; and S7, if the DNS sits in the wrong Cloudflare account.

- **Real assets available for motion:**
  - Existing clinic photos (Francisco → Drive; inventoried in S2).
  - Existing photos of the doctors (one shared 2026-10-23; more to come).
  - AI-generated specialty images: objects and settings only.
  - The logo (raster only).
  - No footage exists today. The photo session is deferred.
- **Sites the client points to:** none; the doctors leave references to us (2026-10-23). S2 picks 3–4 per `taste.md`, at least one from outside health.

## Reusable page structure
Francisco, 2026-10-23: build the page structure so the next clinic can reuse it.

| Reused for the next clinic | Built fresh for each clinic |
|---|---|
| Page types and URL patterns: home, service, clinician, location, contact, legal | Direction, tokens, type, color |
| Content model fed from one data file per clinic, shaped like the KB: clinic, locations, hours, clinicians (with cédula and institution), services (prep, duration, optional price), FAQ | Copy and the one thing |
| Schema generated per page type (MedicalClinic, Physician + Person, BreadcrumbList) | The signature moment |
| Integrations: tagged WhatsApp CTA, GA4 events, GHL form and widget slots, GBP links | Photography |
| Compliance blocks: cédula display, aviso de privacidad, AI disclosure, minors note | Services, prices, specialties |
| Accessibility and performance budgets | |

- **Reuse the skeleton, never the skin.** `taste.md` principle 1 ("no section should fit a competitor's site unchanged") applies to every clinic, especially if the next one is in UMER's corridor.
- **Two shapes for S1.** S1 designs the model against two shapes so it doesn't bake in UMER's:
  - UMER: two owner-specialists in two specialties, with room to add the clinic's other specialists later.
  - A solo practice like drafernandasolis.com, already in the redesign program.
- **Where it lives:** inside UMER's repo, with clinic data kept apart from components. Extract a starter repo when a second clinic actually starts, not before, and add it to `stack.md` then.
- **Cost:** fits in the 10 h only at this level. A multi-clinic CMS, a site generator or a sales-demo mode is a separate project, not this run.

## Open questions
| # | Question | Who answers | Blocks |
|---|---|---|---|
| 1 | UMER's main Google profile lists 322 158 2021 (human line). Switch it to 322 308 0404 so name, address and phone match the site? | Francisco | S6 |
| 2 | GBP manager access? (Search Console done 2026-10-23; data pending) | Francisco | Baseline |
| 3 | WhatsApp conversations started per month, Jul–Oct, from GHL (both numbers) | Francisco | Baseline |
| 4 | Agree the one-thing sentence | Francisco + doctors | S2 |
| 5 | Existing doctor photos: written OK from each doctor and the photographer's permission. Puerta de Hierro logo on Dr. Rentería's coat: retouch out, or another photo? | Doctors | S2 |
| 6 | Logo in a vector file (AI, SVG or PDF) | Doctors | S2 |
| 7 | Domain and DNS are in another of Francisco's Cloudflare accounts. Move them to a Cloudflare account UMER owns (opened with a clinic email), with Francisco as administrator, about a week before launch? Also add a UMER Google account as owner in Search Console | Francisco + doctors | S7 |
| 8 | Booking channel and first-visit flag recorded by the sync; a demo Sofía and number | Delivery | Showcase, before launch |
| 9 | Showcase consent, footer-credit brand, local-competitor policy | HQ | Showcase |
| 10 | Redesign terms and retainer | HQ | S4 |

**Closed 2026-10-23** (the doctors, via Francisco): the site shows only the two owners; no relation to Clínica Rentería; references left to us; no prices on the site; photo session deferred, existing photos used meanwhile; the current hero photo is being replaced. Client contact is now the doctors directly; Fany has left.

**Closed 2026-10-23** (Francisco): Spanish site plus one English page; WhatsApp CTA to 322 308 0404, human line not published; hotfix of the current site approved; S1 starts now. Later the same day: 322 308 0404 takes calls too; training crawlers allowed; S1 approved. The one-thing sentence (question 4) is needed before S2, not S1.
