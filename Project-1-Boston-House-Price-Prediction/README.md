# Boston House Price Prediction
Project Overview

This project focuses on predicting house prices using machine learning techniques and the Boston Housing dataset. It explores the relationships between housing characteristics and median house values and compares the performance of Linear Regression and Random Forest regression models.

Objectives
Explore and analyze the Boston Housing dataset.
Perform exploratory data analysis (EDA).
Visualize the distribution of house prices and correlations between features.
Build and evaluate regression models.
Compare model performance using Mean Squared Error (MSE) and R² score.
Identify important features influencing house price predictions.
Dataset

The project uses the Boston Housing dataset, which contains information about housing characteristics and neighborhood attributes.

Target variable: MEDV — Median value of owner-occupied homes.
Important features: RM (average number of rooms), LSTAT (lower-status population percentage), and other housing-related variables.

The dataset is loaded from a CSV file named boston.csv.

Technologies and Libraries
Python
Pandas
NumPy
Matplotlib
Seaborn
Scikit-learn
Google Colab
Project Workflow
1. Data Loading and Exploration

The dataset was loaded using Pandas. Initial exploration included examining its dimensions, generating descriptive statistics, and checking for missing values.

2. Exploratory Data Analysis

Data visualization was performed using Matplotlib and Seaborn.

A histogram with a KDE curve was used to examine the distribution of median house prices.
A correlation heatmap was created to explore relationships between numerical features.
3. Data Preparation

The dataset was divided into input features and the target variable.

Features (X): All columns except MEDV.
Target (y): MEDV.
Train-test split: 80% training data and 20% testing data.
Random state: 42 for reproducibility.
4. Model Building

Two machine learning regression models were trained.

Linear Regression

Used as a baseline model to predict house prices based on linear relationships between the input features and the target variable.

Random Forest Regressor

An ensemble learning model using 200 decision trees to capture more complex relationships between housing characteristics and prices.

5. Model Evaluation

The models were evaluated using two metrics:

Mean Squared Error (MSE): Measures the average squared difference between actual and predicted values. Lower values indicate better performance.
R² Score: Measures how well the model explains variation in the target variable. Higher values generally indicate better performance.
6. Feature Importance

Feature importance values were extracted from the Random Forest model and visualized using a horizontal bar chart to identify influential predictors.

7. Cross-Validation

Five-fold cross-validation was performed to evaluate the Random Forest model across multiple data splits. The average R² score was calculated to assess model performance.

Results

The following results were obtained from the test-set evaluation:

Model	Mean Squared Error (MSE)	R² Score
Linear Regression	24.29	0.669
Random Forest Regressor	8.51	0.884

The average five-fold cross-validation R² score for the Random Forest model, using standardized features, was approximately 0.627.

Key Findings
Random Forest outperformed Linear Regression on the test set.
The Random Forest model achieved a lower MSE, decreasing from 24.29 to 8.51.
The test-set R² score improved from approximately 0.67 to 0.88.
Feature importance analysis highlighted influential variables, including RM and LSTAT.
The cross-validation score was lower than the test-set score, indicating that model performance may vary across data splits and should be investigated further.
Conclusion

This project demonstrates the application of machine learning techniques to house price prediction.

Based on the test-set results, the Random Forest Regressor performed better than Linear Regression, achieving lower prediction error and a higher R² score. Exploratory data analysis and feature importance visualization also helped reveal relationships between housing characteristics and predicted house prices.

Further improvements could include hyperparameter tuning, more rigorous cross-validation, and testing on additional housing datasets.

Future Improvements
Optimize model parameters using hyperparameter tuning.
Compare additional regression algorithms, such as Gradient Boosting.
Investigate outliers and alternative data preprocessing techniques.
Use a consistent preprocessing pipeline during cross-validation.
Evaluate performance on additional or more recent housing datasets.
Develop an interactive application for house price prediction.
Author

Created as part of my Data Science and Machine Learning project portfolio.
