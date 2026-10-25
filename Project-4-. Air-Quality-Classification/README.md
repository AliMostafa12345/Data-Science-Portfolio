
# Air Quality Classification Using Machine Learning

## Project Overview

This project focuses on developing a machine learning classification model to categorize air quality based on six numerical input features.

Multiple classification algorithms are trained and evaluated to determine which model performs best on the dataset. The project includes data preparation, model comparison, performance evaluation, confusion matrix visualization, and feature importance analysis.

The **Random Forest Classifier** achieved the best performance, with approximately **96.48% test accuracy**.

---

## Problem Statement

Air quality classification can help organize environmental measurements into distinct categories for analysis and monitoring.

The objective of this project is to build a supervised machine learning model that learns patterns from numerical environmental features and predicts one of four air quality classes.

The project demonstrates how classification algorithms can be applied to structured numerical data to identify patterns and make predictions.

---

## Project Objectives

- Explore and examine the air quality dataset.
- Prepare the dataset for machine learning.
- Identify the distribution of the target classes.
- Train and compare multiple classification algorithms.
- Evaluate model performance using accuracy, precision, recall, and F1-score.
- Identify the best-performing classification model.
- Visualize classification results using a confusion matrix.
- Analyze feature importance using the Random Forest model.
- Save the trained model for potential future use.

---

## Dataset Description

The dataset contains **1,845 records**, six numerical input features, and one target variable representing air quality categories.

| Dataset Attribute | Description |
|---|---|
| Total records | 1,845 |
| Input features | 6 |
| Target variable | `Air_Quality` |
| Number of classes | 4 |
| Feature data type | Integer |
| Missing values | None reported in the inspected dataset |

### Input Features

The six input columns are named generically because descriptive feature names are not provided in the notebook.

- `Feature_1`
- `Feature_2`
- `Feature_3`
- `Feature_4`
- `Feature_5`
- `Feature_6`

### Target Variable

The target variable is `Air_Quality`, which contains four distinct classes: 1, 2, 3, and 4.

The observed class distribution is:

| Air Quality Class | Number of Records |
|---|---:|
| Class 1 | 595 |
| Class 2 | 515 |
| Class 3 | 195 |
| Class 4 | 540 |
| **Total** | **1,845** |

Class 3 has fewer records than the other classes, making class-specific evaluation important in addition to overall accuracy.

*Note: The dataset does not provide descriptive meanings for the six features or definitions for the four air quality categories. Their physical interpretation cannot be established from the notebook alone.*

---

## Technologies and Libraries

- **Python** — Programming language
- **Pandas** — Data loading, inspection, and manipulation
- **Matplotlib** — Data visualization
- **Scikit-learn** — Classification, data splitting, and model evaluation
- **Joblib** — Saving the trained model

---

## Machine Learning Workflow

### 1. Data Loading and Exploration

The dataset is loaded into a Pandas DataFrame.

Initial exploration includes:

- Inspecting sample records.
- Examining dataset dimensions and data types.
- Generating descriptive statistics.
- Checking the target class distribution.
- Inspecting the dataset for missing values.

The feature columns are assigned descriptive placeholder names, from `Feature_1` through `Feature_6`, and the target column is named `Air_Quality`.

### 2. Feature and Target Separation

The six numerical input features are separated from the target variable.

- **Features (X):** Six numerical input columns.
- **Target (y):** Four-class `Air_Quality` variable.

### 3. Train-Test Split

The dataset is divided into training and testing subsets using an 80:20 split.

Stratified sampling is applied to preserve the relative class distribution in both subsets.

| Subset | Records |
|---|---:|
| Training set | 1,476 |
| Testing set | 369 |
| Total | 1,845 |

The split uses `random_state=42` to support reproducibility.

### 4. Model Training and Comparison

Three classification algorithms are trained and evaluated:

- **Logistic Regression:** A linear classification algorithm used as a baseline.
- **Decision Tree Classifier:** A tree-based model that learns decision rules from the input features.
- **Random Forest Classifier:** An ensemble of decision trees that combines predictions to improve classification performance.

Each model is evaluated on the same test set to make the results comparable.

