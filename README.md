# 🍎 Food Delivery as a Tool Against Food Deserts

[![Live Demo](https://img.shields.io/badge/Live%20Demo-D3%20Explorer-c8400a?style=for-the-badge&logo=github)](https://dhwani-chande.github.io/Food-Delivery-as-a-Tool-Against-Food-Deserts)
[![CS418](https://img.shields.io/badge/Course-CS418%20Data%20Science-264653?style=for-the-badge)](https://github.com/Dhwani-Chande/Food-Delivery-as-a-Tool-Against-Food-Deserts)
[![Python](https://img.shields.io/badge/Python-3.10+-e9c46a?style=for-the-badge&logo=python&logoColor=black)](https://python.org)
[![License](https://img.shields.io/badge/License-Academic-2d6a4f?style=for-the-badge)](LICENSE)

> **Can food delivery apps solve Chicago's food desert crisis — or do deeper barriers of income and digital access remain?**

A graduate-level data science project analyzing **800+ Cook County census tracts** using USDA Food Access Research Atlas, SNAP participation data, ACS broadband adoption, and Chicago grocery store locations. We test five hypotheses on spatial clustering, affordability, income disparity, and digital access — concluding that delivery is a bridge, not a fix.

---

## 🗺️ Interactive D3 Visualization

**[→ Open Live Explorer](https://dhwani-chande.github.io/Food-Delivery-as-a-Tool-Against-Food-Deserts)**

The interactive dashboard features:
- **Chicago tract map** — 800+ census tracts colored by K-Means cluster, food desert status, DBI heatmap, or income layer
- **Force bubble chart** — K-Means K=4 clusters with food desert rate arcs, clickable to filter the map
- **Income threshold slider** — drag to see how food desert rate changes across income levels
- **SNAP trend chart** — participation trends 2015 → 2019 → 2025
- **Live info panel** — hover any tract to see income, poverty rate, broadband, SNAP share, and DBI score

---

## 📊 Key Findings

| Hypothesis | Result | Key Stat |
|---|---|---|
| H1 — Food deserts cluster geographically | ✅ Supported | 71% of FD tracts also low-income; K=4 optimal |
| H2 — Delivery improves access but not affordability | ✅ Supported | SNAP Intensity = 36% feature importance |
| H3 — Income disparity widening | ✅ Supported | $20,700 gap; $50k income = tipping point |
| H4 — Broadband adoption gap (not availability) is barrier | ✅ Supported | 56–85% range; AUC 0.82+ |
| H5 — Digital Barrier Index predicts food deserts | ✅ Supported | SMOTE recall 31%→71%; AUC 0.825 |

**Best model:** Random Forest — ROC-AUC **0.871**, Accuracy **87.1%**

---

## 🗂️ Repository Structure

```
├── docs/
│   └── index.html              ← Live D3 visualization (GitHub Pages)
│
├── Codes/
│   ├── H1.ipynb                ← Spatial clustering (Nishita)
│   ├── H2.ipynb                ← Affordability models (Anand)
│   ├── H3.ipynb                ← Income disparity + ML (Krishna)
│   ├── H4.ipynb                ← Broadband adoption (Kaushik)
│   └── H5.ipynb                ← Digital Barrier Index (Dhwani)
│
├── Datasets/                   ← Raw data (see sources below)
├── figs/                       ← Exported notebook figures
│
├── CS418_Fall2025_Final_Project_Report.pdf
├── CS418_Fall2025_Report.tex
├── CS418_Final_Presentation.pdf
└── README.md
```

---

## 🔬 Methods

**Data Sources**
- USDA Food Access Research Atlas 2015 & 2019 (800+ Cook County tracts, 147 variables)
- City of Chicago Grocery Store Status Map (264 store locations)
- SNAP administrative data — Jan 2015, 2019, 2025
- ACS 2019 5-year broadband estimates (Census API, table B28002)
- TIGER/Line 2020 tract shapefiles for Illinois

**Techniques Used**
- K-Means clustering (K=4, elbow method confirmed)
- Random Forest, Logistic Regression, Gradient Boosting (ROC-AUC comparison)
- SMOTE oversampling for 3.9% class imbalance (recall 31% → 71%)
- Mann-Whitney U, chi-square, 6-test spatial statistical battery
- Digital Barrier Index: composite z-score of −broadband + seniors + SNAP + no-vehicle

---

## ⚙️ Setup & Reproduction

```bash
# 1. Clone the repo
git clone https://github.com/Dhwani-Chande/Food-Delivery-as-a-Tool-Against-Food-Deserts.git
cd Food-Delivery-as-a-Tool-Against-Food-Deserts

# 2. Create virtual environment
python -m venv .venv
source .venv/bin/activate          # Mac/Linux
# .venv\Scripts\activate           # Windows

# 3. Install dependencies
pip install pandas numpy matplotlib seaborn geopandas folium plotly \
            scikit-learn statsmodels imbalanced-learn shapely requests

# 4. Add your Census API key (needed for H4, H5)
# Set API_KEY variable inside H4.ipynb and H5.ipynb

# 5. Run notebooks in order: H1 → H2 → H3 → H4 → H5
# Export figures to figs/ with names listed below
```

**Required figure exports** (for LaTeX report compilation):
```
figs/
├── nishita_fig1_heatmaps.png       nishita_fig2_income_poverty.png    nishita_fig3_clusters.png
├── anand_fig1_affordability_scatter.png  anand_fig2_corr_heatmap.png  anand_fig3_model_roc.png
├── krishna_fig1_income_change.png  krishna_fig2_ml_comparison.png     krishna_fig3_regression.png
├── kaushik_fig1_broadband_map.png  kaushik_fig2_logit_odds.png        kaushik_fig3_senior_urban.png
└── dhwani_fig1_corr_heatmap.png    dhwani_fig2_barrier_components.png dhwani_fig3_pr_curve.png
```

---

## 👥 Team

| Member | Hypothesis | Focus |
|---|---|---|
| Nishita | H1 | Spatial clustering, K-Means, geographic heatmaps |
| Anand | H2 | Affordability models, ML feature importance |
| Krishna | H3 | Income change over time, regression |
| Kaushik | H4 | Broadband adoption, logistic regression |
| **Dhwani** | **H5** | **Digital Barrier Index, SMOTE, ensemble models** |

---

## 📄 Citation

```bibtex
@misc{chande2025fooddesert,
  title   = {Food Delivery as a Tool Against Food Deserts},
  author  = {Chande, Dhwani and others},
  year    = {2025},
  school  = {CS418 Data Science, Fall 2025},
  url     = {https://github.com/Dhwani-Chande/Food-Delivery-as-a-Tool-Against-Food-Deserts}
}
```

---

<p align="center">
  <sub>Built with Python · D3.js · scikit-learn · GeoPandas · CS418 Fall 2025</sub>
</p>
