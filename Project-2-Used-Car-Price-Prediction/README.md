# Used Car Price Prediction

## 📌 Project Overview

This project uses machine learning regression techniques to predict used car prices based on vehicle characteristics such as brand, model year, mileage, fuel type, transmission, and engine size.

The project follows an end-to-end data science workflow, including data cleaning, exploratory data analysis, feature engineering, model training, performance evaluation, hyperparameter tuning, and saving the final trained model.

Three regression approaches were compared: Linear Regression, Random Forest Regressor, and XGBoost Regressor.

## 🎯 Objectives

- Analyze and understand used car listing data.
- Clean missing values and convert data into appropriate formats.
- Perform exploratory data analysis (EDA) to identify patterns in car prices.
- Engineer useful features from vehicle specifications.
- Apply a log transformation to reduce price skewness.
- Train and compare multiple regression models.
- Evaluate model performance using MAE, RMSE, and R² score.
- Tune the XGBoost model to improve predictive performance.
- Analyze feature importance and prediction errors.
- Save the final trained model for potential future use.

## 📊 Dataset

The dataset contains **4,009 used car listings** and 12 original columns.

### Dataset Features

| Feature | Description |
|---|---|
| `brand` | Vehicle manufacturer |
| `model` | Vehicle model |
| `model_year` | Manufacturing or model year |
| `milage` | Vehicle mileage |
| `fuel_type` | Type of fuel used |
| `engine` | Engine specifications |
| `transmission` | Transmission type |
| `ext_col` | Exterior color |
| `int_col` | Interior color |
| `accident` | Accident history information |
| `clean_title` | Clean title information |
| `price` | Listed price of the vehicle; target variable |

The dataset was loaded from `used_cars.csv`.

## 🛠️ Technologies and Libraries

- **Python** — Programming language
- **Pandas** — Data manipulation and analysis
- **NumPy** — Numerical computations
- **Matplotlib** — Data visualization
- **Seaborn** — Statistical visualization
- **Scikit-learn** — Data preprocessing, regression models, and evaluation metrics
- **XGBoost** — Gradient boosting regression
- **Joblib** — Saving the trained model
- **Google Colab** — Development environment

## 🔍 Project Workflow

### 1. Data Understanding

The dataset was examined to understand its structure and quality.

- Inspected the first few rows.
- Checked the number of rows and columns.
- Examined column names and data types.
- Generated descriptive statistics.
- Identified missing values and their percentages.
- Checked duplicate records and unique values in each column.

The original dataset contained 4,009 rows and 12 columns, with no duplicate rows.

### 2. Data Cleaning

Several preprocessing steps were performed to prepare the dataset for analysis and modeling.

- Removed currency symbols and commas from the `price` column.
- Removed mileage formatting characters from the `milage` column.
- Converted price and mileage into numeric data types.
- Filled missing categorical values using the most frequent value in each column.
- Checked the dataset again to confirm that missing values had been handled.

### 3. Exploratory Data Analysis (EDA)

Visualizations were created using Matplotlib and Seaborn to investigate the data.

- **Price distribution:** Examined the distribution of used car prices using a histogram and KDE curve.
- **Top car brands:** Identified the 15 most frequently listed brands.
- **Price by brand:** Compared price distributions across the 10 most common brands using box plots.
- **Mileage vs. price:** Investigated the relationship between vehicle mileage and listed price.
- **Model year vs. price:** Explored how vehicle age relates to price.
- **Correlation heatmap:** Examined correlations among numerical variables.

### 4. Log Transformation

The target price variable was heavily skewed, so a logarithmic transformation was applied.

The transformation used was:

`log_price = log1p(price)`

This transformation reduces the influence of extreme price values and allows the models to learn from a less-skewed target distribution.

Predictions were later converted back to the original price scale using the inverse transformation, `expm1()`.

### 5. Feature Engineering

Additional preprocessing was performed to create features suitable for machine learning.

- Extracted engine displacement in liters from the engine specifications.
- Created an `engine_size` feature.
- Removed the original `engine` column after extracting the engine size.
- Removed the original `price` column from the modeling features because the transformed `log_price` was used as the target.
- Removed rows where engine size could not be extracted.
- Excluded the high-cardinality `model` column from the encoded dataset.
- Applied Label Encoding to categorical features.

After filtering rows with missing extracted engine sizes, the modeling dataset contained **3,773 rows**.

