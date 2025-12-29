This repository contains the code, data workflows, and visualisations for my PP434 project:

# High Income → High Human Development?
## Structural Prerequisites for India’s Vision 2047

This project examines whether economic growth alone is sufficient to deliver high human development in India, or whether deeper structural and institutional factors shape states’ ability to convert income into human development outcomes.

---

## Project Motivation

India’s Vision 2047 agenda aims to achieve high-income status alongside high human development. While income growth has accelerated since the early 2000s, progress in health and education outcomes has been more uneven across states.

This project asks three linked questions:

1. How has India’s national and state-level HDI evolved alongside income growth since 1990?
2. Do Indian states differ systematically in their ability to convert income into human development?
3. Which structural factors—fiscal effort, state capacity, labour markets, or social structure—help explain these differences?

---

## Data Sources

- **National HDI (1990–2023):** UNDP Human Development Reports Office (HDRO)  
- **State HDI (1990–2023):** Global Data Lab, Radboud University  
- **Income:** Log GNI per capita (2021 PPP$)  
- **Social Sector Spending:** RBI *State Finances: A Study of Budgets* (per capita)  
- **State Capacity Proxies:**
  - NITI Aayog Health Index (2021, Inputs & Processes domain)
  - NITI Aayog School Education Quality Index (2019, Governance & Processes domain)
- **Labour Market:** Worker–Population Ratio (PLFS 2022–23)  
- **Social Structure:** SC/ST population shares (Census of India 2011)

Due to non-aligned years across sources, capacity indices are treated as slow-moving structural proxies suitable for cross-state comparison.

---

## Methodology

All data processing and analysis are conducted in Python, using:

- `pandas`, `numpy` for data cleaning and merging  
- `statsmodels` for regression inference  
- `scikit-learn` for standardisation and residual construction  
- `Vega-Lite` for interactive visualisations (embedded via HTML/JS)

### Key analytical steps

1. **Data restructuring**
   - Long-to-wide transformation of HDI and component indicators
   - Construction of tidy time-series and cross-sectional datasets

2. **Income–HDI relationship**
   - Cross-sectional regression of HDI on log GNI per capita
   - High explanatory power (R² ≈ 0.85), confirming income as a necessary but insufficient condition

3. **Residual HDI (“conversion efficiency”)**
   - Residuals from income–HDI regressions used to rank states by income-adjusted performance

4. **Structural correlates of residual HDI**
   - Social sector spending
   - State capacity proxies (health and education indices)
   - Worker–population ratio
   - Social structure (SC/ST population shares)

All independent variables are standardised (z-scores) to enable coefficient comparability.

---

## Visualisations

The project includes eight interactive Vega-Lite charts covering:

1. National HDI trends (1990–2023)  
2. State HDI trajectories over time  
3. Income–HDI gradients  
4. Income-adjusted HDI residual rankings  
5. Social sector spending vs residual HDI  
6. State capacity indices vs residual HDI  
7. Workforce participation vs residual HDI  
8. Social structure and residual HDI  

Charts 3–8 are linked to reproducible Google Colab notebooks.

---

## Repository Structure

```text
project/
│
├── data/
│   └── processed/              # Cleaned and merged datasets
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
├── README.md

---

## Limitations

- All analyses are cross-sectional and descriptive; no causal claims are made.  
- Endogeneity may remain despite residualisation.  
- Capacity indices may capture formal inputs and compliance rather than implementation quality.  
- Social structure data relies on Census 2011 due to the absence of a more recent census.

---

## Author

**Kumar Rajesh**  
MPP, London School of Economics  
Chevening Scholar
