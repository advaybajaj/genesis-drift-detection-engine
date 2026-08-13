# Understanding the Poleward Migration of Tropical Cyclones

Final project for ENVS 0070G, Brown University. Investigates whether tropical
cyclone genesis and track locations have shifted poleward since 1980 in the
North Atlantic and Western North Pacific basins, and what climatic drivers
(sea surface temperature, vertical wind shear) explain the trend.

**Main hypothesis:** tropical cyclone genesis and track locations have
undergone a statistically significant poleward shift over recent decades.

Read the full paper in [`paper/`](paper/).

## Repo structure

- **`paper/`** — the final write-up (`.docx` and `.pdf`).
- **`code/`** — the three analysis notebooks:
  - `raw_cyclone_data_analysis.ipynb` — IBTrACS track processing; genesis/max-intensity
    latitude trends, coastline proximity, basin comparison (Figures 1, 5, 6).
  - `analysis_with_sst_and_vws.ipynb` — ERA5 sea-surface temperature and vertical
    wind shear analysis at genesis locations (Figures 3, 4).
  - `tree_ring_data_analysis.ipynb` — tree-ring canopy disturbance proxy analysis
    (Figure 2).
- **`data/`** — `ibtracs_storms_summary.csv`, the subset of NOAA's IBTrACS v4
  best-track data used for the storm-track analysis. (ERA5 SST/VWS, the Natural
  Earth coastline shapefile, and the Altman et al. 2018 tree-ring dataset are
  pulled from their original sources in the notebooks rather than stored here.)
- **`figures/`** — final figures as they appear in the paper, one folder per
  figure:
  - `figure1_poleward_migration_trends/` — genesis latitude, max-intensity
    latitude, coastline proximity, and combined trend (panels A–D).
  - `figure2_tree_ring_canopy_disturbance/` — canopy disturbance proportion by
    latitude for three age classes (panels A–C).
  - `figure3_sst_and_genesis/` — genesis latitude in warm vs. cool SST years,
    and the SST time series at genesis (panels A–B).
  - `figure4_wind_shear_and_genesis/` — genesis latitude vs. wind shear, and
    the wind shear time series at genesis (panels A–B).
  - `figure5_basin_comparison/` — KDE and year-over-year genesis latitude by
    basin (panels A–B).
  - `figure6_coastline_proximity_heatmaps/` — 1980–1999 vs. 2000–2024 track
    density heatmaps (panels A–B), plus a video comparison of the two.
- **`reference/`** — supporting, non-final material:
  - `altman_2018_source_figures/` — the published Altman et al. (2018) figure
    panels used to manually reconstruct the tree-ring canopy disturbance
    dataset (digitized via x-step interpolation, per the Methods section).
  - `exploratory_charts/` — earlier combined draft charts exploring latitude
    vs. VWS vs. SST together, superseded by the separate Figures 3 and 4 in
    the final paper. Kept for reference, not part of the paper's figure set.

## Datasets used (per the paper)

| Dataset | Time span | Source | Purpose |
|---|---|---|---|
| IBTrACS v4 Global TC Best Track | 1980–present | NOAA | TC tracks, genesis points, intensity |
| ERA5 Hourly Data on Pressure Levels | 1980–present | ECMWF | Vertical wind shear |
| ERA5 Hourly Data on Single Levels | 1980–present | ECMWF | Sea surface temperature |
| Admin 1: 50m Coastline Dataset | N/A | Natural Earth | Coastline mapping / proximity |
| Tree-ring canopy disturbance data | >50 yrs BP | Altman et al. (2018) | Proxy for historical TC activity |

## Publishing to GitHub

```bash
cd "genesis-drift-detection-engine"
git init
git add .
git commit -m "Initial commit: tropical cyclone poleward migration analysis"
# then create a repo on GitHub and push
```

Note: `data/ibtracs_storms_summary.csv` (~1 MB) and
`figures/figure6_coastline_proximity_heatmaps/genesis_heatmap_comparison.mov`
(~27 MB) are the two largest files. If repo size is a concern, consider
Git LFS for the video or excluding it via `.gitignore`.
