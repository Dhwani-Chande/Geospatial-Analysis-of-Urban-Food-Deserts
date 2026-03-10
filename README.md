<div align="center">

<img src="https://img.shields.io/badge/Chicago-Cook%20County-c8400a?style=flat-square" />
<img src="https://img.shields.io/badge/Tracts%20Analyzed-800%2B-264653?style=flat-square" />
<img src="https://img.shields.io/badge/Best%20AUC-0.871-e9c46a?style=flat-square" />
<img src="https://img.shields.io/badge/Hypotheses-5%20%2F%205%20Supported-2d6a4f?style=flat-square" />

# Geospatial Analysis of Urban Food Deserts

### *Can food delivery apps solve Chicago's food desert crisis?*
### *Or do deeper barriers of income and digital access remain?*

<br/>

[![Live Demo](https://img.shields.io/badge/-%F0%9F%97%BA%EF%B8%8F%20Open%20Live%20D3%20Explorer-c8400a?style=for-the-badge)](https://dhwani-chande.github.io/Geospatial-Analysis-of-Urban-Food-Deserts/)
&nbsp;
[![Report](https://img.shields.io/badge/-📄%20Read%20Full%20Report-264653?style=for-the-badge)](CS418_Fall2025_Final_Project_Report.pdf)
&nbsp;
[![Slides](https://img.shields.io/badge/-📊%20View%20Presentation-2d6a4f?style=for-the-badge)](CS418_Final_Presentation.pdf)

<br/>

> **Conclusion: Delivery is a bridge — not a fix.**  
> Income, digital access, and SNAP reliance are the real determinants of food desert status.  
> Geography alone explains far less than socioeconomic structure.

</div>

---

## What This Project Does

We analyzed **800+ Cook County census tracts** to understand what actually drives food desert status in Chicago. Using USDA food access data, SNAP participation records, ACS broadband adoption statistics, and Chicago grocery locations, we built and tested five hypotheses — using K-Means clustering, ensemble ML models, and a novel Digital Barrier Index (DBI).

Every hypothesis was supported. The pattern is consistent: **the South Side and West Side bear a disproportionate share of food insecurity, and it's not just about distance to a store.**

---

## 🗺️ Live Interactive Visualization

**[→ dhwani-chande.github.io/Geospatial-Analysis-of-Urban-Food-Deserts](https://dhwani-chande.github.io/Geospatial-Analysis-of-Urban-Food-Deserts/)**

Built with D3.js. No install required — runs in any browser.

```
┌─────────────────────────────────┬──────────────────────────────┐
│  CHICAGO TRACT MAP              │  K-MEANS CLUSTER BUBBLES     │
│                                 │                              │
│  800+ dots · 4 view modes:      │  Force-directed layout       │
│  • Cluster coloring             │  Click to filter the map     │
│  • DBI heatmap overlay          │  Arc = food desert rate      │
│  • Food desert isolation        │                              │
│  • Income gradient layer        ├──────────────────────────────┤
│                                 │  INCOME THRESHOLD SLIDER     │
│  Hover → live stats panel       │  Drag to see FD rate change  │
│  (income, poverty, broadband,   ├──────────────────────────────┤
│   SNAP share, DBI score)        │  SNAP TREND 2015→2019→2025   │
│                                 │  Animated bar chart          │
└─────────────────────────────────┴──────────────────────────────┘
```

---

## 📊 Findings at a Glance

| Hypothesis | One-Line Finding | Result |
|---|---|:---:|
| **H1 — Geography** | Food deserts cluster on South & West Side. K=4 optimal. 71% of FD tracts are also low-income. | ✅ |
| **H2 — Delivery & Affordability** | SNAP Intensity (36%) and Median Income (26%) dominate feature importance — not distance. | ✅ |
| **H3 — Income Disparity** | $20,700 gap between FD and non-FD tract incomes. $50k = the tipping point. | ✅ |
| **H4 — Broadband Adoption** | Adoption ranges 56–85% across tracts. Seniors × poverty amplify the gap. AUC 0.82. | ✅ |
| **H5 — Digital Barrier Index** | SMOTE boosted recall from 31% → 71%. DBI composite predicts FD status. AUC 0.825. | ✅ |

<br/>

**Model Performance Summary**

| Model | ROC-AUC | Accuracy | Notes |
|---|---|---|---|
| **Random Forest** | **0.871** | **87.1%** | Best overall · top features: SNAP, Income, Poverty |
| Gradient Boosting | 0.854 | 85.6% | Close second |
| Logistic Regression | 0.812 | 81.4% | Baseline comparison |
| DBI Classifier (H5) | 0.825 | — | After SMOTE · recall 31%→71% |

---

## 🗂️ Repository Structure

```
Geospatial-Analysis-of-Urban-Food-Deserts/
│
├── 📁 docs/
│   └── index.html                   ← D3 visualization · served via GitHub Pages
│
├── 📁 Codes/
│   ├── H1.ipynb                     ← Spatial clustering & K-Means (Nishita)
│   ├── H2.ipynb                     ← Affordability & ML models (Anand)
│   ├── H3.ipynb                     ← Income disparity & regression (Krishna)
│   ├── H4.ipynb                     ← Broadband adoption analysis (Kaushik)
│   └── H5.ipynb                     ← Digital Barrier Index & SMOTE (Dhwani)
│
├── 📁 Datasets/
│   ├── FoodAccessResearchAtlas*.xlsx ← USDA 2015 & 2019 tract data
│   ├── Grocery_Store_Status_Map.csv  ← 264 Chicago grocery locations
│   ├── SNAP_Jan*.xlsx                ← SNAP participation 2015/2019/2025
│   └── tl_2020_17_tract.*            ← TIGER/Line shapefiles (Illinois)
│
├── 📁 figs/                         ← 15+ exported figures (one per notebook section)
│
├── CS418_Fall2025_Final_Project_Report.pdf
├── CS418_Fall2025_Report.tex
├── CS418_Final_Presentation.pdf
├── CS418_ProgressReport_DeliveryAgainstDeserts.pdf
└── CS418_Proposal_Delivery_against_Deserts.pdf
```

---

## 🔬 Data Sources

| Dataset | Provider | Size | Key Variables |
|---|---|---|---|
| Food Access Research Atlas | USDA ERS 2015 & 2019 | 800+ tracts · 147 vars | LowIncomeTracts, LATracts, PovertyRate |
| Grocery Store Status Map | City of Chicago | 264 stores | Coordinates, operating status |
| SNAP Participation | Cook County Admin | Jan 2015 / 2019 / 2025 | Monthly caseloads |
| Broadband Subscriptions | ACS 2019 · Census API (B28002) | Tract-level | B28002_001E, B28002_004E |
| Census Tract Shapefiles | TIGER/Line 2020 · FIPS 17 | Illinois | Tract boundaries for mapping |

---

## ⚙️ Reproducing the Analysis

**Requirements:** Python 3.10+ · Census API key (for H4 & H5)

```bash
# 1. Clone
git clone https://github.com/Dhwani-Chande/Geospatial-Analysis-of-Urban-Food-Deserts.git
cd Geospatial-Analysis-of-Urban-Food-Deserts

# 2. Environment
python -m venv .venv
source .venv/bin/activate       # Mac/Linux
.venv\Scripts\activate          # Windows

# 3. Dependencies
pip install pandas numpy matplotlib seaborn geopandas folium plotly \
            scikit-learn statsmodels imbalanced-learn shapely requests

# 4. Census API key — set inside H4.ipynb and H5.ipynb
#    Get one free at: https://api.census.gov/data/key_signup.html

# 5. Run in order
jupyter notebook Codes/H1.ipynb   # → Codes/H2 → H3 → H4 → H5
```

**Figure exports** — each notebook exports to `figs/` using these names:

```
nishita_fig1_heatmaps.png         nishita_fig2_income_poverty.png      nishita_fig3_clusters.png
anand_fig1_affordability_scatter  anand_fig2_corr_heatmap.png          anand_fig3_model_roc.png
krishna_fig1_income_change.png    krishna_fig2_ml_comparison.png       krishna_fig3_regression.png
kaushik_fig1_broadband_map.png    kaushik_fig2_logit_odds.png          kaushik_fig3_senior_urban.png
dhwani_fig1_corr_heatmap.png      dhwani_fig2_barrier_components.png   dhwani_fig3_pr_curve.png
```

---

## 👥 Team

| Member | Notebook | Role |
|---|---|---|
| Nishita | H1 | Spatial clustering · K-Means · geographic heatmaps · 6-test statistical battery |
| Anand | H2 | Affordability analysis · Random Forest · feature importance ranking |
| Krishna | H3 | Income change over time · ML comparison · regression modeling |
| Kaushik | H4 | Broadband adoption mapping · logistic regression · senior × poverty interaction |
| **Dhwani** | **H5** | **Digital Barrier Index · SMOTE oversampling · ensemble classification** |

---

## 📄 Citation

```bibtex
@misc{chande2025geospatial,
  title  = {Geospatial Analysis of Urban Food Deserts},
  author = {Chande, Dhwani and Nishita and Anand and Krishna and Kaushik},
  year   = {2025},
  note   = {CS418 Data Science, Fall 2025},
  url    = {https://github.com/Dhwani-Chande/Geospatial-Analysis-of-Urban-Food-Deserts}
}
```

---

<div align="center">
<sub>
Built with Python · D3.js · scikit-learn · GeoPandas · imbalanced-learn · CS418 Fall 2025
</sub>
</div>
