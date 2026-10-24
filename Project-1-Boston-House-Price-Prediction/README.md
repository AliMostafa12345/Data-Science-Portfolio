🏡 Boston House Price Prediction
📌 Project Overview

This project focuses on predicting house prices using machine learning techniques and the Boston Housing dataset. It explores the relationships between housing characteristics and median house values, applies exploratory data analysis (EDA), and compares the performance of two regression models: Linear Regression and Random Forest Regressor.

The goal is to understand which features influence house prices and evaluate how effectively machine learning models can predict housing values.

🎯 Objectives
Explore and understand the Boston Housing dataset.
Perform exploratory data analysis using statistical summaries and visualizations.
Identify relationships between housing features and median house prices.
Build and evaluate Linear Regression and Random Forest regression models.
Compare model performance using Mean Squared Error (MSE) and R² score.
Analyze feature importance to identify influential predictors.
📊 Dataset

The project uses the Boston Housing dataset, which contains housing-related information and neighborhood characteristics.

Target variable: MEDV — Median value of owner-occupied homes.
Features: Housing and neighborhood variables, including RM (average number of rooms) and LSTAT (lower-status population percentage), among others.

The dataset is loaded from a CSV file named boston.csv.

Note: The dataset should be placed in the appropriate location or its file path should be updated before running the notebook. The original Boston Housing dataset has also been deprecated in some machine learning libraries due to ethical concerns about certain variables, so its limitations should be considered when interpreting results.
🛠️ Technologies and Libraries
Python — Programming language
Pandas — Data loading and manipulation
NumPy — Numerical operations
Matplotlib — Data visualization
Seaborn — Statistical visualization
Scikit-learn — Machine learning, preprocessing, model training, and evaluation
Google Colab — Development environment
🔍 Project Workflow
1. Data Loading and Exploration
Loaded the dataset using Pandas.
Examined dataset dimensions using df.shape.
Generated descriptive statistics using df.describe().
Checked for missing values using df.isnull().sum().
2. Exploratory Data Analysis (EDA)

Created visualizations to understand the data:

Distribution plot: Used a histogram with a KDE curve to examine the distribution of median house prices.
Correlation heatmap: Visualized correlations between numerical features to investigate relationships among housing variables.
3. Data Preparation
Selected all columns except MEDV as input features.
Used MEDV as the target variable.
Split the dataset into training and testing sets using an 80:20 ratio.
Set random_state=42 to make the train-test split reproducible.
4. Model Building

Two regression algorithms were trained and evaluated.

Linear Regression

Used as a baseline model to estimate house prices based on a linear relationship between the input features and target variable.

Random Forest Regressor

Used an ensemble of decision trees with n_estimators=200 to capture more complex relationships in the data.

5. Model Evaluation

The models were evaluated using:

Mean Squared Error (MSE): Measures the average squared prediction error. Lower values indicate better performance.
R² Score: Measures how much of the variation in the target variable is explained by the model. Higher values generally indicate better performance.
6. Feature Importance

A horizontal bar chart was generated using the Random Forest model's feature importance values to identify which input variables contributed most to its predictions.

7. Cross-Validation

Five-fold cross-validation was performed using cross_val_score with the R² scoring metric to assess model performance across multiple data splits.

The features were standardized using StandardScaler before this evaluation.

📈 Results

The following results were obtained from the notebook's train-test evaluation:

Model	Mean Squared Error (MSE)	R² Score
Linear Regression	24.29	0.669
Random Forest Regressor	8.51	0.884
Key Findings
Random Forest achieved a higher R² score than Linear Regression on the test set.
Random Forest reduced the test-set MSE from approximately 24.29 to 8.51.
The test-set R² score improved from approximately 0.67 to 0.88.
The feature importance analysis highlighted influential variables, including RM and LSTAT.
The five-fold cross-validation R² score for the Random Forest model, using the scaled features, averaged approximately 0.627.

The cross-validation result differs from the test-set score. This suggests that model performance may vary across data splits and deserves further investigation.

💡 Conclusion

This project demonstrates how machine learning can be applied to a housing price prediction problem.

Based on the test-set results, the Random Forest Regressor outperformed Linear Regression, achieving a lower Mean Squared Error and a higher R² score. Feature importance analysis also provided insight into which housing and neighborhood characteristics influenced the model's predictions.

Potential improvements include hyperparameter tuning, more rigorous cross-validation, and evaluation on alternative datasets.

🚀 Future Improvements
Perform hyperparameter tuning using GridSearchCV or RandomizedSearchCV.
Compare additional regression algorithms, such as Gradient Boosting and XGBoost.
Investigate outliers and evaluate alternative preprocessing methods.
Improve validation methodology by using a pipeline and consistent preprocessing within each cross-validation fold.
Evaluate model generalization using additional or more recent housing data.
Develop an interactive application for predicting house prices.

👤 Author

Created as part of my Data Science and Machine Learning project portfolio.

⭐ If you find this project useful, feel free to explore the repository and share your feedback.
