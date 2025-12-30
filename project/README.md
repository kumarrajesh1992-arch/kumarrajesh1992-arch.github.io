# High Income → High Human Development?
## Structural Prerequisites for India’s Vision 2047

This repository contains the code, data workflows, and visualisations for my PP434 project. It examines whether economic growth alone is sufficient to deliver high human development in India, or whether deeper structural and institutional factors shape states’ ability to convert income into human development outcomes.

---

## Project Motivation

India’s Vision 2047 agenda aims to achieve high-income status alongside high human development. While income growth has accelerated since the early 2000s, progress in health and education outcomes has been more uneven across states.

This project asks three linked questions:
1. **Trends:** How has India’s national and state-level HDI evolved alongside income growth since 1990?
2. **Conversion:** Do Indian states differ systematically in their ability to convert income into human development?
3. **Drivers:** Which structural factors—fiscal effort, spending efficiency, labour markets, or social structure—help explain these differences?

---

## Data Sources

* **National HDI (1990–2023):** UNDP Human Development Reports Office (HDRO)
* **State HDI (1990–2023):** Global Data Lab, Radboud University
* **Income:** Log GNI per capita (2021 PPP$)
* **Social Sector Spending:** RBI *State Finances: A Study of Budgets* (per capita)
* **Technical Efficiency in Expenditure:** Technical efficiency scores for health and education expenditure (2020) were sourced from the World Bank's World Bank 2024 India Economic Memorandum, which estimates state-level spending efficiency (see page 130-131) using a Variable Returns to Scale Data Envelopment Analysis model.
* **Labour Market:** Worker–Population Ratio (PLFS 2022–23)
* **Social Structure:** SC/ST population shares (Census of India 2011)

---

## Methodology

All data processing and analysis are conducted in Python, using:
* `pandas`, `numpy` for data cleaning and merging
* `statsmodels` for regression inference
* `scikit-learn` for standardisation and residual construction
* `Vega-Lite` for interactive visualisations (embedded via HTML/JS)

### Key Analytical Steps

1.  **Data Restructuring**
    * Long-to-wide transformation of HDI and component indicators.
    * Construction of tidy time-series and cross-sectional datasets.

2.  **Income–HDI Relationship**
    * Cross-sectional regression of HDI on log GNI per capita.
    * High explanatory power ($R^2 \approx 0.85$), confirming income as a necessary but insufficient condition.

3.  **Residual HDI (“Conversion Efficiency”)**
    * Residuals from income–HDI regressions used to rank states by income-adjusted performance.

4.  **Structural Correlates of Residual HDI**
    * Analysis of Social sector spending, Spending Efficiency (DEA scores), Worker–population ratio, and Social structure (SC/ST population shares).
    * All independent variables are standardised (z-scores) to enable coefficient comparability.

---

## Visualisations

The project includes eight interactive Vega-Lite charts covering:

1.  National HDI trends (1990–2023)
2.  State HDI trajectories over time
3.  Income–HDI gradients
4.  Income-adjusted HDI residual rankings
5.  Social sector spending vs residual HDI
6.  Social sector spending efficiency vs residual HDI
7.  Workforce participation vs residual HDI
8.  Social structure and residual HDI

*Charts 3–8 are linked to reproducible Google Colab notebooks.*

---

## Repository Structure

```text
project/
│
├── data/                       # Cleaned and merged datasets
│
├── raw_original_data/          # Original source data files
│
├── notebooks/
│   ├── data_cleaning.ipynb
│   ├── income_hdi_model.ipynb
│   └── structural_factors.ipynb
│
├── charts/
│   └── vega_specs/             # Vega-Lite JSON specifications
│
└── README.md
```

## Limitations

* Descriptive Nature: All analyses are cross-sectional and descriptive; no causal claims are made.

* Endogeneity: Endogeneity may remain despite residualisation strategies.

* Data Lag: Social structure data relies on Census 2011 due to the absence of a more recent census.

## Author
Kumar Rajesh, MPP Candidate 2025-26, Chevening Scholar, London School of Economics
