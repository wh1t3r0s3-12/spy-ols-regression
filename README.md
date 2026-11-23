# SPY Return Modeling via Multiple OLS Regression

> Multiple Ordinary Least Squares (OLS) linear regression modeling of SPY daily returns using financial assets and interest rate indicators, with full econometric diagnostics.

## Objective

Model and explain the daily return of the SPY (SPDR S&P 500 ETF Trust) using a multiple linear regression framework based on the returns of financial and macroeconomic indicators (Apple stock `AAPL`, `USD/CNY` exchange rate, short-term interest rates, gold price, etc.) over the 2000–2004 period, and validate the robustness of the model through a comprehensive suite of econometric diagnostic tests.

## Project Structure

```text
spy-ols-regression/
├── data/                                                    # Raw dataset files (CSV / XLS)
├── docs/
│   ├── report.docx                                          # Original econometric study report
│   └── white_paper.pdf                                      # Academic research white paper (PDF)
├── notebooks/
│   ├── 01_data_preparation_and_modeling/
│   │   └── 01_data_preparation_and_ols_regression.ipynb     # Data loading, cleaning, merging, and OLS estimation
│   ├── 02_hypothesis_validation/
│   │   ├── 01_linearity_and_homoscedasticity.ipynb          # Rainbow test and studentized residuals vs. fitted values
│   │   ├── 02_residuals_normality.ipynb                     # Histogram and Q-Q plots of studentized residuals
│   │   └── 03_multicollinearity_vif.ipynb                   # Variance Inflation Factor (VIF) analysis
│   └── 03_diagnostics_and_forecasting/
│       ├── 01_leverage_and_influence_diagnostics.ipynb      # Combined diagnostic plot (leverage, residuals, Cook's D)
│       ├── 02_outliers_and_spy_forecasting.ipynb            # Outlier detection and actual vs. predicted SPY returns
│       └── 03_cooks_distance.ipynb                          # Influential observations analysis (Cook's distance)
├── README.md
└── requirements.txt
```

## Data

The [`data/`](data/) folder contains the historical time series used to build the model:

| File | Description |
|---|---|
| `Données SPY.csv` | SPY ETF price series (dependent variable) |
| `AAPL.csv` | Apple Inc. stock price |
| `USD_CNY.csv` | USD/CNY exchange rate |
| `Gold.csv` | Gold price |
| `HIS.csv`, `DTB6.csv`, `TCD6.csv`, `DR5.xls`, `Taux_ST6.xls`, `VRV.xls` | Short/medium-term interest rates, Hang Seng index, term spread, and volume indicators |

## Methodology

The notebooks in [`notebooks/`](notebooks/) are organized into three main stages:

1. **Data Preparation and Modeling ([`01_data_preparation_and_modeling/`](notebooks/01_data_preparation_and_modeling/))**:
   - [`01_data_preparation_and_ols_regression.ipynb`](notebooks/01_data_preparation_and_modeling/01_data_preparation_and_ols_regression.ipynb): column standardization, date parsing, daily return computation, time-series merging on dates, missing value imputation, and multiple OLS regression.
2. **Hypothesis Validation ([`02_hypothesis_validation/`](notebooks/02_hypothesis_validation/))**:
   - [`01_linearity_and_homoscedasticity.ipynb`](notebooks/02_hypothesis_validation/01_linearity_and_homoscedasticity.ipynb): Rainbow linearity test and scatter plots of studentized residuals against fitted values (linearity and homoscedasticity checks).
   - [`02_residuals_normality.ipynb`](notebooks/02_hypothesis_validation/02_residuals_normality.ipynb): histogram and normal/Student-t Q-Q plots of studentized residuals.
   - [`03_multicollinearity_vif.ipynb`](notebooks/02_hypothesis_validation/03_multicollinearity_vif.ipynb): Variance Inflation Factor (VIF) computation across all explanatory variables.
3. **Diagnostics and Forecasting ([`03_diagnostics_and_forecasting/`](notebooks/03_diagnostics_and_forecasting/))**:
   - [`01_leverage_and_influence_diagnostics.ipynb`](notebooks/03_diagnostics_and_forecasting/01_leverage_and_influence_diagnostics.ipynb): joint classification of observations by external studentized residuals, leverage (`hat_diag`), and Cook's distance.
   - [`02_outliers_and_spy_forecasting.ipynb`](notebooks/03_diagnostics_and_forecasting/02_outliers_and_spy_forecasting.ipynb): outlier detection ($\lvert\text{studentized residual}\rvert > 3$) and comparison of actual vs. OLS-predicted SPY returns (2000–2004).
   - [`03_cooks_distance.ipynb`](notebooks/03_diagnostics_and_forecasting/03_cooks_distance.ipynb): detection of influential points using Cook's distance threshold ($4/n$).

The full study documentation is available in [`docs/white_paper.pdf`](docs/white_paper.pdf) (research white paper) and [`docs/report.docx`](docs/report.docx).