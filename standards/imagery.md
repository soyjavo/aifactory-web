# Imagery standard

Version 1 · 2026-10-14 · Owner: Web & SEO

This is not legal advice. Anything marked "confirm" goes to HQ or counsel before launch.

## What may be real, edited or generated

| Content | Real photo | AI edit allowed | AI-generated |
|---|---|---|---|
| Clinicians, staff, author bylines | Required, with a signed release | Background cleanup, relighting, color, upscaling. Never the face, body, age or identity. | Never |
| Patients, testimonials, before/after | Required, with written consent (HIPAA authorization in the US; consent plus aviso de privacidad in MX) | Exposure and crop only | Never |
| The client's premises, presented as theirs | Required | Cleanup, lighting, perspective | Never |
| Illustrative scenes with people (not implied staff or patients) | Preferred | Yes | Allowed, labeled |
| Abstract, texture, objects, environments, icons | — | Yes | Allowed |

Why:

- Google's helpful-content guidance names "AI-generated headshots, made-up names, or false credentials" as deceptive creator profiles (updated 2026-10-05).
- FTC rule 16 CFR 465 bans testimonials from people who don't exist.
- California B&P §651 requires disclosing models ("anyone other than an actual patient") and comparable before/after images.

## Labels

- MX: "Imagen ilustrativa generada con IA." on AI-generated images with people.
- US: "Model, not an actual patient." on any person shown in a patient context who isn't one; "AI-generated illustration" on generated images with people.
- California SB 1050 (synthetic performers in ads, effective 2027-01-01): confirm whether it covers still images before using generated people in US ads.

## Workflow

1. **S2 `assets.md`:** a shot list per page, with each slot marked real, AI-edited or AI-generated.
2. **Photo session per clinic:** a pro or a good phone, natural light, same time of day. Releases signed.
3. **Edit pipeline (through the fal MCP unless noted):**
   - Background cleanup: Bria RMBG 2.0.
   - Relighting and consistency across the set: Magnific Relight, or instruction edits with GPT Image 2.5, Nano Banana 2.1 or FLUX 3 (FLUX 3 locks the regions it doesn't edit).
   - Upscaling: Topaz.
4. **Generation (allowed slots only):** GPT Image 2.5 or Nano Banana 2.1 by default. Recheck the leaderboards when a pick is more than three months old.
5. **Export** through Astro `<Picture>`. Originals stay in Drive.

## Rules

- Client photos go only through paid API tiers; free tiers may train on inputs.
- No Midjourney: its terms forbid automated access.
- Keep C2PA and SynthID provenance intact. Set IPTC DigitalSourceType to `trainedAlgorithmicMedia` (generated) or `compositeWithTrainedAlgorithmicMedia` (AI-edited).
- Log every non-original image in `assets.md`: file, source, model or tool, prompt or edit, date, release or consent reference, label shown.
- MX health promotional material shows the clinician's cédula profesional and issuing institution (LGS Art. 83). Whether a site needs a COFEPRIS aviso de publicidad: confirm per client.

## Video

- AI video follows the same table as stills: no AI-generated clinicians, staff or patients.
- Real premises may get ambient motion only (light, sky, foliage). Nothing added, removed or changed.
- Seedance blocks real faces as a starting frame; don't work around it.
- Real footage of staff needs the same signed release as photos.
- Log each clip in `assets.md`: model, prompt, start and end frames, takes, cost.

## Changelog

- 2026-10-14: v1.
- 2026-10-22: Video section added.
