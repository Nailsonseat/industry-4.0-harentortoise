# CUSTOMER360 — Intelligent Retention Analytics
<sup>Industry 4.0 · Customer analytics · Churn & retention</sup>

[![Python](https://img.shields.io/badge/python-3.8%2B-blue.svg)](https://www.python.org/)
[![Notebooks](https://img.shields.io/badge/jupyter-notebooks-orange.svg)](https://jupyter.org/)
[![License](https://img.shields.io/badge/license-None-lightgrey.svg)](#license--contributions)

**Prepared:** September 2025  
**Authors:** Shubham Sharma · Aadarsh Verma · Areeba Farooqui · Amisha Mishra · Shruti Mishra

---

Quick summary
---------------
- Purpose: Intelligent customer retention using segmentation, churn prediction, and market-basket analysis.
- Dataset: Telco Customer Churn (Kaggle) — included at `data/WA_Fn-UseC_-Telco-Customer-Churn.csv`.
- Notebooks: EDA, churn prediction, customer segmentation, market-basket analysis.

Table of contents
------------------
- [Project overview](#project-overview)
- [Key statistics](#key-statistics)
- [Methodology (summary)](#methodology-summary)
- [Key results & recommendations](#key-results--recommendations)
- [How to reproduce](#how-to-reproduce-quick)
- [Artifacts & files](#artifacts--files)
- [Limitations & next steps](#limitations--next-steps)
- [License & contributions](#license--contributions)

---

Project overview
----------------
This workspace (Customer360) demonstrates an Industry 4.0–oriented customer analytics workflow focused on "Intelligent Retention": segmentation, churn prediction, and market-basket analysis. It combines exploratory data analysis (EDA), clustering (K-Means), several supervised classifiers (Logistic Regression, Random Forest, XGBoost, KNN, SVM), ensemble models, and association-rule mining (Apriori) to produce actionable retention strategies.

Key statistics
--------------

| Item | Value |
|---|---:|
| Dataset | `data/WA_Fn-UseC_-Telco-Customer-Churn.csv` |
| Records | 7,043 |
| Target | `Churn` (binary) |
| Typical features | demographics, tenure, contract, monthly/total charges, service flags (StreamingTV, StreamingMovies, DeviceProtection, TechSupport, etc.) |
| Main notebooks | `exploratory_data_analysis.ipynb`, `churn_prediction.ipynb`, `customer_segmentation.ipynb`, `market_basket_analysis.ipynb` |

Methodology (summary)
---------------------
<details>
<summary>Click to expand methodology</summary>

- EDA: cleaning, missing-value handling, distribution checks, correlation analysis, visualisations.
- Segmentation: K-Means clustering on tenure and spend/service adoption to identify customer groups (e.g., Very New, Low, Medium-High, High spenders).
- Churn prediction: train/evaluate Logistic Regression, Random Forest, XGBoost, KNN, SVM; use cross-validation and ensemble (Voting Classifier) to produce calibrated churn scores.
- Market-basket analysis: Apriori / association-rule mining to find frequently co-subscribed services and bundle candidates.

</details>

Key results & recommendations
----------------------------
- Segmentation: Most customers are Medium-High and High spenders — a good mid-tier revenue opportunity. Only ~18.9% are long-term.
- Churn model: Voting Classifier AUC ≈ 0.839; top financial drivers: TotalCharges, Tenure, MonthlyCharges.
- Contracts: long-term contract customers churn less than month-to-month users — target contract upgrades.
- Service insights: OnlineSecurity and TechSupport reduce churn moderately; Streaming Movies and Streaming TV co-occur strongly — bundle them.

Business recommendations
------------------------
- Launch loyalty / tenure-based rewards for long-term, high-value customers.
- Offer onboarding bundles and targeted communication for Low and Very New segments.
- Promote Streaming bundles and combo packages (Device Protection + Tech Support + Online Backup).
- Simplify payment flows and promote secure alternatives to reduce churn tied to payment method.

How to reproduce (quick)
------------------------
Open this workspace in VS Code or Jupyter and follow the steps below.

1. Create and activate a Python virtual environment (PowerShell):

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

2. Install dependencies:

```powershell
pip install --upgrade pip
pip install -r requirements.txt
```

3. Recommended run order (iterative interactive runs):
- `exploratory_data_analysis.ipynb` (cleaning & EDA)
- `customer_segmentation.ipynb` (clustering & exports)
- `churn_prediction.ipynb` (model training & evaluation)
- `market_basket_analysis.ipynb` (association rules)

Tip: run notebooks sequentially and inspect export folders afterwards. Use seeds (numpy/scikit-learn) for deterministic clustering/modeling.

Artifacts & files
-----------------

```
.
├─ churn_prediction.ipynb
├─ customer_segmentation.ipynb
├─ exploratory_data_analysis.ipynb
├─ market_basket_analysis.ipynb
├─ requirements.txt
├─ data/
│  └─ WA_Fn-UseC_-Telco-Customer-Churn.csv
├─ cluster_notebook_exports/
│  ├─ clustered_customers.csv
│  └─ clustered_customers_tenure.csv
└─ market_basket_exports/
   └─ association_rules.csv
```

Contributors
------------

| Name | Email |
|---|---|
| Shubham Sharma | 21f2000041@ds.study.iitm.ac.in |
| Aadarsh Verma | 22f1001596@ds.study.iitm.ac.in |
| Areeba Farooqui | 22f1001053@ds.study.iitm.ac.in |
| Amisha Mishra | 22f1000938@ds.study.iitm.ac.in |
| Shruti Mishra | 21f3001234@ds.study.iitm.ac.in |

Limitations & next steps
------------------------
- Static dataset: no real-time telemetry — consider adding event streams for early signals.
- Class imbalance & correlated features: use resampling, class weighting, SHAP/LIME for interpretation.

Possible next steps:
- Create a reproducible pipeline (scripts + CI) to run notebooks non-interactively (nbconvert or papermill).
- Add model tracking (MLflow) and an inference API for scored churn probabilities.
- Add simple unit tests or data-validation checks (pandera / great_expectations).

License & contributions
-----------------------
This repository currently has no explicit license. If you plan to reuse or publish this work, add a `LICENSE` file (e.g., MIT). Contributions welcome via forks and pull requests.

Contact
-------
For questions about the notebooks, reproducibility, or pipeline conversion, contact the contributors listed above.