---
layout: page
title: Data
permalink: /data/
---

# Data Sources — Rare Hydrologic Events

Document where critical datasets live so teammates and collaborators can access them quickly.

## Core datasets
- **NOAA Atlas 14 (precipitation frequency)** — stored in `data/atlas14/`. Original source: [NOAA PFDS](https://hdsc.nws.noaa.gov/hdsc/pfds/). Use for baseline design storm calculations.
- **NASA IMERG (near real-time precipitation)** — download via [GES DISC](https://disc.gsfc.nasa.gov/datasets?page=1&keywords=IMERG). Place curated subsets in `data/imerg/`.
- **USGS StreamStats and NHDPlus** — watershed boundaries and flowlines saved under `data/streamstats/`. Source: [USGS StreamStats](https://streamstats.usgs.gov/).
- **CDC Social Vulnerability Index** — CSV exports stored in `data/svi/`. Source: [CDC SVI](https://www.atsdr.cdc.gov/placeandhealth/svi/index.html).

## Shared storage (CyVerse)
- Community path: `i:/iplant/home/shared/esiil/Innovation_summit/Group_15`
- Use subfolders such as `shared_data/`, `raw_inputs/`, and `deliverables/` to organize uploads.
- Large rasters (>100 MB) should stay in CyVerse; link to them from notebooks instead of committing to GitHub.

## Data management notes
- Track provenance in [documentation/group-notes.md](https://github.com/CU-ESIIL/resilience-rare-hydrologic-events-management-innovation-summit-2025__15/blob/main/documentation/group-notes.md) or in dataset-specific README files.
- Include license or usage restrictions for each dataset so downstream users know how the data can be shared.
- When updating datasets, add a short entry to [Updates](updates.md) describing what changed and why.
