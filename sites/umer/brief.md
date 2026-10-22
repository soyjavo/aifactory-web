# Brief — umermedical.com
S0 Discovery · Run: [umermedical.com: Redesign](https://app.notion.com/p/3fae2e0b1cc7819e9eb3c320130ec9a0) · Date: 2026-10-22 · Status: **draft — open items in §Open questions**

Sources: Notion Site/Run records; UMER Knowledge Base (KB-02 v1.0, KB-03 v2.1, KB-04 v1.1); site repo `soyjavo/umer-salud-nayarit-web` @ `bc68b24`; live site read 2026-10-22 (raw HTML + rendered DOM); Google Maps listings 2026-10-22; Doctoralia directory page for Rincón de Guayabitos. Facts marked **(confirm)** are unverified with the client.

## Business
- **Who:** Unidad Médica de Especialidades Rentería (UMER). Private multi-specialty outpatient unit, more than 20 years operating (KB-02).
- **Owners / lead clinicians:** Dr. Alfredo Rentería García — Ginecólogo Oncólogo y Obstetra. Dra. María Fernanda Solís Rendón — Cirujana Oftalmóloga (incl. pediatric). Both also consult at Hospital Puerta de Hierro, Tepic (consultorio 407). Other specialists rent consultorios C3–C6; roster unconfirmed since May 2026.
- **What they sell (client-decided, not ours):** KB-04 v1.1 is the source of truth for the two owners' services: 36 gynecology + 9 ophthalmology services with prices and prep. No catalog exists for the other specialties.
- **Market · language:** MX · es. A real English-speaking foreign-resident segment exists (see Audience) — language scope is an open decision.
- **Locations served:** La Peñita de Jaltemba, Compostela, Nayarit — Gral. Lázaro Cárdenas 8-A, Centro, 63720. The only active UMER location. Not Tepic. A future UMER Tepic branch is planned but not operating.
- **Hours:** Mon–Sat 8:00–21:00, Sun closed (KB-02; matches GBP). Each doctor works specific days.
- **Who approves on the client side:** Fany is the only admin contact since Flavio left (Sep 2026). Final sign-off presumably Dr. Rentería / Dra. Solís **(confirm)**.
- **Existing AIFS work on this account:** Sofía (GHL Conversation AI on WhatsApp), the doctor portal `umer-doctor-hub`, Supabase scheduling. Those belong to delivery; this site only wires to them.

## Goals
- **Primary conversion:** WhatsApp conversation that becomes a booked appointment. MX is WhatsApp-first; today the live home page has no WhatsApp link at all, only `tel:` links.
- **Secondary:** phone call; directions (GBP); English-language enquiry from foreign residents (if in scope).
- **How we'll know it worked:** WhatsApp click-throughs and calls per month from the site, GBP actions (calls, directions, website clicks), branded + "ginecólogo/oftalmólogo La Peñita" impressions and clicks in GSC.
- **Baseline:** none exists. No GA4, no Meta pixel, Search Console access not confirmed. Only Lovable's built-in analytics script is on the site. → Recommend installing GA4 + GSC on the current site now so the relaunch has a before.

## Audience
| Segment | What they're trying to do | What worries them |
|---|---|---|
| Local women, La Peñita–Guayabitos–Lo de Marcos–Las Varas corridor | Prenatal control, pap/colposcopy, ultrasound, IUD, a gynecologist without driving to Tepic or Vallarta | Cost, privacy, whether the specialist is actually there that day |
| Parents | Newborn eye screening (tamiz visual), pediatric eye exam, pediatrics | Whether the doctor sees children; what to bring; consent rules for minors |
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
| Clínica Rentería, Bahía de Acapulco Nte. 8 (GBP 4.0, 77 reviews, open 24 h) | 24 h, review volume, serves foreigners | Reviews complain about surprise charges. **Relationship to UMER unknown — must be clarified before we position against or with it.** |
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
| `/especialidades` | 17 specialties with Unsplash and generated images; Medicina Interna, Cirugía Bariátrica and Nutrición Clínica appear on no KB list; "Estética Vaginal" is claimed | Roster unconfirmed; KB tells Sofía *not* to affirm these | Unbacked claims; stock people as staff |
| Clinician info | No names, cédulas or photos per doctor | LGS Art. 83 requires cédula + institution on health promotion (`imagery.md`) | Compliance gap |
| Privacy notice | "Última actualización: Enero 2024" | A new LFPDPPP was published in 2025 | Route to counsel |

**Search Console (last 3 months):** not available — we couldn't confirm the property exists or reach it. **Open question.**

**GBP and directories (2026-10-22):**
- UMER profile: 5.0 ★, 11 reviews, hours match KB-02, phone +52 322 158 2021. Verification status unknown.
- Practitioner profiles exist for Dr. Rentería and Dra. Solís: 0 reviews, phone +52 322 308 0404 (a number not in KB-02), and hours that don't match KB-03 (Rentería Fri/Sat start 10:00 vs 8:40; Solís missing Tuesday, Sat ends 20:00 vs 21:00). NAP fix for S6.
- Doctoralia: no clinic profile. Two specialists list UMER as their practice: Dr. Jorge Vargas Naranjo (69 opinions) and Dr. Omar García Serrano, Traumatología (13). A UMER Google review names a dermatologist, Araceli — evidence some of the C3–C6 roster is active.

## Existing assets
| Asset | State | Gap |
|---|---|---|
| Logo | Raster PNG 1280×466 (blue + green wave, full name) from the current site | No vector found in Drive. Need SVG/AI. |
| Brand kit | None found | Palette can be derived from the logo in S2 |
| Photos of clinicians | One real photo of Dra. Solís + Dr. Rentería (background removed) in the hero | Release status unknown; no individual portraits |
| Photos of premises | None | Photo session needed (`imagery.md`) |
| Specialty images | Unsplash stock + generated | None usable as UMER-specific |
| Credentials | Cédulas, training, experience "pendiente" in KB-03 | Blocks clinician pages |
| Content source | Notion KB-02…KB-08, written for Sofía | Reuse as the site's fact source — one place to update |
| Drive | "UMER Clinica" shared drive (legal, meetings, operations, specialists, config) | No media or brand folder yet |
| Social | Facebook @umerenteria; Instagram unconfirmed | — |

## Constraints and gates
**Gates — decisions this department doesn't own (S1 can't map services until 1 and 2 close):**
1. **Specialty roster (client, via Fany):** which of the 16 listed specialties and specialists are active and may be published. One page per service requires real presence.
2. **UMER ↔ Clínica Rentería (client):** same owners? same building? shared urgencias? Decides naming, entity disambiguation, schema and whether "urgencias" appears anywhere.
3. **Tepic (client):** how to present Puerta de Hierro consultorio 407 (KB-03 v2.1 calls it "UMER Puerta de Hierro") and the future UMER Tepic. No Tepic location page until UMER really operates there.
4. **English for foreign patients (HQ + client):** whether the site targets them. If yes, a separate English section with its own content, not a translation. Nationality-based pricing ("Consulta extranjero") must not be published before counsel reviews it.
5. **Published prices (client):** KB-04 has them; whether the site shows them is the client's call.
6. **Commercial (HQ):** Site record shows no retainer. Redesign terms and the S8 retainer need to be settled before S4.

