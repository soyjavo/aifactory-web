# Architecture — umermedical.com
S1 Architecture · reads `brief.md` (2026-10-23), `standards/seo.md` (T1 + T2), `standards/stack.md` · Date: 2026-10-23 · Status: **approved by Francisco 2026-10-23**; doctor inputs 4–7 still open (they feed S3 and S7, not S2)

**Decisions this rests on (from the brief):**
- **Scope:** only Dr. Alfredo Rentería and Dra. Fernanda Solís and their services (KB-04); no prices.
- **Languages:** Spanish site plus one English page.
- **CTA:** WhatsApp to 322 308 0404, where the AI assistants answer.
- **Disambiguation:** no relation to Clínica Rentería.
- **Tier and approach:** T2 Local; Calm; page structure reusable for the next clinic.

## Sitemap
18 URLs, 17 indexable. Nine templates (see §Reusable data model).

| URL | Page | Template | Purpose | Intent | Primary query (es) | Schema |
|---|---|---|---|---|---|---|
| `/` | Inicio | Home | First phone screen: who, what, where, next step. Routes to both specialties and both doctors | Local, navigational | "UMER La Peñita", "especialistas La Peñita" | MedicalClinic, WebSite, WebPage |
| `/ginecologia/` | Ginecología y obstetricia | SpecialtyHub | The consult (ultrasound of uterus and ovaries included), endovaginal ultrasound, adolescents 12–17, links to the five service pages and to Dr. Alfredo | Local, transactional | "ginecólogo en La Peñita" | MedicalWebPage (about Gynecologic, Obstetric), BreadcrumbList |
| `/ginecologia/control-de-embarazo/` | Control de embarazo y ultrasonido | Service | Prenatal control, obstetric and structural ultrasound by trimester (11–14, 20–24, 28–32 weeks), twin pregnancy | Transactional | "control de embarazo La Peñita", "ultrasonido de embarazo" | MedicalWebPage + MedicalProcedure |
| `/ginecologia/papanicolaou-colposcopia-vph/` | Papanicolaou, colposcopía y VPH | Service | Detection (pap, colposcopy, HPV test) and treatment of lesions (cauterization, laser, cervical biopsy). Prep from KB-04 | Transactional | "papanicolaou La Peñita" | MedicalWebPage + MedicalTest |
| `/ginecologia/anticonceptivos/` | DIU e implante anticonceptivo | Service | Four IUD types, subdermal implant, removals; deposit and 3-day lead time | Transactional | "DIU La Peñita" | MedicalWebPage + MedicalProcedure |
| `/ginecologia/salud-mamaria/` | Ultrasonido de mama | Service | Breast ultrasound and breast biopsy. States plainly that UMER has no mammography | Transactional | "ultrasonido de mama La Peñita" | MedicalWebPage + MedicalTest |
| `/ginecologia/oncologica/` | Ginecología oncológica | Service | Dr. Alfredo's subspecialty: assessment of suspicious lesions, endometrial and vulvar biopsy | Specialist search | "ginecólogo oncólogo Nayarit" | MedicalWebPage (about Oncologic) |
| `/oftalmologia/` | Oftalmología | SpecialtyHub | Eye exam and prescription, adults and children, chalazion; links to three service pages and to Dra. Fernanda | Local, transactional | "oftalmólogo en La Peñita", "oculista La Peñita" | MedicalWebPage (about Ophthalmology), BreadcrumbList |
| `/oftalmologia/tamiz-visual-recien-nacido/` | Tamiz visual del recién nacido | Service | From 28 days old; arrive 30 min early to dilate; book ahead (the doctor brings equipment from Tepic) | Transactional (parents) | "tamiz visual recién nacido Nayarit" | MedicalWebPage + MedicalTest |
| `/oftalmologia/oct/` | Estudio OCT de mácula y nervio óptico | Service | Three OCT variants; arrive 30 min early; come with an adult (blurred vision after) | Transactional | "estudio OCT ojo", "tomografía de coherencia óptica" | MedicalWebPage + MedicalTest |
| `/oftalmologia/inyeccion-oftalmologica/` | Inyección oftalmológica | Service | Done in the operating room; companion required; no makeup. **What it treats: confirm with Dra. Solís before S3** | Transactional | "inyección en el ojo" (confirm) | MedicalWebPage + MedicalProcedure |
| `/doctores/alfredo-renteria/` | Dr. Alfredo Rentería | Clinician | Real photo, title, cédulas and institution, days at UMER, services, consult length | Name and trust | "Dr. Alfredo Rentería ginecólogo" | ProfilePage, Person, IndividualPhysician |
| `/doctores/fernanda-solis/` | Dra. Fernanda Solís | Clinician | Same, linking to drafernandasolis.com as her main site | Trust | "oftalmóloga La Peñita" (her name belongs to her own site) | ProfilePage, Person, IndividualPhysician |
| `/contacto/` | Contacto y cómo llegar | Contact | Address, Google Maps link to the GBP, hours, WhatsApp, how booking works with the AI disclosure, accessibility, no parking, minors | Navigational | "UMER La Peñita dirección" | WebPage + clinic reference, BreadcrumbList |
| `/preguntas-frecuentes/` | Preguntas frecuentes | FAQ | KB-verified answers, including what UMER doesn't offer and that it isn't Clínica Rentería | Long tail | Many | WebPage, BreadcrumbList |
| `/en/` | English page | LanguageLanding | For winter residents: the two doctors, booking on WhatsApp in English, what to expect, directions. Doesn't promise English-speaking doctors (level unconfirmed in KB-03) | Local (en) | "gynecologist La Peñita", "eye doctor La Peñita" | WebPage (inLanguage en) + clinic reference |
| `/aviso-de-privacidad/` | Aviso de privacidad | Legal | LFPDPPP notice; counsel reviews against the 2025 law | — | — | WebPage |
| `/404` | Página no encontrada | NotFound | Spanish; links to both hubs and WhatsApp; real 404 status | — | — | none, noindex |

