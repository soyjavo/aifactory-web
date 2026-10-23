# Architecture — drafernandasolis.com
S1 Architecture · reads `brief.md` (2026-10-23), `standards/seo.md` (T1 + T2), `standards/stack.md`, and UMER's approved `sites/umer/architecture.md` (shared skeleton, query split) · Date: 2026-10-23 · Status: **draft — items in §Open for sign-off; surgical pages wait on her answers**

**Decisions this rests on:**
- **Shape:** a solo practice on UMER's reusable skeleton: one clinician, one specialty, two real locations. Per UMER's fit check, the specialty hub merges into Home and location pages switch on.
- **Scope:** her ophthalmology services. Clinical services come from KB-04 / KB PH (the same catalog in both locations). Surgical services come from her intake form and launch only as she confirms she performs them (brief Q4). **No prices** (her answer on the form).
- **Split with umermedical.com:** this site owns her name, surgery, Tepic / Puerta de Hierro, children's eyes and retina. UMER owns "oftalmólogo en La Peñita" and its La Peñita service pages (tamiz, OCT, inyección); her site links there instead of competing.
- **No hours anywhere** (they vary, Francisco 2026-10-23). **Emergencies:** 911, or the Hospital Puerta de Hierro ER, 24 h; neither consultorio handles emergencies.
- **Language:** Spanish. English waits on the gate shared with UMER; if it opens, one `/en/` page on UMER's LanguageLanding template.
- **Tier and approach:** T2 Local; Calm.

## Sitemap
18 URLs if every surgical page is confirmed, 17 indexable. Templates: Home, ServicesIndex, Service, Clinician, Location, Contact, FAQ, Legal, NotFound. That is UMER's set with SpecialtyHub folded into Home and LanguageLanding unused unless English opens, plus Location (which UMER's model switches on at two real locations) and ServicesIndex (see §Content model).

