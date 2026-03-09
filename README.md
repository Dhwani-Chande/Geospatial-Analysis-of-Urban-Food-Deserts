# Geospatial Analysis of Urban Food Deserts

A graduate-level data science project analyzing food deserts in Chicago using USDA Food Access Atlas, SNAP participation, ACS broadband adoption, and City of Chicago grocery locations. We test five hypotheses on spatial clustering, affordability, income disparity, and digital access, producing geospatial visuals, ML models, and a Digital Barrier Index.


## Hypothesis

1. Food deserts cluster in specific geographic areas.
2. Delivery services improve food access but may not address affordability barriers for low-income populations.
3. Income disparity and food access are linked in Chicago, with widening gaps.
4. Broadband adoption gaps—not service availability—are the primary digital food access barrier in urban food deserts (amplified by poverty and elderly populations).
5. Higher digital access barriers are more likely to be food deserts.


## Repository structure

- `CS418_Fall2025_Report.tex` — final report (compile instructions inside). Generates `references.bib` via `filecontents*`.
- `figs/` — export all notebook figures here (see list below).
- `Folder/` — notebooks and raw assets
  - `H1.ipynb` (Nishita)
  - `H2.ipynb` (Anand)
  - `H3.ipynb` (Krishna)
  - `H4.ipynb` (Kaushik)
  - `H5.ipynb` (Dhwani)
  - `Grocery store.csv`
  - `tl_2020_17_tract.shp` (+ .dbf/.shx/.prj)
  - `progressreport.txt`
- *(If available)* `data/` and `data_cleaning/` for cleaned merges and scripts.


## Data sources (external)

- USDA Food Access Research Atlas 2015 & 2019 (tract-level demographics, poverty, access flags).
- City of Chicago Grocery Store Status Map (operational grocery locations).
- SNAP administrative data (Jan 2015, Jan 2019, Jan 2025) — Cook County aggregates.
- ACS 2019 5-year, table B28002 (broadband subscription) via Census API key.
- TIGER/Line 2020 tract shapefiles for Illinois (FIPS 17).


## Environment

- Python 3.10+
- Key packages: `pandas numpy matplotlib seaborn geopandas folium plotly scikit-learn statsmodels imbalanced-learn shapely requests`.
- Windows cmd quick setup:

  ```cmd
  py -3 -m venv .venv
  .venv\Scripts\activate
  pip install -U pip
  pip install pandas numpy matplotlib seaborn geopandas folium plotly scikit-learn statsmodels imbalanced-learn shapely requests
  ```


## Reproducing notebooks

1. Place raw data in `Folder/` (Food Access Atlas 2015/2019, SNAP Excel files, ACS API key, shapefiles, Grocery store CSV).
2. Open each notebook (H1–H5) and run all cells in order. For ACS, set `API_KEY` where required (H4, H5).
3. Export figures to `figs/` with these names (as referenced in the report):

   - Nishita: `nishita_fig1_heatmaps.png`, `nishita_fig2_income_poverty.png`, `nishita_fig3_clusters.png`
   - Anand: `anand_fig1_affordability_scatter.png`, `anand_fig2_corr_heatmap.png`, `anand_fig3_model_roc.png`
   - Krishna: `krishna_fig1_income_change.png`, `krishna_fig2_ml_comparison.png`, `krishna_fig3_regression.png`
   - Kaushik: `kaushik_fig1_broadband_map.png`, `kaushik_fig2_logit_odds.png`, `kaushik_fig3_senior_urban.png`
   - Dhwani: `dhwani_fig1_corr_heatmap.png`, `dhwani_fig2_barrier_components.png`, `dhwani_fig3_pr_curve.png`

  (If you prefer the `h1-*.png` exports already present, update the LaTeX figure paths accordingly.)



On Overleaf: upload `CS418_Fall2025_Report.tex`, ensure `figs/` is present with exported PNGs; `references.bib` is auto-created by the filecontents block on first compile.


## Key outputs

- LaTeX report with required CS418 sections and hypothesis tests.
- 15+ figures (>=3 per member) covering geospatial maps, affordability plots, clustering, ROC/PR curves, regression fits, and interaction effects.
- Digital Barrier Index (composite deliverable) and threshold tuning for imbalanced classification.


## Reproducibility checklist (quick)

- Activate virtual environment; install listed packages.
- Ensure Census API key is set for broadband pulls (H4/H5).
- Verify data files exist: Food Access Atlas 2015/2019, SNAP Jan 2015/2019/2025, Grocery store CSV, TIGER/Line shapefiles.
- Run notebooks H1→H5; export figures to `figs/` with names above.


## Contacts / Members

- Nishita — H1 (spatial clustering)
- Anand — H2 (affordability models)
- Krishna — H3 (income change, ML/regression)
- Kaushik — H4 (broadband adoption, logit)
- Dhwani — H5 (Digital Barrier Index, SMOTE models)