**Navigation.**
- Header: Ginecología · Oftalmología · Doctores (both) · Contacto · English · [Agendar por WhatsApp].
- Footer: name, address and phone; hours; aviso de privacidad; the AI-assistant disclosure.
- Each service page links to its hub and its doctor. Each doctor page lists its services. Home links both hubs and both doctors. No orphans.

## Keyword and intent map
No keyword tool was used, and local volumes are small. Competition notes come from web results and Maps on 2026-10-23. Refine with Search Console queries once tomorrow's pull lands, and again 4–6 weeks after the hotfix.

| Query (es unless noted) | Intent | Competition note | Target URL |
|---|---|---|---|
| ginecólogo en La Peñita · ginecólogo Guayabitos · ginecóloga La Peñita | Find and book | Web results show directories only (Doctoralia, Topdoctors); the Maps pack decides, so GBP and this page work together | `/ginecologia/` |
| control de embarazo La Peñita · control prenatal · ultrasonido de embarazo · ultrasonido estructural | Book | CIU Centro Integral de Ultrasonido (GBP 5.0) competes on scans; our edge is the specialist doing it inside the consult | `/ginecologia/control-de-embarazo/` |
| papanicolaou La Peñita (also "papanicolau") · colposcopía Nayarit · prueba VPH | Book | Directories only | `/ginecologia/papanicolaou-colposcopia-vph/` |
| DIU La Peñita · poner DIU Mirena · implante anticonceptivo | Book | Directories only | `/ginecologia/anticonceptivos/` |
| ultrasonido de mama La Peñita · mastografía La Peñita | Book | Mastografía isn't offered: the page says so and offers what is | `/ginecologia/salud-mamaria/` |
| ginecólogo oncólogo Nayarit · ginecología oncológica Tepic | Specialist search | Tepic results are hospitals; win the coastal variant | `/ginecologia/oncologica/` |
| oftalmólogo en La Peñita · oculista La Peñita · doctor de los ojos Guayabitos | Find and book | No local ophthalmologist site found; opticians (Opti-Duran, Óptica Rashel) compete on "examen de la vista" | `/oftalmologia/` |
| examen de la vista La Peñita · graduación de lentes | Mixed (optician vs doctor) | Show it's a medical exam by an ophthalmologist | `/oftalmologia/` |
| oftalmólogo pediatra Nayarit · revisión de la vista niños | Parents | Few providers | `/oftalmologia/` (section) |
| tamiz visual recién nacido Nayarit · tamiz visual La Peñita | Parents, book | Few providers; content is mostly academic | `/oftalmologia/tamiz-visual-recien-nacido/` |
| estudio OCT · tomografía de coherencia óptica Nayarit | Book | Hospital and lab listings | `/oftalmologia/oct/` |
| inyección en el ojo · inyección intravítrea Nayarit (confirm the term) | Book | — | `/oftalmologia/inyeccion-oftalmologica/` |
| UMER La Peñita · Unidad Médica de Especialidades Rentería | Brand | Confusion with Clínica Rentería, a block away | `/`, `/contacto/` |
| Dra. Fernanda Solís oftalmóloga | Name | Her own site should rank first; UMER's page second | drafernandasolis.com, then `/doctores/fernanda-solis/` |
| Dr. Alfredo Rentería ginecólogo | Name | GBP practitioner profile, 0 reviews | `/doctores/alfredo-renteria/` |
| (en) gynecologist La Peñita · eye doctor La Peñita · English speaking doctor Guayabitos | Find and book | Expat clinics (Consultorio Vital) win on English | `/en/` |

