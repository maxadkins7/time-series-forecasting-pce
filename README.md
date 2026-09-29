# Time Series Forecasting & Model Evaluation

Graduate quantitative economics project comparing the forecasting performance of four autoregressive models for the quarterly growth rate of real personal consumption expenditures per capita on nondurable goods.

## Full Work Sample

[View the complete forecasting work sample](docs/Max_Adkins_Time_Series_Forecasting_Work_Sample.pdf)

## Project Overview

The objective of this project was to determine which autoregressive specification — AR(1), AR(2), AR(3), or AR(4) — produced the most reliable out-of-sample forecasts for U.S. real personal consumption expenditures per capita on nondurable goods.

Rather than selecting a model based only on in-sample fit, I used an expanding-window pseudo out-of-sample forecasting design to evaluate how the models performed as new data became available.

**Tool:** EViews  
**Data Source:** Federal Reserve Economic Data (FRED)  
**FRED Series:** `A796RX0Q048SBEA`  
**Forecast Models:** AR(1), AR(2), AR(3), AR(4)  
**Forecast Horizons:** 1, 2, 3, and 4 quarters ahead

---

## Data

The project uses the FRED series:

**Real Personal Consumption Expenditures Per Capita: Goods: Nondurable Goods**

The underlying level series is quarterly and reported in chained 2017 dollars at a seasonally adjusted annual rate.

For the original analysis, the raw series was used through **2020Q1**. Because the forecasting models analyze growth rather than the level of the series, the data was transformed into an annualized quarterly log growth rate:

`Growth_t = 400 × [ln(Y_t) - ln(Y_t-1)]`

This results in a usable transformed sample beginning in **1947Q2**.

The original raw FRED data is stored in:

`data/raw/A796RX0Q048SBEA.csv`

---

## Forecasting Methodology

I estimated four autoregressive specifications:

- AR(1)
- AR(2)
- AR(3)
- AR(4)

The forecasting exercise used an **expanding-window pseudo out-of-sample design**.

The first estimation window covered:

**1947Q2–1989Q4**

Each model generated forecasts 1 through 4 quarters ahead. The estimation window was then expanded by one quarter, the models were re-estimated, and new forecasts were generated.

This process was repeated through **2020Q1**.

This approach mimics a real-time forecasting environment because each forecast is generated using only information that would have been available at that point in time.

---

## Model Evaluation

Model performance was evaluated using both in-sample diagnostics and out-of-sample forecasting tests.

### In-Sample Evaluation

- Akaike Information Criterion (AIC)
- Schwarz Information Criterion (SIC)
- Ljung-Box residual autocorrelation tests
- Jarque-Bera residual normality tests

### Out-of-Sample Evaluation

Forecast accuracy was compared using:

- Mean Squared Error (MSE)
- Median Squared Error (MEdSE)
- Mean Absolute Error (MAE)

Additional forecast evaluation included:

- Forecast bias tests
- Mincer-Zarnowitz calibration tests
- Forecast-error dependence tests
- Forecast encompassing tests
- Forecast-versus-realization analysis

---

## Key Result

**AR(3) produced the strongest overall forecast accuracy.**

It generated the lowest:

- Mean Squared Error
- Median Squared Error
- Mean Absolute Error

at all four forecast horizons.

### Mean Squared Error by Forecast Horizon

| Forecast Horizon | AR(1) | AR(2) | AR(3) | AR(4) |
|---|---:|---:|---:|---:|
| 1 Quarter | 6.0024 | 5.7357 | **5.5616** | 5.6812 |
| 2 Quarters | 6.0910 | 5.7770 | **5.5879** | 5.7209 |
| 3 Quarters | 6.1428 | 6.0696 | **5.8507** | 6.0305 |
| 4 Quarters | 6.1779 | 6.1492 | **6.1027** | 6.3051 |

The consistency of the AR(3) result across multiple forecast horizons and loss measures provided the strongest evidence in favor of that specification.

---

## Important Limitations

AR(3) did not outperform every competing model on every diagnostic.

The analysis also found that:

- residual normality was rejected across the models;
- forecast-error dependence remained at some horizons;
- in-sample model-selection criteria did not identify one universally preferred model;
- forecast encompassing tests indicated that competing specifications could still contain useful information in selected comparisons.

For that reason, the conclusion was based on the overall body of forecast evidence rather than a claim that AR(3) was universally superior.

---

## Skills Demonstrated

- Time-series forecasting
- Autoregressive modeling
- Expanding-window backtesting
- Out-of-sample model evaluation
- Forecast accuracy analysis
- Statistical diagnostics
- Macroeconomic data analysis
- Model comparison
- Quantitative interpretation
- Research communication

---

## Project Context

This project was completed as part of graduate coursework in Quantitative Economics / Econometrics at East Carolina University.

The goal of the project was not simply to identify the model with the best in-sample fit, but to evaluate competing forecasting models using repeated out-of-sample prediction and multiple statistical diagnostics.

---

## Repository Structure

```text
time-series-forecasting-pce/
│
├── README.md
│
├── data/
│   └── raw/
│       └── A796RX0Q048SBEA.csv
│
└── docs/
    └── Max_Adkins_Time_Series_Forecasting_Work_Sample.pdf
