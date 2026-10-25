
# ✈️ Air Passenger Forecasting Using ARIMA and SARIMA

---

## 📌 Project Overview

This project focuses on analyzing historical airline passenger data and forecasting future passenger demand using time series forecasting techniques. The project uses ARIMA and SARIMA models to identify trends, understand seasonal patterns, and predict future passenger numbers.

The dataset contains monthly airline passenger records from January 1949 to December 1960. The project includes data preprocessing, exploratory data analysis (EDA), stationarity testing, model building, performance evaluation, and future forecasting.

The main goal is to compare ARIMA and SARIMA models and identify which model performs better for airline passenger forecasting.

---

## 🎯 Project Objectives

- Analyze historical airline passenger data.
- Identify long-term trends and seasonal patterns.
- Perform data preprocessing and exploratory data analysis.
- Test time series stationarity using the Augmented Dickey-Fuller (ADF) test.
- Build an ARIMA forecasting model.
- Build a seasonal SARIMA forecasting model.
- Compare model performance using MAE and RMSE.
- Forecast passenger demand for the next 12 months.
- Visualize historical data and forecasted passenger numbers.
- Export future predictions to CSV files.

---

## 📊 Dataset Description

The project uses the AirPassengers dataset, which contains monthly airline passenger totals from 1949 to 1960.

**Dataset Information:**

- Dataset Name: AirPassengers
- Time Period: January 1949 – December 1960
- Total Observations: 144
- Frequency: Monthly
- Target Variable: Passengers
- Data Type: Time Series
- Missing Values: None in the provided dataset

**Dataset Features:**

- `Month`: The month and year of the observation.
- `Passengers`: The number of airline passengers recorded during that month.

The dataset shows an increasing trend in passenger traffic, along with recurring seasonal fluctuations.

---

## 🛠️ Technologies and Libraries Used

The following technologies and Python libraries were used in this project:

- Python
- Pandas
- NumPy
- Matplotlib
- Statsmodels
- Scikit-learn
- Google Colab
- Jupyter Notebook

**Libraries and Their Purposes:**

- **Pandas:** Data loading, manipulation, and preprocessing.
- **NumPy:** Numerical calculations.
- **Matplotlib:** Data visualization and forecasting plots.
- **Statsmodels:** ARIMA, SARIMA, and stationarity testing.
- **Scikit-learn:** Model evaluation using MAE and RMSE.
- **Google Colab:** Cloud-based development and execution.

---

## 🔍 Project Workflow

### 1. Data Loading and Preprocessing

- Loaded the AirPassengers dataset using Pandas.
- Converted the month column into datetime format.
- Set the month column as the time series index.
- Inspected the dataset structure and data types.
- Checked for missing values.
- Prepared the data for time series forecasting.

### 2. Exploratory Data Analysis (EDA)

Exploratory Data Analysis was performed to understand the characteristics of the dataset.

The analysis included:

- Visualizing monthly passenger traffic.
- Identifying long-term growth trends.
- Observing yearly seasonal patterns.
- Understanding fluctuations in passenger demand.

The time series visualization showed that passenger traffic increased over time and followed recurring seasonal patterns.

### 3. Stationarity Testing

The Augmented Dickey-Fuller (ADF) test was used to check whether the original time series was stationary.

**ADF Test Results:**

- ADF Statistic: 0.8154
- p-value: 0.9919
- Significance Level: 0.05
- Conclusion: The original time series is non-stationary.

Since the p-value was greater than 0.05, the null hypothesis of a unit root could not be rejected.

Differencing was incorporated into the forecasting models to address the non-stationary behavior of the data.

### 4. Train-Test Split

The dataset was divided into training and testing sets while preserving chronological order.

- Training Data: 115 observations
- Testing Data: 29 observations
- Total Observations: 144
- Training Percentage: Approximately 80%
- Testing Percentage: Approximately 20%

The training set was used to build the models, while the testing set was used to evaluate forecasting performance.

### 5. ARIMA Model Development

An ARIMA model was developed using the following configuration:

`ARIMA(1,1,1)`

ARIMA stands for Autoregressive Integrated Moving Average.

The model uses autoregressive, differencing, and moving-average components to identify relationships in historical time series data.

However, the standard ARIMA model does not explicitly model yearly seasonality.

### 6. SARIMA Model Development

A Seasonal Autoregressive Integrated Moving Average (SARIMA) model was developed to capture both trend-related changes and recurring seasonal patterns.

**Model Configuration:**

`SARIMA(1,1,1)(1,1,1,12)`

**Model Parameters:**

- `p = 1`: Non-seasonal autoregressive order.
- `d = 1`: Non-seasonal differencing order.
- `q = 1`: Non-seasonal moving-average order.
- `P = 1`: Seasonal autoregressive order.
- `D = 1`: Seasonal differencing order.
- `Q = 1`: Seasonal moving-average order.
- `s = 12`: Seasonal period of 12 months.

The seasonal period of 12 allows the model to account for recurring annual patterns in passenger traffic.

### 7. Model Evaluation

Both models were evaluated using two statistical performance metrics.

**Mean Absolute Error (MAE)**

MAE measures the average absolute difference between actual and predicted passenger counts. A lower MAE indicates better predictive performance.

**Root Mean Squared Error (RMSE)**

RMSE measures the square root of the average squared prediction errors. It penalizes larger prediction errors more heavily than MAE. A lower RMSE indicates better predictive performance.

### 8. Future Forecasting

After evaluating the models, the SARIMA model was fitted to the complete historical dataset.

The final model was used to forecast passenger demand for the next 12 months, corresponding to January through December 1961.