## Content model
### Services × locations × audiences
- **One location.** No city or area pages (`seo.md`). Neighboring towns (Rincón de Guayabitos, Los Ayala, Lo de Marcos, Las Varas) appear only in the how-to-get-here text and as the GBP service area.
- **Services mapped from KB-04 v1.1.** No prices anywhere.

| Page | KB-04 services on it | Not shown |
|---|---|---|
| `/ginecologia/` | Consulta general (with uterus and ovaries ultrasound), USG endovaginal, Consulta extranjero (no separate mention; `/en/` covers it) | Consulta urgencia (FAQ explains urgencias), Seguimiento fertilidad, Revisión de cirugía (follow-ups, internal) |
| `/ginecologia/control-de-embarazo/` | USG útero y ovarios (obstétrico), USG estructural / materno-fetal / doppler, Control obstetricia gemelar | — |
| `/ginecologia/papanicolaou-colposcopia-vph/` | Papanicolaou, Colposcopía, Estudio pap-VPH, Cultivo vaginal (mentioned as on medical indication), Biopsia de cérvix, Biopsia-VPH, Cauterización bajo / alto grado, Láser bajo / alto grado | — |
| `/ginecologia/anticonceptivos/` | DIU Mirena, DIU de cobre, DIU mia care, T de plata, Implanon, Retiro de DIU, Retiro de Implanon | — |
| `/ginecologia/salud-mamaria/` | USG de mamas, Biopsia de mama | — |
| `/ginecologia/oncologica/` | Biopsia de endometrio, Biopsia vulvar (assessment happens in the consult) | — |
| `/oftalmologia/` | Consulta general, Consulta extranjero (as above), Sutura por retiro de chalazión | Consulta de urgencia (FAQ) |
| `/oftalmologia/tamiz-visual-recien-nacido/` | Tamiz visual para recién nacido | — |
| `/oftalmologia/oct/` | OCT macular, OCT nervio óptico, OCT macular y nervio óptico | — |
| `/oftalmologia/inyeccion-oftalmologica/` | Inyección oftalmológica | — |
| Not on the site | Pellets; Aplicación de células madre (a tightly regulated area: off unless the doctors and counsel confirm) | — |

