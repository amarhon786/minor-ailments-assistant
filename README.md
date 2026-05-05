# Minor Ailments Assistant

> Open-source structured-intake & documentation tool for Ontario pharmacists practising under the Minor Ailments Program.


<!-- Once you have screenshots, drop them in docs/screenshots/ and uncomment:
![Home screen](docs/screenshots/home.png)
-->

## What this is

A web-based assessment and documentation companion for Ontario pharmacists practising under the Minor Ailments Program (O. Reg. 256/24). The tool walks each OCP assessment-and-prescribing algorithm one question per screen, raises red flags with a clear reason, and at the end generates four structured documents in one click: SOAP note, prescription with Prescriber ID Reference 09, plain-language patient counselling handout, and physician notification fax.

**It is an assessment and documentation tool, not a clinical recommender.** The pharmacist makes every clinical decision; the tool only structures the intake and renders the documents. It never says "this is a UTI, prescribe X." It says "criteria met, no red flags raised — proceed or refer."

## Why I built this

I asked every pharmacist the same question: *what's the slowest part of your day?*

The answer kept coming back: Minor Ailments Program documentation. Every prescription needs a SOAP note, a counselling handout, sometimes a physician fax — and most existing tools either cost money, store patient data on third-party servers, or quietly overstep into clinical decision-making.

This is a free, open-source, local-first alternative.

## Features

- **All 19 authorised conditions** — UTI, allergic rhinitis, conjunctivitis, oral thrush, dermatitis, diaper rash, dysmenorrhea, GERD, hemorrhoids, cold sores, impetigo, insect bites & urticaria, tick-bite Lyme prophylaxis, MSK sprains/strains, canker sores, pinworms, vulvovaginal candidiasis, nausea, mild acne
- **One question per screen, plain language** — walks each OCP algorithm step-by-step
- **Red flags with immediate stop** — each red flag gives a clear reason and routes to referral
- **Four documents in one click** — SOAP note, prescription, patient handout, physician fax — all printable
- **Local-first, PHIPA-clean** — patient data never leaves the browser. No server, no analytics, no third-party storage
- **Searchable history** — past assessments stored locally and reviewable in full, with re-printable documents
- **Print-ready output** — clean print stylesheet strips the chrome for clinical document printing



## Quick start

This is a single-file static HTML app — no build step, no dependencies to install.

**Run locally:**

```bash
git clone https://github.com/amarhon786/minor-ailments-assistant.git
cd minor-ailments-assistant
open index.html        # macOS
# or just double-click index.html on Windows
```

**Deploy to GitHub Pages:**

1. Fork or clone this repo
2. Push to your own repo on GitHub
3. Go to **Settings → Pages**
4. Set **Source** to *Deploy from a branch*, **Branch** to `main`, folder to `/ (root)`
5. Save — your demo will be live at `https://amarhon786.github.io/minor-ailments-assistant/` in about a minute

**Deploy to Vercel / Netlify / Cloudflare Pages:** import the repo, no build settings needed, output directory is `/`.

## Architecture

The whole application is a single `index.html` file containing:

- **Algorithm definitions** as a JSON-shaped `CONDITIONS` object — adding a new condition is a data change, not a code change
- **Screen-based React component tree** with `localStorage`-backed persistence
- **Document templates** (SOAP, Rx, handout, fax) generated dynamically from saved assessment data
- **Print stylesheet** that strips UI chrome so each document prints clean

Two design principles shaped every decision:

1. **Assessment + documentation, not recommendation.** The tool walks the algorithm and surfaces criteria; the pharmacist judges. There is no "this is condition X" output anywhere in the codebase.
2. **Local-first by default.** Every byte of patient data lives in the browser. The server-free architecture is a regulatory and ethical decision, not a technical limitation.

## Tech stack

- React 18 (via CDN — no build step)
- Custom CSS with design tokens (Newsreader serif + IBM Plex Sans + IBM Plex Mono)
- `localStorage` for persistence
- Print stylesheet for clinical documents
- Single HTML file, ~3500 lines, ~165 KB

## Project structure

```
.
├── index.html       # The entire app — React, CSS, content all in one
├── README.md        # You are here
├── DISCLAIMER.md    # Important clinical-use disclaimer
├── LICENSE          # MIT
└── .gitignore
```

## Roadmap

- [ ] Verify each clinical algorithm against the official OCP/CPhA published source
- [ ] Add the 14 proposed-but-not-yet-authorised conditions when OCP expands the program
- [ ] Pharmacist-feedback loop (issue templates for clinicians)
- [ ] Optional cloud-sync for multi-device use (would require a server — would break PHIPA-clean default, may stay opt-in)
- [ ] Port to React + Vite + TypeScript for easier multi-file extension
- [ ] Mobile-responsive refinements for tablet-first pharmacy counter use

## Positioning vs MAPflow

[MAPflow](https://opatoday.com/mapflow) is a commercial minor-ailments tool from the Ontario Pharmacists Association covering all 19 conditions. It validates that the demand exists. This project differs by being **open-source, free, transparent, and local-first** — the algorithms are inspectable, modifiable, and the patient data architecture is auditable from a single HTML file. Different audiences, complementary tools.

## Contributing

Contributions welcome — especially from practising RPhs reviewing the clinical algorithms. Open an issue or PR.

For algorithm updates, please cite the OCP or CPhA source you're aligning to.

## Disclaimer

> **This is a portfolio project. Clinical algorithms have not been verified by a licensed pharmacist.**

The clinical content here is a good-faith approximation of OCP/CPhA-published algorithms but **must not be used for actual patient care without verification against the official sources**. The architecture (assessment + documentation, not recommendation) is sound; the specific clinical thresholds need verification. See [DISCLAIMER.md](DISCLAIMER.md) for the full statement.

## License

[MIT](LICENSE) — do whatever you want with this, no warranty.

## Acknowledgments

- Ontario College of Pharmacists for publishing the Minor Ailments assessment & prescribing algorithms
- Canadian Pharmacists Association for the broader minor ailments framework
- Every pharmacist in Kitchener–Waterloo and Cambridge who answered my cold emails

---

Built by Ali Marhon
