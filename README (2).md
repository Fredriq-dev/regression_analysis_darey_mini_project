# Marketing Sales Regression Analysis

A Simple Linear Regression project that models the relationship between marketing channel spend (TV, Radio, Social Media) and Sales revenue. The analysis identifies the strongest ROI driver across channels and produces a data-backed budget allocation recommendation.

---

## Project Overview

| Item | Detail |
|---|---|
| Dataset | `marketing_and_sales_data_evaluate_lr.csv` |
| Rows | 4,571 |
| Target variable | Sales |
| Predictors | TV, Radio, Social Media |
| Model | Ordinary Least Squares (OLS) via statsmodels |
| Best predictor | TV (r = 0.9995, R² = 0.999) |

### What the notebook does

1. **Load & explore** — reads the dataset, inspects shape, dtypes, and summary statistics
2. **Handle missing values** — fills nulls in each column using median imputation
3. **EDA** — scatter plots for each channel vs Sales and a correlation matrix to justify variable selection
4. **Variable selection** — identifies TV as the strongest predictor based on correlation with Sales
5. **OLS model** — fits a Simple Linear Regression using `statsmodels` and prints the full statistical summary
6. **Diagnostic plots** — Residuals vs Fitted, Q-Q plot, and Scale-Location plot to verify model assumptions
7. **Model interpretation** — extracts R², intercept, coefficient, and p-value with plain-English commentary
8. **ROI comparison** — runs OLS on all three channels and ranks them by R² and sales lift per spend unit

### Key finding

> TV advertising is the dominant driver of Sales. Every 1-unit increase in TV spend is associated with approximately **3.56 units of incremental Sales**. The model explains **99.9% of Sales variation** (R² = 0.999).

**Recommended budget allocation:**
- TV → 70–80%
- Radio → 15–20%
- Social Media → 5–10%

---

## Project Structure

```
├── regression_analysis.ipynb                     # Main analysis notebook
├── marketing_and_sales_data_evaluate_lr.csv      # Dataset
├── scatter_plots.png                             # EDA scatter plots (generated)
├── diagnostics.png                               # Regression diagnostic plots (generated)
└── README.md                                     # This file
```

---

## Environment Setup

### Requirements

- Python 3.8+
- Jupyter Notebook or JupyterLab

### Install dependencies

Run the following command in your terminal to install all required libraries:

```bash
pip install pandas numpy matplotlib seaborn statsmodels scipy scikit-learn
```

Or install them one by one:

```bash
pip install pandas        # data loading and manipulation
pip install numpy         # numerical operations
pip install matplotlib    # plotting
pip install seaborn       # statistical visualisations
pip install statsmodels   # OLS regression and statistical summaries
pip install scipy         # Q-Q plot and statistical tests
pip install scikit-learn  # LinearRegression (ROI comparison section)
```

### Run the notebook

```bash
# Clone or download the project files, then:
jupyter notebook regression_analysis.ipynb

# Or with JupyterLab:
jupyter lab regression_analysis.ipynb
```

Once open, run all cells in order via **Kernel → Restart & Run All**.

---

## Libraries Used

| Library | Version | Purpose |
|---|---|---|
| pandas | ≥ 1.3 | Data loading, cleaning, manipulation |
| numpy | ≥ 1.21 | Numerical computation |
| matplotlib | ≥ 3.4 | Base plotting |
| seaborn | ≥ 0.11 | Scatter plots and heatmaps |
| statsmodels | ≥ 0.13 | OLS regression and model summary |
| scipy | ≥ 1.7 | Normality testing (Q-Q plot) |
| scikit-learn | ≥ 0.24 | LinearRegression utility |

---

## Regression Assumptions Tested

| Assumption | Diagnostic plot | What to look for |
|---|---|---|
| Linearity | Residuals vs Fitted | Random scatter around zero — no curve |
| Normality | Q-Q plot | Points closely following the diagonal line |
| Homoscedasticity | Scale-Location | Flat, even spread of residuals across fitted values |

---

## Notes

- Missing values are filled using **median imputation** per column rather than row deletion, preserving the full dataset size.
- The constant (intercept) is added manually via `sm.add_constant()` as statsmodels requires explicit intercept specification.
- All plots are saved as `.png` files in the project root directory when the notebook is run.