### 6. Train-Test Split

The dataset was divided into training and testing sets.

- **Training data:** 80%
- **Testing data:** 20%
- **Random state:** 42

The resulting datasets contained 3,018 training samples and 755 testing samples.

### 7. Model Training

Three regression models were trained and evaluated.

#### Linear Regression

Used as a baseline model to estimate used car prices based on relationships between the input features and the transformed target.

#### Random Forest Regressor

An ensemble learning model using 200 decision trees to capture nonlinear relationships between vehicle characteristics and prices.

#### XGBoost Regressor

A gradient boosting model configured with 500 estimators, a learning rate of 0.05, and a maximum tree depth of 5.

### 8. Model Evaluation

The models were evaluated using three metrics.

- **Mean Absolute Error (MAE):** Measures the average absolute prediction error.
- **Root Mean Squared Error (RMSE):** Measures the square root of the average squared prediction error.
- **R² Score:** Measures how much variation in the target variable is explained by the model.

For the reported MAE, RMSE, and R² results, evaluation was performed on the log-transformed target variable.

### 9. Hyperparameter Tuning

An improved XGBoost model was trained with the following configuration:

- `n_estimators=800`
- `learning_rate=0.03`
- `max_depth=6`
- `subsample=0.8`
- `colsample_bytree=0.8`

The tuned model was evaluated on the same test set to compare its performance against the earlier models.

### 10. Feature Importance

Feature importance values were extracted from the XGBoost model and visualized using a horizontal bar chart.

This analysis helps identify which encoded vehicle characteristics contributed most to the model's predictions.

### 11. Prediction Analysis

The tuned model's predictions were converted back to the original price scale.

- Compared actual and predicted car prices.
- Created an actual-versus-predicted scatter plot.
- Added a reference line representing perfect predictions.
- Calculated prediction errors and absolute errors.
- Examined the predictions with the largest absolute errors.

### 12. Model Saving

The final tuned XGBoost model was saved as a serialized file using Joblib.

The output file is:

`used_car_price_model.pkl`

This allows the trained estimator to be loaded for potential future prediction tasks.

## 📈 Model Performance

The following results were obtained on the test set:

| Model | MAE | RMSE | R² Score |
|---|---:|---:|---:|
| Linear Regression | 0.3471 | 0.4812 | 0.6873 |
| Random Forest Regressor | 0.2491 | 0.3567 | 0.8282 |
| XGBoost Regressor | 0.2226 | 0.3226 | 0.8595 |
| Tuned XGBoost | 0.2145 | 0.3103 | 0.8699 |

*Note: MAE and RMSE are calculated on the log-transformed price target, not directly in the original currency.*

## 💡 Key Findings

- Random Forest outperformed Linear Regression on the test set.
- XGBoost achieved better results than both Linear Regression and Random Forest.
- Hyperparameter tuning further improved the XGBoost model's performance.
- The tuned XGBoost model achieved an R² score of approximately **0.87**.
- The tuned model produced the lowest MAE and RMSE among the evaluated models.
- Vehicle characteristics such as mileage, model year, brand, and engine size can help explain differences in used car prices.
- Extremely expensive luxury vehicles may be more difficult to predict accurately when relatively few comparable examples are available.

## 📝 Conclusion

This project demonstrates an end-to-end machine learning workflow for used car price prediction.

The process included data cleaning, exploratory analysis, feature engineering, log transformation, categorical encoding, model training, evaluation, and hyperparameter tuning.

Among the evaluated models, the tuned XGBoost Regressor achieved the strongest test-set performance, with an R² score of approximately 0.87.

The project also included feature importance analysis, actual-versus-predicted price visualization, prediction error analysis, and saving the final trained model.

Although the results are promising, further work could improve the reliability of predictions, particularly for expensive luxury vehicles and less common vehicle configurations.

## 🚀 Future Improvements

- Use more representative data for high-value luxury vehicles.
- Explore more robust categorical encoding techniques.
- Use a preprocessing pipeline to ensure consistent transformations during training and inference.
- Perform systematic hyperparameter optimization.
- Evaluate model performance using cross-validation.
- Report MAE and RMSE on the original price scale for easier interpretation.
- Investigate prediction errors across different vehicle brands and price ranges.
- Develop an interactive application for used car price estimation.

## 👤 Author

Created as part of my Data Science and Machine Learning project portfolio.