| URL | Page | Template | Purpose | Intent | Primary query (es) | Schema |
|---|---|---|---|---|---|---|
| `/` | Inicio | Home | First phone screen: who (Dra. Fernanda Solís, cirujana oftalmóloga), the one thing, where (Tepic and La Peñita), next step (WhatsApp by location). Routes to services, both consultorios and her profile | Local, name | "oftalmólogo en Tepic", "Dra. Fernanda Solís oftalmóloga" | WebSite, WebPage, site graph |
| `/sobre-mi/` | Sobre la Dra. Solís | Clinician | Real photo, cédulas and institution, certification, memberships, bio, both consultorios, what she treats | Name, trust | "Dra. María Fernanda Solís Rendón" | ProfilePage, Person, IndividualPhysician |
| `/servicios/` | Servicios | ServicesIndex | Every service in patient language, grouped (consulta, niños, retina, cirugía), each with where it happens | Navigational | — | CollectionPage, BreadcrumbList |
| `/servicios/consulta-oftalmologica/` | Consulta oftalmológica | Service | Full eye exam for adults and children: graduación, eye pressure, fondo de ojo; follow-up for diabetes and hypertension; what to bring; dilation means bringing a companion | Transactional | "examen de la vista con oftalmólogo Tepic", "revisión de la vista Tepic" | MedicalWebPage + MedicalTest |
| `/servicios/oftalmologia-pediatrica/` | Ojos de niños | Service | Children's eye exam, first glasses, estrabismo (assessment), and the **tamiz visual del recién nacido** as a section (from 28 days; premature babies without waiting; towel; arrive 30 min early) | Parents, book | "oftalmólogo pediatra Tepic", "tamiz visual Tepic" | MedicalWebPage + MedicalTest |
| `/servicios/retina-y-diabetes/` | Retina, diabetes y mácula | Service | Diabetic retinopathy and macular degeneration: OCT (three variants), inyección intravítrea, retina laser. Prep from KB PH (dilation, companion, no makeup) | Problem, book | "retinopatía diabética Tepic", "estudio OCT Tepic" | MedicalWebPage, about MedicalCondition; MedicalTest / MedicalProcedure |
| `/servicios/cirugia-catarata/` | Cirugía de catarata | Service | What a cataract is, when to operate, the lens implant, recovery, where she operates. Post-op: her discharge instructions; 911 in an emergency | Transactional | "operación de cataratas Tepic", "cirugía de catarata Tepic" | MedicalWebPage + SurgicalProcedure |
| `/servicios/glaucoma/` | Glaucoma | Service | Diagnosis, drops, laser and surgery; why follow-up matters | Problem, book | "glaucoma Tepic", "presión alta en los ojos" | MedicalWebPage, about MedicalCondition |
| `/servicios/estrabismo/` | Estrabismo en niños y adultos | Service | Assessment and surgery of a deviated eye at any age | Problem, book | "estrabismo Tepic", "ojo desviado niño" | MedicalWebPage + SurgicalProcedure |
| `/servicios/pterigion/` | Pterigión (carnosidad en el ojo) | Service | What it is, sun exposure, when to remove it, recovery | Problem, book | "carnosidad en el ojo Tepic", "cirugía de pterigión" | MedicalWebPage + SurgicalProcedure |
| `/servicios/cirugia-plastica-ocular/` | Párpados y vías lagrimales | Service | Drooping eyelid, chalazion (KB: sutura por retiro de chalazión), tear ducts | Problem, book | "párpado caído cirugía Tepic", "chalazión" | MedicalWebPage + SurgicalProcedure |
| `/servicios/lasik-prk/` | Cirugía refractiva LASIK / PRK | Service | Candidacy, LASIK vs PRK, where it's done | Transactional | "cirugía láser de ojos Tepic", "LASIK Tepic" | MedicalWebPage + SurgicalProcedure |
| `/consultorios/tepic-puerta-de-hierro/` | Consultorio 407, Hospital Puerta de Hierro | Location | Address, floor and room, map link to the Tepic GBP, phone and WhatsApp, GHL online booking, the hospital's 24 h ER for emergencies | Local, navigational | "oftalmólogo Puerta de Hierro Tepic" | WebPage + location node, BreadcrumbList |
| `/consultorios/la-penita/` | UMER La Peñita | Location | Address, map link to the La Peñita GBP, phone and WhatsApp, the days she's usually there (no hours), links to UMER's ophthalmology pages | Navigational (her patients) | "Dra. Fernanda Solís La Peñita" — not "oftalmólogo en La Peñita", which is UMER's | WebPage + location node, BreadcrumbList |
| `/contacto/` | Contacto | Contact | Both consultorios side by side, "¿En qué consultorio?" CTA, emergency note, email | Navigational | "Dra. Fernanda Solís teléfono" | WebPage, BreadcrumbList |
| `/preguntas-frecuentes/` | Preguntas frecuentes | FAQ | Emergencies (911), the difference between a *consulta de urgencia* and an emergency, children and minors, dilation and companions, what she doesn't offer | Long tail | Many | WebPage, BreadcrumbList |
| `/aviso-de-privacidad/` | Aviso de privacidad | Legal | LFPDPPP notice; counsel reviews against the 2025 law. The medical-information disclaimer moves here from today's terms page | — | — | WebPage |
| `/404` | Página no encontrada | NotFound | Links to services, both consultorios, WhatsApp; real 404 status | — | — | none, noindex |

**Launch rule for service pages:**
- **Launch on records:** consulta, ojos de niños, retina y diabetes. They are in KB-04 / KB PH, and she does them in both places.
- **Launch only on her yes (brief Q4):** catarata, glaucoma, estrabismo, pterigión, párpados, LASIK/PRK. These are in her intake form, but the site will say *she* operates, and *where*. A page she doesn't confirm folds into its closest page or into `/servicios/` (redirects below).

**Navigation:**
- Header: Servicios · Consultorios (Tepic, La Peñita) · Sobre mí · Contacto · [Agendar por WhatsApp].
- Footer: both consultorios (address and phone), cédulas, the emergency line, aviso de privacidad, AI disclosure, link to umermedical.com.
- Each service page links to `/servicios/`, `/sobre-mi/` and the consultorio(s) where it happens; `/sobre-mi/` lists every service; Home links everything. No orphans.