### 5. Model Evaluation

The following metrics are used to evaluate classification performance:

- **Accuracy:** The proportion of correctly classified records.
- **Precision:** The proportion of predicted class members that belong to the actual class.
- **Recall:** The proportion of actual class members correctly identified.
- **F1-score:** The harmonic mean of precision and recall.

A confusion matrix is also generated to examine correct and incorrect predictions across the four classes.

### 6. Feature Importance Analysis

The Random Forest model's `feature_importances_` attribute is used to rank the six input features.

A horizontal bar chart visualizes their relative importance according to the fitted model.

These scores indicate how much each feature contributes to the forest's split-based predictive process. They do not establish causation or necessarily represent the real-world importance of an environmental variable.

### 7. Model Saving

After training, the selected Random Forest model is saved as `air_quality_model.pkl` using Joblib.

This preserves the fitted classifier for potential reuse.

---

## Models and Performance

All three models were evaluated on the same test set containing 369 records.

| Model | Test Accuracy |
|---|---:|
| Logistic Regression | 90.79% |
| Decision Tree Classifier | 93.22% |
| Random Forest Classifier | **96.48%** |

The Random Forest Classifier achieved the highest test accuracy among the three evaluated models.

---

## Detailed Performance of the Best Model

The Random Forest model achieved the following class-wise results:

| Class | Precision | Recall | F1-Score | Support |
|---|---:|---:|---:|---:|
| Class 1 | 1.00 | 0.98 | 0.99 | 119 |
| Class 2 | 0.95 | 0.96 | 0.96 | 103 |
| Class 3 | 0.93 | 0.95 | 0.94 | 39 |
| Class 4 | 0.95 | 0.95 | 0.95 | 108 |
| **Macro Average** | **0.96** | **0.96** | **0.96** | **369** |
| **Weighted Average** | **0.97** | **0.96** | **0.96** | **369** |

### Performance Highlights

- Overall test accuracy reached approximately 96.48%.
- Class 1 achieved an F1-score of 0.99.
- Class 2 achieved an F1-score of 0.96.
- Class 3 achieved an F1-score of 0.94.
- Class 4 achieved an F1-score of 0.95.
- The model demonstrated strong precision and recall across all four classes on the held-out test set.

Although Class 3 has fewer observations, the model achieved a recall of 0.95 for this class.

These results reflect one stratified train-test split and do not guarantee the same performance on new or independently collected data.

---

## Visualizations

### 1. Confusion Matrix

The confusion matrix compares actual and predicted air quality classes.

It helps identify which categories are correctly classified and which categories are most frequently confused with one another.

### 2. Feature Importance Chart

The feature importance chart ranks the six input features according to their importance scores in the trained Random Forest model.

This visualization provides an overview of which features contributed most to the model's decision-making process.

---

## Key Findings

- Random Forest outperformed Logistic Regression and the Decision Tree Classifier on the test set.
- The highest test accuracy was approximately 96.48%.
- The model achieved strong precision, recall, and F1-scores across all four target classes.
- The dataset contains an unequal distribution of class labels, with Class 3 being the least represented.
- Feature importance analysis provides a way to examine the relative contribution of the input features.
- The project demonstrates a complete classification workflow, from data exploration through model evaluation and saving.

---

## Conclusion

This project demonstrates the application of supervised machine learning to a four-class air quality classification problem.

Three classification algorithms were compared, and the Random Forest Classifier achieved the best performance, with **96.48% accuracy on the held-out test set**.

The project also includes class-wise evaluation, confusion matrix visualization, feature importance analysis, and model persistence.

Overall, the results demonstrate the potential of tree-based ensemble methods for classifying structured numerical data. Further validation on independent datasets and clearer definitions of the input features and target categories would be valuable before drawing real-world environmental conclusions.

---

## Limitations

- The input features have generic names, so their physical and environmental meanings are unclear.
- The definitions and severity levels associated with the four target classes are not documented in the notebook.
- Evaluation uses a single train-test split rather than independent external validation.
- The dataset has an unequal distribution of target classes.
- High test accuracy alone does not establish generalization to other datasets or environmental conditions.

