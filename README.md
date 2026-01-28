# Forecasting Global Uncertainty Using UN Security Council Resolution Texts

This repository contains the complete replication code for my seminar paper on uncertainty forecasting using natural language processing of United Nations Security Council resolutions.

## Abstract

I apply Latent Dirichlet Allocation to 2,075 UNSC resolutions (1990Q1-2023Q4) and evaluate whether thematic content improves forecasts of the World Uncertainty Index. The best-performing model reduces out-of-sample forecast error by 11.5% relative to an AR(2) baseline, with the improvement statistically significant across multiple hypothesis tests.

## Data Sources

**World Uncertainty Index (WUI):** Ahir et al. (2022), quarterly data 1990-2023  
**UNSC Resolutions:** Compiled Record of the UN Security Council (CR-UNSC) by Fobbe (2024)  

**Note on large data files:**
The raw data required for replication are too large for GitHub (>100 MB) and are therefore **not** included in this repository.

**Required files:**
- `data/WUI_Data.xlsx`
- `data/CR-UNSC_2024-05-19_ALL_CSV_FULL.csv`

**Data:**
Contact me so I can provide the data. 
Place the files in your local `data/` directory:

All other files in the `data/` directory are generated automatically by the notebooks.

## Repository Structure

```
├── 01_wui_data_processing.ipynb          # WUI data preparation
├── 02_download_unsc_dataset.ipynb        # UNSC resolution download
├── 03_merge_wui_unsc_data.ipynb          # Data integration
├── 04_nlp_topic_modeling.ipynb           # LDA topic modeling (K=6, K=25)
├── 05_topic_wui_correlation_analysis.ipynb # Predictive relationship analysis
├── 06_baseline_forecasting_models_HYBRID.ipynb # Baseline model selection
├── 07_EXHAUSTIVE_TESTING_HYBRID.ipynb    # Cross-validation forecast evaluation
├── 08_statistical_significance_tests_HYBRID.ipynb # Hypothesis testing
├── data/                                 # Processed datasets and trained models
├── results/                              # Cross-validation and test results
└── figures/                              # Visualizations
```

## Reproduction Instructions

**1. Environment Setup**

```bash
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

**2. Execution Order**

Run notebooks sequentially (01 through 08). All intermediate results are saved to `data/` and `results/` directories.

**Note:** Notebooks 01-02 download external data. If replication fails due to data availability, contact me for preprocessed files.

**3. Key Results**

Main findings are generated in:
- Notebook 07: Cross-validation forecast performance
- Notebook 08: Statistical significance tests
- Results stored in `results/summary_k6_ALL_COMBINATIONS.csv` and `results/statistical_tests_k6.csv`

## Main Results

**Best Model:** Topics 2 + 3 + 6 (Peacekeeping, Sanctions, Regional Security)  
**Improvement:** 11.5% RMSE reduction vs. AR(2) baseline  
**Statistical Tests:** 5/5 tests significant (Diebold-Mariano, Sign, Wilcoxon, Bootstrap DM, Clark-West)  
**Robustness:** 9/10 cross-validation folds outperform baseline

## Software Requirements

Python 3.12  
Key packages: pandas, numpy, scipy, statsmodels, gensim, nltk, scikit-learn

See `requirements.txt` for complete dependencies.

## References

Ahir, H., Bloom, N., & Furceri, D. (2022). The World Uncertainty Index. NBER Working Paper No. 29763.

Fobbe, L. (2024). The Corpus of the UN Security Council. Dataset.
