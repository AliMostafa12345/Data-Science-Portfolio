# Renewable Energy Share Forecasting Using ARIMA

## Project Overview

This project focuses on analyzing and forecasting the share of renewable energy in total final energy consumption in the United States using time series analysis and statistical forecasting techniques.

The project uses historical yearly data to identify trends, evaluate stationarity, and forecast renewable energy share values using an ARIMA (AutoRegressive Integrated Moving Average) model.

---

## Problem Statement

Understanding changes in renewable energy consumption is important for energy planning, sustainability initiatives, and environmental decision-making.

The objective of this project is to analyze historical renewable energy consumption trends in the United States and develop a time series forecasting model to predict renewable energy share based on historical observations.

---

## Dataset Description

The project uses the **Global Data on Sustainable Energy** dataset.

The dataset contains information about sustainable energy indicators across different countries and years.

### Selected Features

| Feature | Description |
|---|---|
| `Entity` | Country or geographical entity |
| `Year` | Year of the observation |
| `Renewable_Energy_Share` | Share of renewable energy in total final energy consumption, expressed as a percentage |

The analysis focuses specifically on the United States and its historical renewable energy share.

---

## Technologies and Libraries

- **Python** — Data analysis and model development
- **Pandas** — Data loading, filtering, and manipulation
- **NumPy** — Numerical computations
- **Matplotlib** — Data visualization
- **Statsmodels** — Stationarity testing and ARIMA modeling
- **Scikit-learn** — Forecast evaluation metrics

---

## Project Workflow

### 1. Data Loading and Exploration

The dataset was loaded into a Pandas DataFrame and explored to understand its structure, data types, and missing values.

The initial exploration included:

- Inspecting the first few records.
- Examining dataset information and column data types.
- Checking for missing values.
- Identifying the relevant variables for time series analysis.

### 2. Data Preparation

The dataset was filtered to include only observations for the United States.

The following preprocessing steps were performed:

- Selected the `Year` and renewable energy share columns.
- Renamed the selected columns for easier analysis.
- Removed observations with missing values.
- Converted the `Year` column into a datetime format.
- Set the year as the time series index.

### 3. Exploratory Time Series Analysis

The historical renewable energy share was visualized using a line chart.

The visualization helps examine changes in renewable energy consumption over time and identify the overall trend in the selected country.

### 4. Stationarity Testing

The **Augmented Dickey-Fuller (ADF) test** was used to determine whether the original time series was stationary.

The initial test produced the following results:

| Metric | Result |
|---|---:|
| ADF Statistic | -0.4655 |
| p-value | 0.8986 |
| Significance Level | 0.05 |
| Result | Non-stationary |

Since the p-value was greater than 0.05, the null hypothesis of a unit root could not be rejected. Therefore, the original time series was considered non-stationary.

### 5. First-Order Differencing

First-order differencing was applied to help remove the trend-related non-stationarity in the original time series.

The differenced series was visualized and evaluated again using the ADF test.

| Metric | Result |
|---|---:|
| ADF Statistic | -5.9750 |
| p-value | 1.8971 × 10⁻⁷ |
| Significance Level | 0.05 |
| Result | Stationary |

The p-value was below 0.05, providing evidence to reject the null hypothesis of a unit root. The differenced series was therefore considered stationary according to the ADF test.

### 6. ARIMA Model Development

The ARIMA model was selected to forecast renewable energy share using historical observations.

The model was configured with the following parameters:

- **p = 1:** Autoregressive order.
- **d = 1:** Differencing order.
- **q = 1:** Moving average order.

The final model configuration was **ARIMA(1, 1, 1)**.

The original time series was divided chronologically into training and testing subsets:

- **Training set:** 80% of the observations.
- **Testing set:** 20% of the observations.

The model was fitted using the training data, and forecasts were generated for the same number of periods as the testing set.

### 7. Model Evaluation

The model's forecasting performance was evaluated by comparing predicted values with actual renewable energy share observations.

The following evaluation metrics were used:

- **Mean Absolute Error (MAE):** Measures the average absolute difference between actual and forecast values.
- **Root Mean Squared Error (RMSE):** Measures the square root of the average squared prediction errors, giving greater weight to larger errors.

---

## Model Performance

The ARIMA(1, 1, 1) model achieved the following results on the test set:

| Evaluation Metric | Value |
|---|---:|
| Mean Absolute Error (MAE) | 0.8631 |
| Root Mean Squared Error (RMSE) | 0.9197 |

Both metrics are expressed in the units of the target variable, renewable energy share measured in percentage points.

The results indicate that the forecasts had an average absolute error of approximately **0.86 percentage points** on the test observations.

### Forecast Visualization

A comparison plot was created to visualize actual renewable energy share values against the ARIMA forecast values.

The visualization helps assess how closely the forecast follows the observed values over the testing period.

---

## Key Findings

- The original renewable energy share time series was non-stationary according to the ADF test.
- First-order differencing produced a stationary series according to the subsequent ADF test.
- The ARIMA(1, 1, 1) model was used to forecast renewable energy share from historical observations.
- The model achieved an MAE of approximately 0.863 and an RMSE of approximately 0.920.
- Comparing actual and forecast values provides insight into the model's ability to capture changes in renewable energy share.

---

## Conclusion

This project demonstrates the application of time series analysis to renewable energy consumption data. The workflow includes data exploration, preprocessing, visualization, stationarity testing, differencing, ARIMA forecasting, and model evaluation.

The ADF test identified non-stationarity in the original series, while first-order differencing provided evidence of stationarity. The ARIMA(1, 1, 1) model was then evaluated using MAE and RMSE, achieving values of approximately 0.863 and 0.920, respectively.

Overall, the project illustrates how statistical forecasting methods can support the analysis of historical renewable energy trends. More advanced forecasting approaches and additional validation could be explored to assess predictive performance further.

---

## Limitations

- The analysis focuses exclusively on the United States.
- The forecasting model uses a single historical time series and does not incorporate external variables that may influence renewable energy consumption.
- The dataset contains a limited number of annual observations, restricting the amount of historical information available for model training.
- The ARIMA parameters were specified directly rather than selected through a systematic model comparison process.
- Forecast performance on the test set does not guarantee the same accuracy for future observations.