- **Packages** (Bienestar Femenino, Salud Femenina, Prevención VPH, Salud Mamaria) are named on their related pages only once the doctors confirm what each includes. Never with a price.
- **Audiences:**
  - Adolescents 12–17 → a note on `/ginecologia/` (with a parent or tutor; a person books every minor, KB-08).
  - Children and newborns → `/oftalmologia/` and the tamiz page.
  - Foreign residents → `/en/`.

### Clinician pages
- Name, honorific, title (KB-03 v2.1), real photo with written OK from the doctor and photographer permission, short bio from facts the doctor confirms.
- **Cédula profesional and issuing institution**, general and specialty (LGS Art. 83). The doctors provide them; we check them against SEP's Registro Nacional de Profesionistas. Without them, clinician pages and the doctor blocks on service pages don't launch.
- Days and hours at UMER (KB-03). Consult length.
- Other practice: Hospital Puerta de Hierro, Tepic, consultorio 407 (KB-03). Shown as a fact line; its booking number only if the doctors confirm (gate 3). Sofía never books Tepic, so the site doesn't either.
- Languages: Spanish. English is listed only once the level is confirmed (KB-03 says "a confirmar").
- Links: Dra. Solís → drafernandasolis.com (`sameAs`). Each doctor → their GBP practitioner profile.

### Reusable data model
Clinic facts live in data files, never in components: Astro content collections, edited through Keystatic (`stack.md`). Each fact carries `kb_ref` and `verified_on`.

| Collection | Holds | UMER source | For the next clinic |
|---|---|---|---|
| `clinic` (singleton) | Legal and brand name, address, WhatsApp and call numbers, prefilled-message tag, hours, timezone, accessibility, parking, `sameAs`, AI-assistant disclosure text, disambiguation note | KB-02 | Same singleton for a solo practice |
| `locations` | Address, geo, hours, map link, notes | KB-02 (1 row) | Location pages switch on only with more than one real location |
| `clinicians` | Name, title, cédulas and institution, photo and release ref, bio, languages and level, schedule per location, affiliations, `sameAs` | KB-03 + doctors | 1 row for a solo practice |
| `specialties` | Name, schema enum, hub copy, clinician refs | KB-03 | — |
| `services` | Name, specialty, clinicians, `kb_id`, patient prep, duration (internal), price (internal; display off), bookable by AI (internal), minimum age, companion required, lead time, schema type, page ref, show flag | KB-04 | The main reuse lever: a new clinic's catalog drops in here |
| `pages` | Service-page grouping: slug, title, H1, meta, primary query, services, FAQ refs, image refs, body | S3 | — |
| `faqs` | Question, answer, scope (global / specialty / page), KB source, verified date | KB-05…08 | — |
| `not_offered` | Services and equipment the clinic doesn't have: X-ray, mammography, CT, MRI, 24 h urgencias | KB-03 negative list | Keeps pages, FAQ and generated imagery from implying them (the lesson from Sofía's radiology case) |
| `legal` | Privacy responsible party, contact, update date, COFEPRIS number (optional) | Counsel | — |
| `media` | File, real / AI-edited / AI-generated, label, release or consent ref | `assets.md` | — |

- **Templates (9):** Home, SpecialtyHub, Service, Clinician, Contact, FAQ, LanguageLanding, Legal, NotFound. Each reads only from the collections.
- **Fit check against a solo practice** (drafernandasolis.com):
  - One clinician and one specialty: the SpecialtyHub merges into Home.
  - Service and Clinician templates stay unchanged.
  - Two cities (her Tepic and La Peñita practices) become two `locations` rows, which switches location pages on.
  - No field in the model is UMER-specific.
- **KB sync:** facts are copied from the Notion KB into the collections by hand, through the agent, with `kb_ref` and `verified_on`; S8 checks the KB for changes each month. An automated Notion → repo sync waits for a second clinic.