## Keyword and intent map
No keyword tool was used and local volumes are small. Sources: Search Console (3 months to 2026-10-20), the Doctoralia Tepic list, Top Doctors, and UMER's map. Patient words come before clinical ones because that is how people search ("carnosidad", "ojo desviado", "operación de cataratas").

| Query (es) | Intent | Competition note | Target URL |
|---|---|---|---|
| oftalmólogo Tepic · oftalmólogos en Tepic · oculista Tepic · oftalmóloga Tepic | Find and book | Doctoralia leaders (Rodríguez Ascencio 650 opinions, Miramontes 554, Carro 325) and the Maps pack. GSC: 65 impr., pos 10.3, the only generic query with a click | `/` |
| Dra. Fernanda Solís · María Fernanda Solís · Dra. Solís oftalmóloga | Name | 394 impr. for "fernanda solis", 0 clicks: the name is shared with other people. Every title says *Dra.* and *oftalmóloga* | `/`, then `/sobre-mi/` |
| oftalmólogo pediatra Tepic · oftalmopediatría · oftalmólogo para niños | Parents | ~50 impr. in 3 months, positions 1–12, no page to land on. No Tepic ophthalmologist claims children on Doctoralia; Top Doctors' nearest are in Guadalajara | `/servicios/oftalmologia-pediatrica/` |
| tamiz visual Tepic · tamiz oftalmológico recién nacido Tepic | Parents, book | Mostly academic content | `/servicios/oftalmologia-pediatrica/` (section) |
| examen de la vista con oftalmólogo · revisión de la vista · graduación Tepic | Mixed (optician vs doctor) | Opticians compete; say plainly it's a medical exam | `/servicios/consulta-oftalmologica/` |
| retinopatía diabética Tepic · diabetes y la vista · degeneración macular · estudio OCT Tepic · inyección en el ojo | Problem, book | Hospital and lab listings | `/servicios/retina-y-diabetes/` |
| operación de cataratas Tepic · cirugía de catarata Nayarit | Book | The three Doctoralia leaders all list catarata | `/servicios/cirugia-catarata/` |
| glaucoma Tepic · presión alta en los ojos | Problem | Rodríguez Ascencio and Carro list glaucoma surgery | `/servicios/glaucoma/` |
| estrabismo Tepic · ojo desviado · ojos cruzados niño | Parents, problem | GSC: "especialistas en estrabismo", pos 20 | `/servicios/estrabismo/` |
| carnosidad en el ojo · pterigión Tepic · cirugía de pterigión | Problem | Not checked yet | `/servicios/pterigion/` |
| párpado caído cirugía · chalazión · bolita en el párpado · vías lagrimales | Problem | Dr. Nuño Moya (oculoplastics, Brasilia 22) | `/servicios/cirugia-plastica-ocular/` |
| LASIK Tepic · cirugía láser de ojos · operación para no usar lentes | Book | Five Doctoralia listings offer refractive laser (Rodríguez Ascencio, Carro, Miramontes, Ballesteros, Corona) | `/servicios/lasik-prk/` |
| oftalmólogo Puerta de Hierro · oftalmología Puerta de Hierro Tepic | Find | GSC: 6 impr. across three phrasings | `/consultorios/tepic-puerta-de-hierro/` |
| oftalmólogo urgencias Tepic | Emergency | Don't compete: the FAQ sends people to 911 and the hospital ER | `/preguntas-frecuentes/` |

**Split with umermedical.com** (so the two sites don't compete):

| Query | Owner | Other site |
|---|---|---|
| oftalmólogo en La Peñita · oculista La Peñita · doctor de los ojos Guayabitos | UMER `/oftalmologia/` | Her La Peñita page links there, no targeting |
| tamiz visual La Peñita / Nayarit | UMER tamiz page | Hers targets Tepic |
| estudio OCT La Peñita · inyección en el ojo (La Peñita) | UMER OCT / inyección pages | Her retina page targets Tepic and the conditions |
| oftalmólogo pediatra (Tepic, Nayarit) | **Hers** (the dedicated page) | **Proposal for the UMER run:** its `/oftalmologia/` section mentions children but drops "oftalmólogo pediatra Nayarit" as a target |
| Dra. Fernanda Solís (any variant) | Hers | UMER's `/doctores/fernanda-solis/` second, `sameAs` here (already in UMER's S1) |
| any surgery | Hers | UMER has no surgery pages |

