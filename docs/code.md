---
layout: page
title: Code
permalink: /code/
---

# Code Library — Hydrologic Resilience Toolkit

Use this page to catalog the notebooks and scripts you want others to run. Keep entries short and link directly to the files in this repository.

## Quick start
- Place notebooks, scripts, and helper modules inside the [`code/`](https://github.com/CU-ESIIL/resilience-rare-hydrologic-events-management-innovation-summit-2025__15/tree/main/code) directory.
- Add a README or inline comments that list required inputs and environment dependencies.
- Drop rendered outputs (PNGs, GIFs, HTML) in `docs/assets/results/` so they can be featured on the homepage.

## Featured workflows

### Extreme precipitation summarizer
- **Path:** [`code/extreme_precipitation_summary.ipynb`](https://github.com/CU-ESIIL/resilience-rare-hydrologic-events-management-innovation-summit-2025__15/blob/main/code/extreme_precipitation_summary.ipynb)
- **Purpose:** Calculates 24-hour return period rainfall using NOAA Atlas 14 grids and prepares county-level summaries.
- **Inputs:** `data/atlas14/*.tif`
- **How to run:** Open in JupyterLab → run all cells. Requires `xarray`, `rasterio`, and `geopandas`.
- **Outputs:** `docs/assets/results/extreme_rainfall_map.png`

### Exposure dashboard builder
- **Path:** [`code/exposure_dashboard.py`](https://github.com/CU-ESIIL/resilience-rare-hydrologic-events-management-innovation-summit-2025__15/blob/main/code/exposure_dashboard.py)
- **Purpose:** Generates Plotly Express visualizations and exports HTML dashboards for stakeholder briefings.
- **Inputs:** `data/exposure/critical_facilities.geojson`, `outputs/risk_scores.csv`
- **How to run:**
  ```bash
  python code/exposure_dashboard.py --config configs/dashboard.yaml
  ```
- **Outputs:** `docs/assets/results/exposure_dashboard.png` and `outputs/dashboard.html`

### Social vulnerability join
- **Path:** [`code/social_vulnerability_join.R`](https://github.com/CU-ESIIL/resilience-rare-hydrologic-events-management-innovation-summit-2025__15/blob/main/code/social_vulnerability_join.R)
- **Purpose:** Joins CDC Social Vulnerability Index data with watershed boundaries to create composite resilience metrics.
- **Inputs:** `data/svi/svi.csv`, `data/watersheds.geojson`
- **How to run:**
  ```r
  Rscript code/social_vulnerability_join.R
  ```
- **Outputs:** `outputs/svi_watershed_scores.csv`

## Contributing
- Commit code with informative messages so teammates can follow your progress.
- Reference this page from the homepage when new workflows are ready for review.
- Open an issue if a script requires environment changes or additional data agreements.
