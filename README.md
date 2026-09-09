# Hand-on Workshop: From Flood Mapping to Critical Infrastructure Accessibility 

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/amaletaa/SESAC-Beginner_EO_Analysi_Series/blob/main/sweden_2020_flood_accessibility_final.ipynb)
![License](https://img.shields.io/badge/code-MIT-blue)

A hands-on Earth Observation workshop notebook that follows one real flood, start to finish: from a raw Sentinel-1 radar signal, to a flood map, to which roads it cuts, to who loses access to a hospital because of it.

Built for the **SESAC Beginner EO Analysis Series** ("From Flood Mapping to Critical Infrastructure Accessibility"), Lund University, September 2026.

## The story

In February 2020, storms Ciara and Dennis brought sustained, heavy rainfall to southwestern Sweden. Sweden's Civil Contingencies Agency (MSB) requested Copernicus Emergency Mapping — activation **EMSR427** — which ended up covering 12 areas across roughly 41,200 km² of southern Sweden.

This notebook focuses on one of those areas: the **Viskan river valley**, from **Borås** down to **Skene**, in Sjuhärad — one of the two rivers EFAS flagged with the highest flood risk in the whole event. The study area is deliberately widened to include both **Södra Älvsborgs Sjukhus (SÄS)** hospital sites, Borås and Skene.

## What the notebook does

1. **Satellite data** — pulls a before/during pair of Sentinel-1 SAR images over the flood window.
2. **Flood detection** — turns the raw radar signal into a binary flood mask, using a simple, transparent, two-condition rule (absolute threshold + significant drop from baseline).
3. **Roads & infrastructure** — pulls the road network and four critical-facility categories (hospitals, fire stations, police, schools) from OpenStreetMap, and intersects them with the flood extent.
4. **Accessibility analysis** — builds a road network graph and computes how much of it is reachable within 5/10/15 minutes of each facility category, normal vs. flood conditions.
5. **Exposure** — checks the result against population (SCB grid) and land cover (NMD2018), both to see who's affected and as a quality check on the SAR method itself.

No coding experience is needed to run it — every cell is pre-written; the job is to run each cell in order and interpret the output.

## Repository structure

```
.
├── README.md
├── sweden_2020_flood_accessibility_final.ipynb   # the workshop notebook
├── population.tif                                # SCB 1 km population grid, pre-clipped to the AOI
├── landcover.tif                                  # NMD2018 land-cover raster, pre-clipped to the AOI
└── slides/
    └── Beginner_EO_Analysis.pdf                  # presentation slides used alongside the notebook
```

## Data sources

| Data | Source | Account needed? |
|---|---|---|
| Sentinel-1 GRD SAR (VH) | Copernicus Data Space Ecosystem (Sentinel Hub) | **Yes** — free CDSE OAuth client |
| Roads + hospitals / fire stations / police / schools | OpenStreetMap (`osmnx`) | No |
| Population grid | SCB (Statistics Sweden), 1 km grid | No |
| Land cover raster | NMD2018, Naturvårdsverket (Swedish EPA) | No |

Only the Sentinel-1 step needs an account. Everything else runs the moment you execute the cell.

## How to run it

1. Click the **Open in Colab** badge above, or open the `.ipynb` directly in Google Colab.
2. If you don't already have one, create a free account at the [Copernicus Data Space Ecosystem](https://dataspace.copernicus.eu), then create a Sentinel Hub OAuth client (Profile icon → Sentinel Hub → User Settings → OAuth clients → Create).
3. Run every cell top to bottom. When prompted, paste your Client ID and Client Secret — these are typed live via `getpass` and never saved into the notebook file.
4. If Colab asks you to restart the runtime after the first cell (package installation), that's expected — restart, then continue from the next cell.

## Credits & data licenses

- **Sentinel-1 / Copernicus Data Space Ecosystem** — © European Union, Copernicus Sentinel data.
- **Roads & critical facilities** — © [OpenStreetMap](https://www.openstreetmap.org/copyright) contributors, ODbL.
- **Population grid** — SCB (Statistics Sweden).
- **Land cover (NMD2018)** — Naturvårdsverket (Swedish Environmental Protection Agency), CC0.
- Workshop developed for **SESAC** (Swedish Competence Centre for Satellite-Enabled Social Science Analytics), with support from Rymdstyrelsen (Swedish National Space Agency).

Code in this repository is shared under the MIT License; the datasets above retain their own original licenses as listed.

## Author

Chantziara Amalia Nikoleta — SESAC, Project Assistant.

---

*If you use or adapt this notebook, a link back to this repository is appreciated.*