## Content model
### On UMER's collections
Same collections, same fields, so the skeleton is truly shared (`sites/umer/architecture.md` §Reusable data model).

| Collection | Her rows | Source |
|---|---|---|
| `clinic` (singleton) | Her practice: "Dra. María Fernanda Solís Rendón — Oftalmología", default WhatsApp, prefilled-message tag, `sameAs`, AI disclosure, disambiguation note (*Dra.*, *oftalmóloga*) | Brief |
| `locations` | 2 rows: Tepic (consultorio 407) and La Peñita. Address, geo, map link to that location's GBP, public phone, WhatsApp, `has_online_booking` (Tepic: GHL calendar), `hours: null` | Brief; Francisco |
| `clinicians` | 1 row: cédulas 11984010 / 13206835 (UdeG), certification **(pending her)**, memberships (SMO; Sociedad de Oftalmólogos de Nayarit, member), photo and release ref, bio | Her form; KB-03; her answers |
| `services` | KB-04 ophthalmology rows (consulta general, consulta de urgencia, consulta extranjeros, OCT ×3, tamiz, inyección, chalazión) plus surgical rows from her form, each with `confirmed_by_doctor` and `locations` | KB-04 / KB PH; her form |
| `pages` | Every page above | S3 |
| `faqs` | Includes the 911 answer and the *consulta de urgencia* distinction | Francisco 2026-10-23; KB |
| `not_offered` | Emergency care (either consultorio); 24 h service; anything she declines in Q4 | Francisco; her answers |
| `media` | Her real photos (retouch only), generated objects and places, labels, release ref | `assets.md` |

- **Services × locations:** a service lists the locations where it really happens. Consults, children, tamiz, OCT and inyección: both (KB PH has the same catalog in Tepic). Surgery: wherever she answers in Q4 — probably the hospital's operating room, but not assumed. A page title names only the real locations.
- **Not shown:** prices (her choice); "consulta para extranjeros" as a separate offer (counsel hasn't reviewed nationality-based pricing, same rule as UMER); "consulta de urgencia" as a page (it's an urgent appointment in the catalog, not an emergency service; it lives in the FAQ next to the 911 rule so nobody reads it as one).
- **Two templates UMER's run hasn't built:** Location (its model already anticipates it for a second real location) and ServicesIndex, because a solo practice with ~9 services needs the list page that UMER's hubs provide. Both read only from the collections, so the next clinic gets them free.

### Clinician page
- Real photo (her existing ones, retouch only, release on file before the showcase use).
- Cédula profesional and cédula de especialidad with issuing institution (LGS Art. 83); checked against SEP's Registro Nacional de Profesionistas before launch.
- Certification: exact body and name from her certificate. Until then the page says nothing about certification rather than "certificada".
- Memberships: Sociedad Mexicana de Oftalmología; Sociedad de Oftalmólogos de Nayarit (member).
- No years, patient counts or "15+ años" unless she confirms them (brief Q5).

### Blog
None. Her form asks for one (eye care, check-ups, tamiz). That's content production: the S8 monthly quota or the future content department, not this build.

## Redirects (redesign)
Served from `_redirects` in Workers static assets; `trailingSlash: 'always'`. Anything not listed returns a real 404 (the hotfix made every unknown URL return 200). Only `/` has search equity today, so these protect links and shares, not rankings.

