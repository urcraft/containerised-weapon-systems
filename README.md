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

- `index.html` — the entire site: self-contained HTML/CSS/JS, no build step, no framework.
- `data/systems.json` — the dataset the page renders (fetched at runtime).
- `images/` — one representative photo per system, hosted locally.

Type: **Saira Condensed** (display) · **Public Sans** (body) · **IBM Plex Mono** (data plates), via Google Fonts.

## Sources & licensing

Data is compiled from 70+ public sources — defence media (The War Zone, Naval News, Army Recognition, European Security & Defence), manufacturer material, government releases and reputable encyclopaedias — cited per entry.

Photos are drawn from **Wikimedia Commons**, **U.S. Department of Defense** public-domain imagery, and cited defence-media / manufacturer sources; each image is credited in its caption. Where an image is not public domain it is used for non-commercial documentation and journalism, with attribution.

## Disclaimer

This catalogue documents **publicly reported** hardware for research and journalism. Dates, VLS-cell counts and missile fits are best-available estimates; newly unveiled 2026 systems are flagged medium-confidence. Nothing here is operational guidance.
