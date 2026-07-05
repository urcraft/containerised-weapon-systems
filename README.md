# The Box That Fights — a registry of containerised weapon systems

An open-source, single-page catalogue of military hardware that is **hidden inside, launched from, or built into standard shipping containers** — plotted on a vertical timeline from Russia's 2010 Club-K to the newest 2026 prototypes.

**Live site:** https://urcraft.github.io/containerised-weapon-systems/

## What's here

27 systems across 16 nations and nine weapon classes (strike missiles, loitering-munition swarms, directed energy, air-defence / C-UAS, artillery, naval "arsenal ships", covert/disguised launchers, autonomous vehicles and modular mission systems). Each entry carries an official name, builder, country, the most timeline-relevant date, a short factual summary, cited sources, and one representative photo.

Every system is tagged by **concealment posture**, shown by the connector colour on the timeline:

- 🟥 **Concealed cargo** — disguised as ordinary freight to hide the weapon (Club-K, YJ-18C, DPRK MLRS)
- 🟧 **Container form-factor** — an ISO-sized box that openly opens/erects to fire (Mk 70, Typhon, CML, HELIOS)
- 🟦 **Modular deck launcher** — a container module bolted onto a ship or vehicle deck (LORA, C-DOME, Zhong Da 79)

## How it's built

- `index.html` — the entire site: self-contained HTML/CSS/JS, no framework.
- `data/systems.xlsx` — **the editable dataset and single source of truth.** One row per system; open it in Excel, Google Sheets, LibreOffice or Numbers to add or change entries.
- `data/systems.json` — generated from the spreadsheet at deploy time and fetched by the page at runtime. It is **not** committed (see `.gitignore`).
- `scripts/build_data.py` — converts `systems.xlsx` → `systems.json`.
- `scripts/json_to_xlsx.py` — the inverse, used to (re)generate the spreadsheet from JSON if needed.
- `images/` — one representative photo per system, hosted locally.
- `favicon.svg` / `favicon.ico` / `apple-touch-icon.png` — the site icon (a corrugated shipping container with three missiles erecting from it, in the site palette).

Type: **Saira Condensed** (display) · **Public Sans** (body) · **IBM Plex Mono** (data plates), via Google Fonts.

### Editing the data

1. Open `data/systems.xlsx` and edit the rows. Each card is one row.
   - Simple fields have one column each: `name`, `builder`, `country`, `summary`, etc.
   - The photo is split across `photo_file`, `photo_credit`, `photo_license`, `photo_source`.
   - Up to three sources use `source1_url` / `source1_title` … `source3_url` / `source3_title`.
   - Add a new system with a new row; drop its photo under `images/` and point `photo_file` at it (e.g. `images/new-system.jpg`).
2. Commit the spreadsheet (and any new image) and push to `main`.
3. GitHub Actions rebuilds `systems.json` and redeploys the site automatically.

To preview locally, regenerate the JSON first and serve the folder:

```bash
pip install openpyxl
python scripts/build_data.py          # writes data/systems.json
python -m http.server                 # then open http://localhost:8000
```

### Deployment

`.github/workflows/deploy.yml` runs on every push to `main`: it builds `systems.json` from the spreadsheet, assembles `index.html` + `images/` + the icon files + the generated JSON, and publishes to GitHub Pages. **One-time setup:** in the repo's **Settings → Pages**, set **Source** to **GitHub Actions**.

## Sources & licensing

Data is compiled from 70+ public sources — defence media (The War Zone, Naval News, Army Recognition, European Security & Defence), manufacturer material, government releases and reputable encyclopaedias — cited per entry.

Photos are drawn from **Wikimedia Commons**, **U.S. Department of Defense** public-domain imagery, and cited defence-media / manufacturer sources; each image is credited in its caption. Where an image is not public domain it is used for non-commercial documentation and journalism, with attribution.

## Disclaimer

This catalogue documents **publicly reported** hardware for research and journalism. Dates, VLS-cell counts and missile fits are best-available estimates; newly unveiled 2026 systems are flagged medium-confidence. Nothing here is operational guidance.
