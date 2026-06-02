# TÜİK Forecasting Project

## 1. Project Overview

This project develops an R-based forecasting analysis using a time series data set obtained from the TÜİK Data Portal. The selected data set is Health Expenditures under the Health and Social Protection theme.

The project forecasts total health expenditure in Türkiye for the next available annual period after the latest TÜİK observation.

## 2. Data Source and TÜİK Connection

- TÜİK data set name: Health Expenditures
- TÜİK theme/category: Health and Social Protection
- TÜİK table name: Health Expenditures
- tuikr dataflow ID: NA - istab table accessed via `tuikr::statistical_tables("12")` table_url
- Selected variable: Total Health Expenditure - General Total
- Unit: Million TRY
- Data frequency: Annual
- Time coverage: 1999 / 2024
- Latest available observation: 2024
- Forecast target period: 2025
- R package used for data access: `tuikr`
- Package source: https://github.com/emraher/tuikr

The data were accessed directly in R using `tuikr::statistical_tables("12")` and the corresponding TÜİK table URL. The table file was then retrieved in R using `httr::GET()`. No manually downloaded, manually edited, or separately prepared data file was used.

## 3. Research Objective

The objective of this project is to forecast total health expenditure in Türkiye for 2025 using annual TÜİK data. The selected variable is meaningful because health expenditure is an important indicator of the size and development of the health system and public/private health financing.

## 4. Use of TÜİK Data in R

The TÜİK table was identified through the `tuikr` package. Since the selected table is an `istab` table, the table URL returned by `tuikr::statistical_tables("12")` was used to access the data directly in R.

The raw TÜİK table was cleaned inside the R Markdown notebook. The analysis selected the "Total health expenditure" row and the "General total" column. The resulting time series covers 1999 to 2024 and is measured in million TRY.

## 5. Exploratory Time Series Analysis

The selected time series shows a strong upward trend over time. This increase is expected because total health expenditure is reported in nominal million TRY and may be affected by inflation, population growth, expansion of health services, and changes in health financing.

Since the data are annual, the series does not contain monthly or quarterly seasonality. Therefore, seasonal forecasting methods are not applicable to this selected time series.

## 6. Forecasting Methods Applied

The following forecasting methods were applied:

- Naïve Forecasting
- Moving Average
- Weighted Moving Average
- Exponential Smoothing
- Trend-Adjusted Exponential Smoothing
- Linear Trend Projection

The following methods were considered but not applied because the data are annual and do not contain recurring seasonal periods:

- Seasonal Indices
- Additive Decomposition
- Multiplicative Decomposition
- Regression with Trend and Seasonal Dummy Variables

## 7. Forecast Accuracy Comparison

The candidate methods were compared using the following accuracy and monitoring measures:

- Bias / Mean Error
- MAD
- MSE
- MAPE
- RSFE
- Tracking Signal

The full comparison table is saved in:

`outputs/tables/accuracy_comparison.csv`

## 8. Selection of the Superior Method

The superior method was selected based on both forecast accuracy and suitability to the structure of the selected time series. Since total health expenditure has a strong upward trend and no seasonal structure, methods that can better reflect the trend pattern are more appropriate than purely level-based methods.

The selected superior method and its final forecast are reported in:

`outputs/tables/final_forecast.csv`

## 9. Final Next-Period Forecast

- Latest available observation: 2024
- Forecast target period: 2025
- Forecasted variable: Total Health Expenditure - General Total
- Unit: Million TRY

The final forecast value is produced in the R Markdown notebook and saved in `outputs/tables/final_forecast.csv`.

## 10. Interpretation of Results

The final forecast represents the estimated total health expenditure in Türkiye for 2025, based on historical annual TÜİK data from 1999 to 2024. The result should be interpreted as a quantitative time series forecast based only on past values of health expenditure.

## 11. Limitations

This project has several limitations. First, the selected series is annual, so the number of observations is more limited than in monthly or quarterly data. Second, the variable is reported in nominal million TRY, so inflation strongly affects the upward movement of the series. Third, the models use only past health expenditure values and do not include external explanatory variables such as inflation, population, exchange rates, health policy changes, or public budget changes. Finally, TÜİK data may be revised in future releases.

## 12. Reproducibility

To reproduce the project:

1. Clone or download this repository.
2. Open the project in RStudio.
3. Restore the package environment if needed:
```r
renv::restore()
## 13. Repository Structure

R_Based_Forecasting_Quant/
├── README.md
├── forecasting_project.Rmd
├── forecasting_project.html
├── outputs/
│   ├── tables/
│   │   ├── accuracy_comparison.csv
│   │   └── final_forecast.csv
│   └── figures/
├── renv.lock
└── .gitignore

## 14. Author

- Student name: Burak Alper Kara
- Student number: 138722517
- Course name: Quantative Analysis