| Old URL | New URL | Code |
|---|---|---|
| `/sobre-mi` | `/sobre-mi/` | 301 |
| `/servicios` | `/servicios/` | 301 |
| `/servicios/cirugia-catarata` | `/servicios/cirugia-catarata/` | 301 |
| `/servicios/cirugia-glaucoma` | `/servicios/glaucoma/` | 301 |
| `/servicios/oftalmologia-pediatrica` | `/servicios/oftalmologia-pediatrica/` | 301 |
| `/servicios/cirugia-plastica-ocular` | `/servicios/cirugia-plastica-ocular/` | 301 |
| `/servicios/lasik-prk` | `/servicios/lasik-prk/` | 301 |
| `/contacto` | `/contacto/` | 301 |
| `/agendar` | `/contacto/` | 301 (online booking moves to the Tepic page; contact routes by location) |
| `/preguntas-frecuentes` | `/preguntas-frecuentes/` | 301 |
| `/privacidad` | `/aviso-de-privacidad/` | 301 |
| `/terminos-y-condiciones` | `/aviso-de-privacidad/` | 301 (legal text consolidated, as on UMER) |
| `/lovable-uploads/3cac8bfb-70d9-40ee-b19b-265bf8d8c9c8.png` (today's og:image and favicon) | `/og/dra-solis.png` | 301 |

If a surgical page doesn't launch, its old URL (where one exists) points to `/servicios/` instead.

## Conversion paths
Two locations means every CTA first answers **"¿En qué consultorio?"** with two buttons, Tepic and La Peñita, then opens that location's WhatsApp. A service page that happens in one place skips the question.

- Every WhatsApp link carries a prefilled message with page and location, e.g. "Hola, vengo de la página de la Dra. Fernanda Solís (catarata, Tepic)". GHL can then count site conversations per page: the showcase's before and after.
- GA4 events, same names as UMER: `whatsapp_click`, `call_click`, `booking_click`, `directions_click`, each with page, service and location parameters.
- **Keep the existing GA4 property** (`G-XF18KGEHHY`), so the baseline carries across the relaunch.
- The AI disclosure sits next to every CTA that reaches an agent.

| Audience | Entry page | CTA | Channel |
|---|---|---|---|
| Adults with an eye problem | `/`, `/servicios/consulta-oftalmologica/`, problem pages | Agendar por WhatsApp → location choice | Tepic 311 980 1034 **(WhatsApp: confirm)** · La Peñita 322 308 0404 (WhatsApp, AI assistants answer — UMER S1) |
| Parents | `/servicios/oftalmologia-pediatrica/` | Same; a note that a person books every minor (KB-08) | Same |
| Cataract / surgery patients | Surgical pages | Same, tagged with the procedure | Same |
| Patients who prefer to book online | `/consultorios/tepic-puerta-de-hierro/` | "Agenda en línea" (GHL calendar, Tepic only) | GHL `links.intelvec.com` |
| Ready to call | Any | "Llamar" next to WhatsApp | Tepic 311 980 1034 · La Peñita 322 308 0404 |
| Needs directions | Location pages | "Cómo llegar": link to that location's GBP | Maps |
| Emergency | FAQ, footer, contact, cataract page | "Llama al 911"; Hospital Puerta de Hierro ER, 24 h | Phone |
| Her operated patients | Cataract and surgical pages | The number in their discharge instructions; never published | — |

- **Public numbers:** one per location, the same on the site and its GBP (brief proposal; confirm Tepic). Human-assistance lines (311 910 0090, 322 158 2021) stay inside the agent flows.
- **First phone screen on every template:** who, what, where (both cities), next step. `taste.md` principle 8.
- **Staging and demos:** WhatsApp numbers are build-time settings, as on UMER, so a staging copy can point at a demo agent.

## Schema plan
One identity across both sites: UMER's `/doctores/fernanda-solis/` references `https://drafernandasolis.com/#dra-solis`.

- **Site-wide graph (every page):**
  - `Person`, `@id` `#dra-solis`: name, `honorificPrefix` "Dra.", `jobTitle` "Cirujana oftalmóloga", `image` (a real photo), `alumniOf` Universidad de Guadalajara, `memberOf` (SMO; Sociedad de Oftalmólogos de Nayarit), `hasCredential` (one `EducationalOccupationalCredential` per cédula, `recognizedBy` the issuing institution; certification added when confirmed), `knowsLanguage` es, `workLocation` both location nodes, `sameAs`: facebook.com/oftalmologiatepic, instagram.com/drafernandasolis, Doctoralia, both GBPs, `https://umermedical.com/doctores/fernanda-solis/`.
  - `IndividualPhysician`, `@id` `#physician`: `medicalSpecialty` `Ophthalmology` (enum checked on UMER's side), `isAcceptingNewPatients` true, `practicesAt` both location nodes, `hospitalAffiliation` Hospital Puerta de Hierro, Tepic.
  - Location nodes, `@id` `#consultorio-tepic` and `#consultorio-la-penita`: type `Physician` (a MedicalBusiness), each mirroring its GBP practitioner profile exactly: name, address, `geo`, `telephone` (the public number), `hasMap` and `sameAs` its GBP URL. `containedInPlace`: Hospital Puerta de Hierro (a `Hospital` node with address) and UMER (`https://umermedical.com/#clinic`). **No `openingHoursSpecification`** — hours vary.
  - `WebSite`, `@id` `#website`: publisher `#dra-solis`, `inLanguage` es-MX.
  - `BreadcrumbList` on every page except home.
- **Service:** `MedicalWebPage` with `about` a `MedicalTest`, `MedicalProcedure`, `SurgicalProcedure` or `MedicalCondition`, as in the sitemap; `provider` `#physician`; `reviewedBy` `#dra-solis` and `lastReviewed` only once she approves that page's copy in S3. No offers, no prices.
- **Clinician:** `ProfilePage`, `mainEntity` `#dra-solis`.
- **ServicesIndex:** `CollectionPage` listing the service pages.
- **Location:** `WebPage`, `about` its location node.
- **FAQ:** plain HTML; no `FAQPage` (rich result removed 2026-05-07, `seo.md`).
- **Not used:** `AggregateRating`, `Review`, `openingHoursSpecification`, generic `LocalBusiness`.

## Technical (T1)
- **Rendering and URLs:** Astro static, so every page's text is in the server HTML (today only the home page's is). `trailingSlash: 'always'`, directory build format, absolute canonicals on `https://drafernandasolis.com/` (apex; `www` 301s to it). `lang="es-MX"`.
- **Titles:** unique title and meta description per page from `pages`; one H1. Pattern "{Página} en {ciudades reales} | Dra. Fernanda Solís", ≤ 60 characters where possible. Never her name alone, given the ambiguity in GSC.
- **Crawling:** `sitemap.xml` at build, excluding the 404; resubmitted in Search Console at launch (first submitted 2026-10-23). `robots.txt` allows Googlebot, Bingbot, OAI-SearchBot, Claude-SearchBot, PerplexityBot. Training crawlers: **recommend Allowed**, matching UMER; record on the Site.
- **Analytics:** existing GA4 property; Search Console (domain property; its DNS TXT record survives the cutover); Bing Webmaster Tools and IndexNow on deploy.
- **Images and motion:** Astro `<Picture>`. The LCP element is a real photo or a still, never animated. Calm budget: ≤ 15 KB motion JS per page. Generated images only for objects and places, logged in `assets.md`.

## Open for sign-off
| # | Item | Who | Default if no answer |
|---|---|---|---|
| 1 | 10 service-side pages (index + 3 on records + up to 6 surgical, each on her yes) | Francisco | As proposed |
| 2 | Two location pages under `/consultorios/` | Francisco | As proposed |
| 3 | Tepic public number 311 980 1034 and whether it takes WhatsApp | Francisco | Call only on 311 980 1034; WhatsApp goes to La Peñita's 322 308 0404 with "Tepic" in the prefilled message |
| 4 | Training crawlers allowed (as UMER) | Francisco | Allowed |
| 5 | Which surgeries she performs and where (brief Q4) | Dra. Solís | Those pages don't launch |
| 6 | Inyección oftalmológica: what it treats, patient-facing name (same question as UMER's #5) | Dra. Solís | Named only as part of the retina page, no condition claims |
| 7 | Proposal to the UMER run: drop "oftalmólogo pediatra Nayarit" as a target on UMER's `/oftalmologia/` | UMER run / Francisco | Both sites target it and split the signal |
| 8 | English: in or out (shared gate) | Francisco (HQ) + client | Spanish only |
