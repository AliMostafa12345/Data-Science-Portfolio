# Boston House Price Prediction

## 📌 Project Overview

This project focuses on predicting house prices using machine learning techniques and the Boston Housing dataset. It explores relationships between housing characteristics and median house values and compares two regression models: Linear Regression and Random Forest Regressor.

## 🎯 Objectives

- Explore and analyze the Boston Housing dataset.
- Perform Exploratory Data Analysis (EDA).
- Visualize house price distributions and feature correlations.
- Build and evaluate machine learning regression models.
- Compare model performance using Mean Squared Error (MSE) and R² score.
- Identify important features influencing house price predictions.

## 📊 Dataset

The project uses the Boston Housing dataset, which contains information about housing characteristics and neighborhood attributes.

- **Target variable:** `MEDV` — Median value of owner-occupied homes.
- **Important features:** `RM` (average number of rooms), `LSTAT` (lower-status population percentage), and other housing-related variables.
- **Dataset file:** `boston.csv`

## 🛠️ Technologies and Libraries

- **Python** — Programming language
- **Pandas** — Data manipulation and analysis
- **NumPy** — Numerical computations
- **Matplotlib** — Data visualization
- **Seaborn** — Statistical visualization
- **Scikit-learn** — Machine learning and model evaluation
- **Google Colab** — Development environment

## 🔍 Project Workflow

### 1. Data Loading and Exploration

- Loaded the dataset using Pandas.
- Examined dataset dimensions using `df.shape`.
- Generated descriptive statistics using `df.describe()`.
- Checked missing values using `df.isnull().sum()`.

### 2. Exploratory Data Analysis (EDA)

- Created a histogram with a KDE curve to examine the distribution of median house prices.
- Generated a correlation heatmap to visualize relationships between numerical features.
- Examined patterns and potential relationships among housing variables.

### 3. Data Preparation

- Separated input features (`X`) and the target variable (`y`).
- Used `MEDV` as the target variable.
- Split the dataset into training and testing sets.
- Used an 80:20 train-test split.
- Set `random_state=42` for reproducibility.

### 4. Model Building

#### Linear Regression

Linear Regression was used as the baseline model to predict house prices based on relationships between the input features and the target variable.

#### Random Forest Regressor

A Random Forest regression model was trained using 200 decision trees to capture more complex relationships between housing characteristics and prices.

### 5. Model Evaluation

The models were evaluated using the following metrics:

- **Mean Squared Error (MSE):** Measures the average squared difference between actual and predicted values. Lower values indicate better performance.
- **R² Score:** Measures how well the model explains the variation in the target variable. Higher values generally indicate better performance.

### 6. Feature Importance

Feature importance values were extracted from the trained Random Forest model and displayed in a horizontal bar chart to identify influential predictors.

### 7. Cross-Validation

Five-fold cross-validation was performed using the R² scoring metric to examine the Random Forest model's performance across multiple data splits.

Feature standardization was applied using `StandardScaler` before the cross-validation evaluation.

## 📈 Results

The following results were obtained from the test-set evaluation:

| Model | Mean Squared Error (MSE) | R² Score |
|---|---:|---:|
| Linear Regression | 24.29 | 0.669 |
| Random Forest Regressor | 8.51 | 0.884 |

The average five-fold cross-validation R² score for the Random Forest model was approximately **0.627**.

## 💡 Key Findings

- Random Forest outperformed Linear Regression on the test set.
- Random Forest achieved a lower MSE, reducing it from 24.29 to 8.51.
- The test-set R² score improved from approximately 0.67 to 0.88.
- Feature importance analysis highlighted influential variables, including `RM` and `LSTAT`.
- The cross-validation score was lower than the test-set score, suggesting that model performance may vary across data splits.

## 📝 Conclusion

This project demonstrates how machine learning can be applied to house price prediction.

Based on the test-set results, the Random Forest Regressor performed better than Linear Regression, achieving a lower prediction error and a higher R² score. Exploratory data analysis and feature importance visualization also provided insights into relationships between housing characteristics and predicted house prices.

Further improvements could include hyperparameter tuning, more rigorous cross-validation, and evaluation using additional housing datasets.

## 🚀 Future Improvements

- Perform hyperparameter tuning using `GridSearchCV` or `RandomizedSearchCV`.
- Compare additional regression algorithms, such as Gradient Boosting.
- Investigate outliers and alternative preprocessing techniques.
- Use a consistent preprocessing pipeline during cross-validation.
- Evaluate performance on additional or more recent housing datasets.
- Develop an interactive application for house price prediction.

## 👤 Author

Created as part of my Data Science and Machine Learning project portfolio.