### Blog
None. T2, and content at volume belongs to another department.

## Redirects (redesign)
Served from `_redirects` in Workers static assets; `trailingSlash: 'always'`. Anything not listed returns a real 404 (today every unknown URL returns 200).

| Old URL | New URL | Code |
|---|---|---|
| `/especialidades` | `/` | 301 |
| `/casos-de-exito` | `/` | 301 |
| `/agendar-cita` | `/contacto/` | 301 |
| `/contacto` | `/contacto/` | 301 |
| `/preguntas-frecuentes` | `/preguntas-frecuentes/` | 301 |
| `/politica-de-privacidad` | `/aviso-de-privacidad/` | 301 |
| `/terminos-y-condiciones` | `/aviso-de-privacidad/` | 301 (legal text consolidated) |
| `/lovable-uploads/2f6f58d9-a14f-414f-a149-7baa01ef0330.png` (logo; the og:image since the hotfix) | `/og/umer.png` | 301 |

## Conversion paths
Every WhatsApp link carries a prefilled message with the page tag, e.g. "Hola, vengo de la página web de UMER (control de embarazo)." That lets GHL count site conversations per page, which is the before/after for the showcase. GA4 events: `whatsapp_click`, `call_click`, `directions_click`, each with page and service parameters. The AI disclosure sits next to every CTA.

| Audience | Entry page | CTA | Channel |
|---|---|---|---|
| Local women | `/ginecologia/` and its service pages | Agendar por WhatsApp (tagged with the service) | WhatsApp 322 308 0404 → Sofía / Jessica |
| Pregnant women | `/ginecologia/control-de-embarazo/` | Same, with the trimester windows next to it | Same |
| Parents | `/oftalmologia/tamiz-visual-recien-nacido/` | Same, with "avísenos con anticipación" | Same |
| Adults with an eye problem | `/oftalmologia/` | Same | Same |
| Foreign residents | `/en/` | "Message us on WhatsApp" (prefilled in English) | Same; Sofía handles English conversations |
| Patients who know the doctors from Tepic | `/doctores/*` | WhatsApp for La Peñita; the Puerta de Hierro line for Tepic only if gate 3 allows | Same / +52 311 980 1034 |
| Ready to call | Any | "Llamar" button next to WhatsApp (322 308 0404 takes calls, confirmed 2026-10-23) | Phone 322 308 0404 |
| Needs directions | `/contacto/` | "Cómo llegar": Google Maps link to UMER's GBP, not raw coordinates | Maps |

- **First phone screen on every template:** who (UMER and the two doctors), what (two specialties), where (La Peñita), next step (WhatsApp). `taste.md` principle 8.
- **Staging and sales demo:** the WhatsApp number is a build-time setting. A staging copy can point at the demo Sofía number (delivery provides it), so demos never touch the live patient line.

## Schema plan
- **Site-wide graph (every page):**
  - `MedicalClinic`, `@id` `https://umermedical.com/#clinic`:
    - Name "UMER · Unidad Médica de Especialidades Rentería", `alternateName` "UMER", `url`, `logo`, `image` (a real photo).
    - `telephone`: the same number as the GBP; align them first.
    - `address`: Gral. Lázaro Cárdenas 8-A, Centro, 63720 La Peñita de Jaltemba, Compostela, Nayarit, MX. `geo` 21.0383, −105.2489.
    - `openingHoursSpecification`: Mo–Sa 08:00–21:00.
    - `medicalSpecialty`: `Gynecologic`, `Obstetric`, `Oncologic`, `Ophthalmology`. Enum names checked on schema.org: it's `Ophthalmology`, not "Ophthalmologic".
    - `isAcceptingNewPatients` true. `sameAs`: UMER's GBP and facebook.com/umerenteria only. Nothing that points to Clínica Rentería.
  - `WebSite`, `@id` `#website`: publisher `#clinic`, `inLanguage` es-MX.
  - `BreadcrumbList` on every page except home.
