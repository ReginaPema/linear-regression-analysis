# <img src="https://img.icons8.com/?size=50&id=HQtNBWg4FaaB&format=png&color=000000" align="center"/> Linear Regression Analysis
### Análisis de Regresión Lineal: del Modelo Simple a la Validación Completa

> **EN** · Six notebooks covering the full spectrum of linear regression: from non-linear growth models and regularization (Ridge/Lasso) through multiple regression via matrix algebra, stepwise variable selection, and full assumption validation with manual vs library verification. Datasets span economics, environmental science, and real estate.
>
> **ES** · Seis notebooks que cubren el espectro completo de la regresión lineal: desde modelos de crecimiento no lineal y regularización (Ridge/Lasso) hasta regresión múltiple por álgebra matricial, selección stepwise de variables, y validación completa de supuestos con verificación manual vs librería. Los datasets abarcan economía, ciencias ambientales e inmobiliario.

---

## <img src="https://img.icons8.com/?size=40&id=80454&format=png&color=000000" align="center"/> Notebooks

### 01 · Logistic Growth Model: Mexico GDP (1960–2021)
**Dataset:** World Bank; Mexico GDP historical data (`Mexico GDP.xlsx`)

- Fit a logistic S-curve growth model to 62 years of GDP data using `scipy.optimize`
- Compared logistic model vs linear regression baseline
- Generated GDP forecast through 2040
- Validated model fit with residual analysis

---

### 02 · Ridge & Lasso Regularization: Vehicle CO₂ Emissions
**Dataset:** `FuelConsumptionCo2.xlsx`; vehicle fuel consumption and emissions

- Applied and compared OLS, Ridge and Lasso regression for CO₂ prediction
- Found optimal alpha via cross-validation for each regularized model
- **Verified:** `predict()` output matches manual matrix calculation β = (XᵀX)⁻¹Xᵀy exactly
- Demonstrated when regularization adds value vs when OLS is sufficient

---

### 03 · Advanced Statistics & Regression: Ames Housing
**Dataset:** Ames Housing (Kaggle); house sale prices in Ames, Iowa

- Normality tests (Shapiro-Wilk, QQ plots) on `SalePrice`, `GrLivArea`, `2ndFlrSF`
- VIF multicollinearity detection and variance analysis
- Linear regression: `SalePrice ~ GrLivArea + 2ndFlrSF`
- Validated all 4 regression assumptions; identified mild heteroscedasticity at high price range

---

### 04 · Multiple Regression via Matrix Algebra: King County Housing
**Dataset:** `kc_house_data.csv`; 21,613 house sales in King County, Seattle

- Derived OLS coefficients with the closed-form matrix solution: **β = (XᵀX)⁻¹Xᵀy**
- Cross-validated against `statsmodels` OLS and `sklearn`; results identical
- Variable selection by correlation → VIF → p-value (stepwise)
- **Final equation:** price = −21,812,893 + 173.78·sqft_living + 106,954·grade + ... (10 variables)
- **R² = 0.6920** | Mild heteroscedasticity noted at high price range

---

### 05 · Hypothesis Testing & Stepwise: King County Housing
**Dataset:** `kc_house_data.csv`; same as notebook 04  
**Builds on:** notebook 04, extends to formal statistical testing

- 17 candidate variables after dropping `sqft_basement` (perfect multicollinearity with `sqft_living + sqft_above`)
- Applied 3 parallel StepWise methods: t-Student, p-value, confidence interval
- **All 3 methods consistently eliminated only `floors`** (no statistically significant effect on price)
- Final model: 16 variables, **R²≈0.700**, F-test significant overall

---

### 06 · Regression Assumptions & Prediction Intervals: Advertising
**Dataset:** `Advertising.csv`; TV, Radio, Newspaper spend vs Sales (200 observations)

- Eliminated `Newspaper` (p≈0.839) → **final model: Sales = 4.639 + 0.055·TV + 0.102·Radio**
- **R² = 0.899 (train) | 0.907 (test)**. Excellent generalization, no overfitting
- Computed **90% prediction interval** for TV=100, Radio=50 → Sales≈15.22, PI=[12.34, 18.10]
- Validated 4 regression assumptions using **both library and manual formulas:**
  - Normality: Jarque-Bera
  - Homoscedasticity: White test
  - Independence: Durbin-Watson
  - Linearity: residuals vs fitted

---

## <img src="https://img.icons8.com/?size=40&id=80717&format=png&color=000000" align="center"/> Model Summary / Resumen de Modelos

| Notebook | Dataset | Target | R² | Key Technique |
|---|---|---|---|---|
| 01 | Mexico GDP | GDP (log scale) | — | Logistic growth curve |
| 02 | CO₂ Vehicles | CO₂ emissions | — | Ridge α · Lasso α · OLS |
| 03 | Ames Housing | SalePrice | — | Normality + VIF + assumptions |
| 04 | King County | Price | 0.6920 | β = (XᵀX)⁻¹Xᵀy · 10 vars |
| 05 | King County | Price | 0.700 | StepWise (3 methods) · 16 vars |
| 06 | Advertising | Sales | 0.907 | Final eqn + 90% PI + 4 assumptions |

---

## <img src="https://img.icons8.com/?size=40&id=80431&format=png&color=000000" align="center"/> Tools / Herramientas

![Python](https://img.shields.io/badge/Python-8B9E8B?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-6B7F6B?style=flat&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-7A9E9F?style=flat&logo=numpy&logoColor=white)
![Statsmodels](https://img.shields.io/badge/Statsmodels-4B6CB7?style=flat)
![Scikit-learn](https://img.shields.io/badge/scikit--learn-B8A9C9?style=flat&logo=scikit-learn&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-7A9E9F?style=flat&logo=scipy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557c?style=flat)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=flat)

---

## <img src="https://img.icons8.com/?size=40&id=80358&format=png&color=000000" align="center"/> Related Projects / Proyectos Relacionados

| Project | Description |
|---|---|
| [ARIMA-SARIMA_sales_forecast](https://github.com/ReginaPema/ARIMA-SARIMA_sales_forecast) | Time series forecasting: ARIMA/SARIMA vs linear regression benchmark |
| [eda-retail-sales-analysis](https://github.com/ReginaPema/eda-retail-sales-analysis) | EDA with correlation and statistical analysis (r=0.92 units→sales) |

---

## <img src="https://img.icons8.com/?size=40&id=PhymLYNNjf3I&format=png&color=000000" align="center"/> Repository Structure / Estructura

```
linear-regression-analysis/
├── notebooks/
│   ├── 01_logistic_regression_mexico_gdp.ipynb
│   ├── 02_ridge_lasso_co2_vehicles.ipynb
│   ├── 03_statistics_regression_ames_housing.ipynb
│   ├── 04_multiple_regression_matrix_kingcounty.ipynb
│   ├── 05_stepwise_hypothesis_testing_kingcounty.ipynb
│   └── 06_regression_assumptions_advertising.ipynb
├── data/
│   ├── Mexico GDP.xlsx
│   ├── FuelConsumptionCo2.xlsx
│   ├── kc_house_data.csv       ← used by notebooks 04 & 05
│   └── Advertising.csv
└── README.md
```

> **Note / Nota:** The Ames Housing dataset (notebook 03) loads directly from Kaggle or a local copy (see notebook instructions). All other datasets must be placed in the same carpet as the notebook before running.

---

*Project developed as part of the Data Scientist Certificate · 
Proyecto desarrollado como parte del certificado Científico de Datos — EBAC (2026)* <img src="https://img.icons8.com/?size=35&id=FgMs84V9yrMV&format=png&color=000000" align="center"/>