**Compliance (flag and route; not legal advice):**
- Cédula profesional + issuing institution on every clinician page (LGS Art. 83).
- COFEPRIS aviso de publicidad: confirm whether needed (`imagery.md`).
- Aviso de privacidad: review against the 2025 LFPDPPP; name the responsible party.
- Remove all fabricated cases, testimonials and stock "staff" (see table).
- AI disclosure: if the WhatsApp CTA reaches Sofía, the site says the first reply may come from an AI assistant.
- Minors: booking copy follows KB-08 (adult with ID; a human books every minor).

**Operational:**
- Stack: moves to the default (Astro → Cloudflare) in this run; no exception needed. The site needs its own Cloudflare account (client's, with us invited, or the agency program) — never the company account (`stack.md`). Domain registrar and DNS owner unknown.
- Dra. Solís has her own site (`dra-fernanda-solis` run). Her clinician page here and her own site must link to each other without competing for the same queries — settle in S1 for both.
- Content should read from the KB, so a change to hours or services is made once.

## SEO tier
- **T2 Local**, as on the Site record. A local clinic competing on GBP, service pages and directories. T3 isn't justified: no content operation, and content at volume belongs to another department.
- Training crawlers: undecided. Recommend **Allowed** (a local clinic gains nothing from blocking them) — decide at S1 and record on the Site.

## Open questions
| # | Question | Who answers | Blocks |
|---|---|---|---|
| 1 | Which specialties/specialists are active and publishable? | Client (Fany) | S1 |
| 2 | What is UMER's relationship to Clínica Rentería? | Client | S1 |
| 3 | Do we target English-speaking foreign residents? | Francisco (HQ) + client | S1 |
| 4 | Which WhatsApp number is the site CTA: human line 322 158 2021 or the WABA 311 296 0297 where Sofía runs? And what is 322 308 0404 on the practitioner profiles? | Francisco | S1 conversion paths |
| 5 | Is umermedical.com verified in Search Console, under which account? GBP owner/manager access? | Francisco | Baseline |
| 6 | Agree the one-thing sentence | Francisco + client | S2 |
| 7 | Show prices on the site? | Client | S3 |
| 8 | Who owns the domain and DNS; can the client open a Cloudflare account? | Francisco / client | S4 |
| 9 | Does a release exist for the Solís + Rentería hero photo? Logo vector? | Client | S2 |
| 10 | Redesign terms and retainer | HQ | S4 |