The forecasted values were visualized alongside historical passenger data and exported to CSV files for further analysis.

---

## 📈 Model Performance and Results

The following results were obtained from the 29-observation test set.

| Model | MAE | RMSE |
|---|---:|---:|
| ARIMA(1,1,1) | 85.25 | 97.50 |
| SARIMA(1,1,1)(1,1,1,12) | 23.56 | 30.14 |

### Key Findings

- The original time series was non-stationary.
- Airline passenger traffic showed a clear increasing trend.
- Passenger numbers exhibited recurring seasonal patterns.
- The ARIMA model produced relatively high forecasting errors.
- The SARIMA model achieved lower MAE and RMSE by incorporating seasonality.
- The final SARIMA model was used to forecast passenger demand for 1961.

**Result:** Based on the reported test-set metrics, SARIMA performed better than ARIMA for this dataset.

---

## 📉 Data Visualizations

The project includes the following visualizations:

- **Historical Passenger Traffic:** Displays monthly airline passenger numbers from 1949 to 1960.
- **Actual vs. Forecasted Passengers:** Compares actual passenger counts with model predictions.
- **ARIMA Forecast:** Visualizes predictions generated by the ARIMA model.
- **SARIMA Forecast:** Compares actual values with seasonal model predictions.
- **Future Passenger Forecast:** Displays historical passenger traffic alongside the 12-month forecast for 1961.

These visualizations help demonstrate the trends, seasonal patterns, and forecasting performance of the models.

---

## 📁 Project Structure

```text
Air-Passenger-Forecasting/
│
├── README.md
├── AirPassengers.csv
├── AirPassenger_Forecasting.ipynb
├── AirPassengers_Future_Forecast.csv
└── AirPassengers_SARIMA_Forecast.csv
```

**Note:** The filenames above are examples based on the project. Make sure they match the actual files in your GitHub repository.

---

## ⚙️ Installation and Setup

### Prerequisites

- Python 3.9 or later
- Jupyter Notebook or Google Colab
- Basic knowledge of Python and time series analysis

### Step 1: Clone the Repository

```bash
git clone https://github.com/your-username/Air-Passenger-Forecasting.git
```

### Step 2: Navigate to the Project Directory

```bash
cd Air-Passenger-Forecasting
```

### Step 3: Install Required Libraries

```bash
pip install pandas numpy matplotlib statsmodels scikit-learn jupyter
```

### Step 4: Run the Notebook

```bash
jupyter notebook
```

Alternatively, upload the notebook to Google Colab and run the cells sequentially.

### Step 5: Load the Dataset

Make sure the dataset path matches your local environment.

```python
import pandas as pd

df = pd.read_csv("AirPassengers.csv")
```

---

## 💾 Output Files

The project generates the following CSV files:

- `AirPassengers_Future_Forecast.csv`
- `AirPassengers_SARIMA_Forecast.csv`

These files contain the forecast dates and predicted passenger numbers for the next 12 months.

**Output Columns:**

- `Date`: Forecast month.
- `Predicted_Passengers`: Predicted number of passengers.

The forecast values are generated by executing the corresponding notebook cells.

---

## 💡 Applications

This project demonstrates techniques that can be applied to:

- Airline passenger demand forecasting.
- Transportation demand analysis.
- Seasonal business forecasting.
- Capacity and resource planning.
- Historical trend analysis.
- Time series modeling.
- Predictive analytics.

The forecasts are based on historical data and are intended to demonstrate forecasting techniques rather than predict current airline demand.

---

## ⚠️ Limitations and Future Improvements

Although the SARIMA model performed better than ARIMA in this experiment, several improvements could be explored:

- Optimize model parameters using grid search and information criteria.
- Compare SARIMA with Holt-Winters Exponential Smoothing.
- Experiment with SARIMAX and other forecasting methods.
- Perform residual analysis to identify remaining patterns.
- Use rolling-origin time series cross-validation.
- Compare the models against a seasonal-naive baseline.
- Generate prediction intervals to measure forecast uncertainty.
- Investigate logarithmic transformations to address changing variance.

The reported evaluation metrics are based on a single chronological train-test split, so results may vary with different configurations and evaluation methods.

---

## 📝 Conclusion

This project demonstrates the use of time series forecasting techniques to analyze historical airline passenger traffic and predict future passenger demand.

The analysis included data preprocessing, exploratory data analysis, stationarity testing, model development, evaluation, and visualization.

Two models, ARIMA and SARIMA, were evaluated using Mean Absolute Error (MAE) and Root Mean Squared Error (RMSE).

The ARIMA model achieved an MAE of approximately 85.25 and an RMSE of approximately 97.50. In comparison, the SARIMA model achieved an MAE of approximately 23.56 and an RMSE of approximately 30.14 on the reported test set.

These results demonstrate that incorporating seasonal patterns improved forecasting performance for this dataset.

The final SARIMA model was fitted to the complete historical dataset and used to forecast monthly passenger numbers for 1961.

Overall, this project provides practical experience in Python-based data analysis, time series modeling, statistical forecasting, model evaluation, and data visualization. It also highlights the importance of accounting for seasonality when working with time-dependent data.

---

## 👨‍💻 Author

**Your Name**

- GitHub: https://github.com/your-username
- Project: Air Passenger Forecasting Using ARIMA and SARIMA

---

## ⭐ Support

If you find this project useful for learning data science and time series forecasting, consider giving the repository a star on GitHub.

---

## 🏷️ Tags

`Python` `Data Science` `Time Series Forecasting` `ARIMA` `SARIMA` `Pandas` `NumPy` `Matplotlib` `Statsmodels` `Machine Learning`

