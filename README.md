# Retail Sales Forecasting for Inventory and Demand Planning Using Time-Series and Machine Learning

---

## Project Overview

Retail inventory management and supply chain optimization heavily rely on accurate demand forecasting. This research project investigates multi-department retail dynamics utilizing **152,000+ transactional records**. By formulating four core Research Questions (RQs), this study bridges traditional econometric time-series models (**ARIMA**, **SARIMA**, **Prophet**) with non-linear machine learning algorithms (**XGBoost**, **Random Forest**) to benchmark predictive accuracy and dissect the structural drivers of consumer demand.

---

## Research Questions (RQs)

1. **RQ1 (Predictive Performance):** How do traditional statistical time-series models compare against tree-based machine learning ensembles in predicting weekly store-level retail sales?

2. **RQ2 (Promotional Impact):** To what extent do statutory holidays and marketing markdowns influence weekly sales velocity and consumer purchasing behavior?

3. **RQ3 (Store Heterogeneity):** How do physical store classifications (Store Type and Scale) and regional geographies impact baseline revenue distribution?

4. **RQ4 (Macroeconomic Interactions):** Do external macroeconomic indicators (CPI, fuel price, unemployment, temperature) exhibit significant linear interaction with weekly store demand?

---

## Repository Structure

```text
retail-sales-forecasting/
│
├── data/
│   ├── raw/
│   │   ├── Dataset (Features).csv
│   │   ├── Dataset (sales).csv
│   │   └── Dataset (stores).csv
│   │
│   └── processed/
│       ├── master_cleaned_sales.csv
│       └── master_engineered_sales.csv
│
├── notebooks/
│   ├── 01_data_cleaning.ipynb
│   ├── 02_feature_engineering.ipynb
│   ├── 03_time_series_baseline.ipynb
│   └── 04_advanced_ml_evaluation.ipynb
│
├── visualizations/
│   ├── correlation_matrix_heatmap.png
│   ├── fig1_ml_feature_importances.png
│   ├── fig2_rq2_holidays_markdowns_impact.png
│   ├── fig3_rq3_store_attributes_impact.png
│   ├── fig4_rq4_macroeconomic_correlation_heatmap.png
│   ├── traditional_models_forecast_comparison.png
│   ├── weekly_sales_by_season.png
│   └── weekly_sales_by_store_type.png
│
├── .gitignore
├── README.md
└── requirements.txt
```

---

## Methodology & Modular Pipeline

The analytical workflow is structured into four sequential, reproducible Jupyter Notebooks.

### Phase 1: Data Preprocessing (`01_data_cleaning.ipynb`)

- Integrated raw sales data, store attributes, and environmental features.
- Handled missing values.
- Performed structural data type normalization.
- Prepared a unified dataset for downstream analysis.

### Phase 2: Feature Engineering (`02_feature_engineering.ipynb`)

- Generated temporal autocorrelation features:
  - `sales_lag_1`
  - `sales_lag_4`
- Calculated 4-week rolling moving averages:
  - `sales_rolling_mean_4`
- Applied One-Hot Encoding to categorical store types and geographical regions.
- Prepared engineered features for machine learning evaluation.

### Phase 3: Statistical Baseline Modeling (`03_time_series_baseline.ipynb`)

- Implemented classical univariate and multivariate time-series forecasting frameworks.
- Evaluated:
  - **ARIMA**
  - **SARIMA**
  - **Prophet**
- Conducted out-of-sample forecasting evaluation to establish statistical baseline performance.

### Phase 4: Machine Learning & Empirical Synthesis (`04_advanced_ml_evaluation.ipynb`)

- Trained ensemble machine learning models:
  - **XGBoost**
  - **Random Forest**
- Computed feature importance metrics to identify key demand drivers.
- Benchmarked statistical and machine learning models.
- Conducted empirical analysis addressing RQ1 through RQ4.

---

## Empirical Findings & Model Benchmarking (RQ1)

Models were evaluated on identical test splits using **Root Mean Squared Error (RMSE)** and **Mean Absolute Error (MAE)**.

| **Model Architecture** | **Model Variant** | **MAE ($)** | **RMSE ($)** | **Empirical Ranking** |
|:---|:---|---:|---:|:---|
| **Traditional Time-Series** | **ARIMA(1,1,1)** | **39,448.05** | **46,284.69** | **Rank 1 (Best Overall Accuracy)** |
| **Traditional Time-Series** | SARIMA | 40,055.98 | 47,795.23 | Rank 2 |
| **Machine Learning** | **Random Forest** | **45,314.37** | **49,028.19** | **Rank 3 (Best ML Model)** |
| Traditional Time-Series | Naive Baseline | 41,193.71 | 50,205.85 | Rank 4 |
| Machine Learning | XGBoost | 46,509.10 | 52,676.87 | Rank 5 |
| Traditional Time-Series | Prophet | 43,021.44 | 54,453.00 | Rank 6 |

**Key Finding:** ARIMA(1,1,1) achieved the lowest MAE and RMSE among all evaluated models, demonstrating the strongest predictive performance in this experimental setting.

---

## Core Insights & Business Implications

### 1. Model Superiority (RQ1)

Classical econometric modeling via **ARIMA(1,1,1)** outperformed non-linear machine learning algorithms in capturing single-series temporal dependencies, suggesting that linear lag momentum dominates store-level aggregate forecasting in this experimental setting.

### 2. Promotional Elasticity (RQ2)

Holiday weeks triggered an average sales volume of **$98,867.76**, compared with **$57,740.56** during non-holiday periods, indicating an approximately **71.2% commercial lift**.

Feature importance analysis further identified promotional markdowns (`markdown_3`, `markdown_4`) and historical sales lags as primary demand accelerators.

### 3. Store Heterogeneity (RQ3)

**Type A** locations dominate baseline retail turnover:

- **Mean Sales:** $79,952.03
- **Maximum Sales Peak:** $505,958.73

Type A stores outperform Type B and Type C locations, indicating that structural store scale has a substantial influence on sales capacity compared with geographic regional allocation.

### 4. Macroeconomic Invariance (RQ4)

Macroeconomic indicators (`cpi`, `fuel_price`, `unemployment`, `temperature`) exhibited near-zero linear correlations with weekly demand (approximately **0.00 to -0.006**).

This suggests that internal retail operational timing and historical sales momentum are more strongly associated with demand variation than the examined external macroeconomic indicators.

---

## Conclusion

This empirical study highlights the effectiveness of classical time-series techniques, particularly **ARIMA**, for aggregate store-level sales forecasting, while identifying **Random Forest** as a strong non-parametric alternative when incorporating multivariate features.

The findings provide several practical implications for retail inventory planners and supply chain managers:

- Prioritize historical sales patterns and lag-based demand signals.
- Incorporate holiday schedules into inventory and promotional planning.
- Account for physical store characteristics when allocating inventory.
- Evaluate promotional markdowns as important demand-driving factors.
- Avoid relying exclusively on external macroeconomic indicators for short-term demand forecasting.

Overall, the study demonstrates how combining statistical forecasting, machine learning, and empirical business analysis can support more informed retail demand planning and inventory optimization.

---

## 👤 Author

**Mohammad Sourav**

*Interdisciplinary Researcher | Consumer Psychology, Artificial Intelligence & Data Science*
