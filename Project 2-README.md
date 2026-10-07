Used Car Price Prediction
📌 Project Overview

This project focuses on predicting the prices of used cars using machine learning regression techniques.

The dataset contains information about used vehicles, including brand, model, model year, mileage, fuel type, engine, transmission, exterior/interior color, accident history, and price.

The project follows an end-to-end machine learning workflow:

Data understanding

Data cleaning

Exploratory Data Analysis (EDA)

Feature engineering

Categorical encoding

Model training

Model evaluation

Hyperparameter tuning

Prediction analysis

Feature importance analysis

Model saving

📊 Dataset

The dataset contains 4,009 used-car records and 12 original features.

Important features include:

Feature	Description
brand	Car manufacturer
model	Car model
model_year	Manufacturing/model year
milage	Vehicle mileage
fuel_type	Type of fuel used
engine	Engine specifications
transmission	Transmission type
ext_col	Exterior color
int_col	Interior color
accident	Accident history
clean_title	Clean title status
price	Used car price
🧹 Data Cleaning

The dataset required several preprocessing steps:

Converted price from strings such as $10,300 into numerical values.

Converted milage from strings such as 51,000 mi. into numerical values.

Filled missing categorical values using the mode.

Extracted engine displacement in liters from the engine column.

Removed rows where engine size could not be extracted.

Removed the high-cardinality model feature before modeling.

Applied Label Encoding to categorical features.

After preprocessing, the modeling dataset contained 3,773 records.

📈 Exploratory Data Analysis

Several visualizations were created to understand the dataset and relationships between variables:

Car price distribution

Top 15 car brands by number of listings

Price distribution by brand

Mileage vs. price

Model year vs. price

Correlation heatmap

Log-transformed price distribution

XGBoost feature importance

Actual vs. predicted prices

The original price distribution was highly skewed, so a log transformation was applied:

df_clean["log_price"] = np.log1p(df_clean["price"])

⚙️ Feature Engineering

The engine specification was processed to extract engine displacement in liters.

For example:

3.7L V6 → 3.7
3.8L V6 → 3.8
2.0L I4 → 2.0


A new feature called engine_size was created from this information.

🤖 Machine Learning Models

Three regression models were trained and compared:

Linear Regression

Random Forest Regressor

XGBoost Regressor

The dataset was split into:

80% training data

20% testing data

random_state=42

📊 Model Performance
Model	R² Score	MAE	RMSE
Linear Regression	0.687	0.347	0.481
Random Forest	0.828	0.249	0.357
XGBoost	0.859	0.223	0.323
Tuned XGBoost	0.870	0.215	0.310

The Tuned XGBoost model performed the best.

🚀 XGBoost Hyperparameter Tuning

The final XGBoost model used:

XGBRegressor(
    n_estimators=800,
    learning_rate=0.03,
    max_depth=6,
    subsample=0.8,
    colsample_bytree=0.8,
    random_state=42
)


The tuned model achieved an R² score of approximately 0.87.

🔍 Feature Importance

The most important features identified by XGBoost were:

Mileage — 41.3%

Engine Size — 18.9%

Model Year — 17.5%

Brand — 6.0%

Fuel Type — 4.6%

This indicates that mileage, engine size, and model year were particularly influential in predicting used-car prices.

💰 Prediction Analysis

The model predictions were converted back from log scale into the original price scale using:

actual_prices = np.expm1(y_test)
predicted_prices = np.expm1(tuned_predictions)


An Actual vs. Predicted price visualization was also created to evaluate prediction performance.

⚠️ Limitations

The model performed well overall but struggled with extremely expensive vehicles.

For example, some vehicles priced above several hundred thousand dollars were significantly underpredicted.

This is likely because the dataset contains relatively few extremely high-value vehicles, giving the model limited examples from which to learn these price patterns.

Other limitations include:

Label encoding was used for categorical variables.

The model column was removed because of its high cardinality.

Engine extraction was based on a regular expression and resulted in some missing values.

The dataset may not represent the entire used-car market.

💾 Saved Model

The final tuned XGBoost model was saved using Joblib:

joblib.dump(
    xgb_tuned,
    "used_car_price_model.pkl"
)


The saved model file is:

used_car_price_model.pkl

🛠️ Technologies Used

Python

Google Colab

Pandas

NumPy

Matplotlib

Seaborn

Scikit-learn

XGBoost

Joblib

📁 Project Structure
Project 2/
│
├── used_car_price_prediction.ipynb
├── used_car_price_model.pkl
└── README.md

🎯 Conclusion

This project demonstrates a complete machine learning regression workflow for used-car price prediction.

After preprocessing the data and comparing multiple regression algorithms, the Tuned XGBoost model achieved the best performance with an R² score of approximately 0.87.

The project demonstrates practical skills in data cleaning, exploratory data analysis, feature engineering, machine learning, model evaluation, hyperparameter tuning, and model deployment preparation.
