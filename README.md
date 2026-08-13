🏠 House Price Prediction
📌 Overview

This project uses machine learning regression models to predict house prices based on various housing and socioeconomic features.

The project compares Linear Regression with Random Forest Regression and evaluates their performance using Mean Squared Error (MSE) and R² Score.

📊 Dataset

The dataset contains information about housing characteristics and their corresponding median house values.

Feature	Description
CRIM	Per-capita crime rate
ZN	Proportion of residential land
INDUS	Proportion of non-retail business acres
CHAS	Charles River proximity indicator
NOX	Nitric oxide concentration
RM	Average number of rooms per dwelling
AGE	Proportion of older buildings
DIS	Distance to employment centers
RAD	Accessibility to radial highways
TAX	Property-tax rate
PTRATIO	Pupil-teacher ratio
B	Demographic-related index
LSTAT	Percentage of lower-status population
MEDV	Median house value (target)

The dataset was checked for missing values, and no missing values were found.

🛠️ Technologies Used
Python
Google Colab
Pandas
NumPy
Matplotlib
Seaborn
Scikit-learn
🔄 Project Workflow
Loaded the housing dataset.
Explored the dataset and examined its features.
Checked for missing values.
Separated the input features from the target variable.
Split the dataset into training and testing sets.
Trained a Linear Regression model.
Trained a Random Forest Regression model.
Evaluated both models using MSE and R².
Compared model performance.
Analyzed feature importance from the Random Forest model.
🤖 Models
1. Linear Regression

Linear Regression was used as the baseline model.

Results:

MSE: 24.29
R² Score: 0.669
2. Random Forest Regression

Random Forest was then used to capture more complex relationships between the housing features and house prices.

Results:

MSE: 8.51
R² Score: 0.884
📈 Model Comparison
Model	MSE	R² Score
Linear Regression	24.29	0.669
Random Forest	8.51	0.884

Random Forest performed significantly better than Linear Regression.

The R² score improved from approximately 0.67 to 0.88, while the MSE decreased from approximately 24.29 to 8.51.

🔍 Feature Importance

The Random Forest model was also used to determine which features were most influential in predicting house prices.

Some of the important features included:

RM — average number of rooms
LSTAT — percentage of lower-status population
Other housing and socioeconomic characteristics

The notebook contains the feature-importance visualization generated during the analysis.

✅ Conclusion

The results show that Random Forest Regression significantly outperformed Linear Regression for this house-price prediction task.

The Random Forest model achieved an R² score of approximately 0.88, suggesting that it captured the relationships in the dataset much better than the baseline Linear Regression model.

The analysis also showed that variables such as RM and LSTAT were important predictors of house prices.

🚀 Possible Improvements

The model could potentially be improved further through:

Hyperparameter tuning
Cross-validation
Feature engineering
Feature selection
Testing additional regression algorithms
Comparing additional evaluation metrics
📁 Files
House-Price-Prediction/
│
├── House_Price_Prediction.ipynb
└── README.md


The .ipynb file contains the complete analysis, visualizations, model training, evaluation, and results.