- **SpecialtyHub:** `MedicalWebPage`, `about` the specialty enum. `reviewedBy` (the doctor's Person) and `lastReviewed` only once the doctor has approved that page's copy in S3.
- **Service:** `MedicalWebPage` with `about` a `MedicalProcedure` or `MedicalTest` (name, description, preparation where the type supports it). The performing doctor is linked by `@id`. No offers, no prices.
- **Clinician:** `ProfilePage` whose `mainEntity` is a `Person`:
  - `honorificPrefix`, `jobTitle`, `image`, `knowsLanguage`, `sameAs`.
  - `hasCredential`: an `EducationalOccupationalCredential` per cédula, `recognizedBy` the issuing institution.
  - Plus an `IndividualPhysician` (`@id` …`#physician`) with `medicalSpecialty`, `practicesAt` `#clinic`, address, telephone and their own `openingHoursSpecification`. `hospitalAffiliation` (Hospital Puerta de Hierro, Tepic) only if the doctors confirm gate 3.
- **Contact:** `WebPage` with a reference to `#clinic`.
- **FAQ:** plain HTML. No `FAQPage` markup, since the rich result was removed 2026-05-07 (`seo.md`).
- **`/en/`:** `WebPage` with `inLanguage` en, `about` `#clinic`. No hreflang: no Spanish page is its alternate.
- **Not used:** `AggregateRating` or `Review` on our own pages, generic `LocalBusiness`.

## Technical (T1)
- **Rendering and URLs:** Astro static, so every page's text is in the server HTML. `trailingSlash: 'always'`, directory build format, absolute canonicals on `https://umermedical.com/`. `lang="es-MX"` (`en` on `/en/`).
- **Titles and headings:** a unique title and meta description per page, from the `pages` data, and one H1. Title pattern: "{Página} en La Peñita | UMER", kept to 60 characters where possible.
- **Crawling:** `sitemap.xml` at build, excluding the 404. `robots.txt` allows Googlebot, Bingbot, OAI-SearchBot, Claude-SearchBot and PerplexityBot. Training crawlers (GPTBot, ClaudeBot, Google-Extended): **Allowed** (Francisco, 2026-10-23; on the Site record). Real 404 status (`not_found_handling: "404-page"`).
- **Analytics:** GA4, Search Console (property verified 2026-10-23), Bing Webmaster Tools, and IndexNow on deploy.
- **Images and motion:** images through Astro `<Picture>`. The LCP element is a real photo, never animated. Calm motion budget: ≤ 15 KB of motion JS per page.

## Open for sign-off
| # | Item | Who | Default if no answer |
|---|---|---|---|
| 1 | ~~Ten service and hub pages: right number?~~ **Closed:** as proposed, at the department's judgment (Francisco, 2026-10-23) | — | — |
| 2 | ~~Training crawlers allowed?~~ **Closed:** allowed | — | — |
| 3 | ~~Does 322 308 0404 take calls?~~ **Closed:** yes, so the call button stays | — | — |
| 4 | Tepic (gate 3): show "también consulta en Hospital Puerta de Hierro, Tepic" and that line's booking number? | Doctors | The fact line only, no number |
| 5 | Inyección oftalmológica: what it treats and the right patient-facing name | Dra. Solís | Page held until answered |
| 6 | What each package includes | Doctors | Packages not mentioned |
| 7 | Cédulas and institutions for both doctors (Francisco is asking them) | Doctors | Clinician pages and doctor blocks don't launch (blocks S7, not S2) |
| 8 | Switch UMER's main GBP phone to 322 308 0404 | Francisco | Decided in S6 |

**Note for delivery:** Sofía's negative list says UMER has no "tomografía". The site will name OCT as "tomografía de coherencia óptica", an eye study UMER does offer. Sofía's KB should carry the same distinction, so she doesn't deny OCT to a patient who read the site.
