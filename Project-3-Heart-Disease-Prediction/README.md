
# Heart Disease Prediction Using Machine Learning

## Project Overview

This project focuses on building a machine learning classification model to predict the presence or absence of heart disease based on patient medical attributes.

Using Python and Scikit-learn, multiple classification algorithms are trained and evaluated to identify a suitable predictive model. The project follows a complete machine learning workflow, including data preparation, model comparison, feature scaling, hyperparameter tuning, model evaluation, and prediction on new patient data.

The final model uses Logistic Regression with hyperparameter tuning through GridSearchCV and achieves approximately **85.19% test accuracy**.

---

## Problem Statement

Heart disease is a major health concern, and identifying potential risk patterns from clinical measurements can support research and preliminary risk assessment.

The objective of this project is to develop a supervised machine learning classification model that learns from patient medical data and predicts whether heart disease is present or absent.

This project is intended for educational and analytical purposes and is not a substitute for professional medical diagnosis.

---

## Project Objectives

- Explore and prepare the heart disease dataset.
- Identify the relationship between medical attributes and the target variable.
- Train and compare multiple classification algorithms.
- Improve Logistic Regression using feature scaling and hyperparameter tuning.
- Evaluate model performance using classification metrics.
- Visualize model performance with a confusion matrix and ROC curve.
- Examine feature importance using Logistic Regression coefficients.
- Save the trained model for future predictions.
- Test the model using an example patient record.

---

## Dataset Description

The project uses the `Heart_Disease_Prediction.csv` dataset.

According to the notebook summary, the dataset contains **270 patient records and 13 input features**, along with a target column indicating the presence or absence of heart disease.

### Input Features

The dataset includes the following medical attributes:

| Feature | Description |
|---|---|
| Age | Patient's age |
| Sex | Encoded sex category |
| Chest pain type | Category of chest pain |
| BP | Blood pressure |
| Cholesterol | Cholesterol level |
| FBS over 120 | Fasting blood sugar indicator |
| EKG results | Electrocardiogram results |
| Max HR | Maximum heart rate |
| Exercise angina | Exercise-induced angina indicator |
| ST depression | ST depression measurement |
| Slope of ST | Slope of the ST segment |
| Number of vessels fluro | Number of major vessels identified by fluoroscopy |
| Thallium | Thallium test result category |

**Target Variable:** `Heart Disease`

The target variable is encoded using Scikit-learn's `LabelEncoder` before model training.

*Note: Refer to the dataset documentation for the exact meaning and coding of each feature.*

---

## Technologies and Libraries

The project uses the following tools and Python libraries:

- **Python** — Programming language
- **Google Colab** — Notebook-based development environment
- **Pandas** — Data loading and manipulation
- **NumPy** — Numerical computing
- **Matplotlib** — Data visualization
- **Scikit-learn** — Model training, preprocessing, tuning, and evaluation
- **Joblib** — Saving the trained machine learning pipeline

---

## Machine Learning Workflow

### 1. Data Loading and Exploration

The dataset is loaded into a Pandas DataFrame.

Initial exploration includes:

- Inspecting the first few records.
- Examining dataset dimensions and column information.
- Checking the distribution of the target variable.

### 2. Data Preprocessing

The target column, `Heart Disease`, is encoded using `LabelEncoder`.

The dataset is then divided into:

- **Features (X):** The 13 medical input variables.
- **Target (y):** The encoded heart disease label.

The data is split into training and testing sets using an 80:20 ratio. Stratified sampling is applied to preserve the target class distribution.

| Dataset | Number of Records |
|---|---:|
| Training set | 216 |
| Testing set | 54 |
| Total | 270 |

The split uses `random_state=42` to make the experiment reproducible.

### 3. Model Training and Comparison

Four classification algorithms are trained and evaluated:

- Logistic Regression
- Decision Tree Classifier
- Random Forest Classifier
- Support Vector Machine (SVM)

Accuracy and classification reports are used to compare their performance.

### 4. Feature Scaling

A `StandardScaler` is combined with Logistic Regression in a Scikit-learn Pipeline.

Feature scaling standardizes the input variables and is particularly useful for distance-based and linear optimization algorithms.

### 5. Hyperparameter Tuning

GridSearchCV is used to tune the Logistic Regression model through five-fold cross-validation.

The following parameters are explored:

- **C:** `0.01`, `0.1`, `1`, `10`, `100`
- **Solver:** `liblinear`, `lbfgs`

The best configuration reported by the notebook is:

- `C = 0.01`
- `solver = lbfgs`

The selected model is then evaluated on the held-out test set.

### 6. Model Evaluation

The final model is evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion matrix
- ROC curve
- Area Under the ROC Curve (ROC-AUC)

These metrics provide a broader view of model performance than accuracy alone.

### 7. Feature Importance Analysis

The absolute values of the trained Logistic Regression coefficients are used to rank the input features by coefficient magnitude.

A horizontal bar chart visualizes the relative magnitude of these coefficients.

**Important:** Absolute coefficient magnitude indicates the strength of a coefficient in the fitted model, not whether a feature increases or decreases risk. The interpretation also depends on feature scaling and encoding.

### 8. Model Saving

The best fitted pipeline is saved as:

`heart_disease_model.pkl`

The saved pipeline includes the fitted scaler and Logistic Regression model, allowing new records to pass through the same preprocessing and prediction steps.

### 9. Prediction on New Patient Data

An example patient record is created using a Pandas DataFrame with all 13 required features.

The saved-in-memory best model predicts one of two outcomes:

- Presence of Heart Disease
- Absence of Heart Disease

The example record in the notebook produces the output **"Prediction: Absence of Heart Disease."**

This is an illustrative model prediction, not a medical conclusion.

---

## Model Performance

### Classification Accuracy

The following results were obtained on the 54-record test set before hyperparameter tuning:

| Model | Test Accuracy |
|---|---:|
| Logistic Regression | 85.19% |
| Decision Tree | 79.63% |
| Random Forest | 81.48% |
| Support Vector Machine (SVM) | 74.07% |

### Final Tuned Model

The best Logistic Regression configuration achieved the following results:

| Metric | Score |
|---|---:|
| Cross-validation accuracy | 85.63% |
| Test accuracy | 85.19% |
| Class 0 precision | 0.87 |
| Class 0 recall | 0.87 |
| Class 0 F1-score | 0.87 |
| Class 1 precision | 0.83 |
| Class 1 recall | 0.83 |
| Class 1 F1-score | 0.83 |

The class labels `0` and `1` correspond to the encoded target categories. The original dataset's label mapping should be checked when interpreting these class-specific metrics.

The final model demonstrates reasonably balanced precision and recall across both classes on this test split.

*Note: These results reflect a single train-test split of a relatively small dataset. They do not establish clinical reliability or guarantee performance on other populations.*

---

## Visualizations

The notebook generates the following visualizations:

### 1. Confusion Matrix

Displays the number of correct and incorrect predictions for each class, helping identify false positives and false negatives.

### 2. ROC Curve

Shows the relationship between the true positive rate and false positive rate at different classification thresholds. The ROC-AUC score summarizes the model's ability to distinguish between the two classes.

### 3. Feature Importance Chart

Displays the absolute Logistic Regression coefficients to compare the relative magnitude of the model's feature coefficients.

---

## Project Structure

The repository can be organized as follows:

```text
Heart_Disease_Classification/
│
├── Classification Project 1.ipynb
├── Heart_Disease_Prediction.csv
├── heart_disease_model.pkl
└── README.md
```

The notebook and CSV file are the primary project inputs. The `.pkl` file is generated when the model-saving cell is executed.

Adjust the filenames in this structure to match the actual files in your GitHub repository.

---

## Installation and Requirements

Install the required libraries using pip:

```bash
pip install pandas numpy matplotlib scikit-learn joblib
```

The notebook was developed in Google Colab, where many of these libraries are already available.

---

## How to Run the Project

### Option 1: Google Colab

1. Open the notebook in Google Colab.
2. Upload the dataset or clone the project repository.
3. Update the CSV file path if necessary.
4. Run the notebook cells in order.
5. Review the classification reports, visualizations, and model evaluation results.
6. Run the prediction cell to test the model on the example patient record.

### Option 2: Run Locally

1. Clone or download the GitHub repository.
2. Install the required Python libraries.
3. Place the CSV file in the expected location or update the file path.
4. Open the notebook in Jupyter Notebook or JupyterLab.
5. Execute the cells sequentially.

The original notebook uses the Google Colab path:

```python
df = pd.read_csv(
    "/content/Heart_Disease_Classification/Heart_Disease_Prediction.csv"
)
```

Update this path when running the project outside Google Colab.

---

## Loading the Saved Model

After running the notebook and generating `heart_disease_model.pkl`, the fitted pipeline can be loaded with Joblib.

```python
import joblib

model = joblib.load("heart_disease_model.pkl")
```

To generate a prediction, provide a Pandas DataFrame containing the same 13 feature columns used during training.

```python
prediction = model.predict(new_patient)

if prediction[0] == 1:
    print("Prediction: Presence of Heart Disease")
else:
    print("Prediction: Absence of Heart Disease")
```

Ensure that the input columns, order, data types, and categorical encodings match the training data.

The mapping between encoded labels and the original target labels should also be verified before using the output in downstream applications.

---

## Key Learnings

Through this project, the following machine learning concepts are demonstrated:

- Supervised learning for binary classification.
- Target variable encoding and stratified train-test splitting.
- Comparison of multiple classification algorithms.
- Feature scaling with Scikit-learn Pipelines.
- Hyperparameter optimization using GridSearchCV.
- Model evaluation using classification metrics and ROC analysis.
- Interpretation of Logistic Regression coefficients.
- Model persistence using Joblib.
- Generating predictions for new input records.

---

## Future Improvements

Potential extensions to the project include:

- Perform more extensive exploratory data analysis.
- Check for missing values, duplicate records, and unusual values.
- Compare additional classification algorithms.
- Evaluate models using repeated stratified cross-validation.
- Investigate class-specific errors and threshold selection.
- Improve coefficient interpretation and compare it with model-agnostic feature importance methods.
- Add a simple web interface using Streamlit or Flask.
- Create a reproducible training script and a separate prediction script.
- Add automated tests for input validation and model predictions.

---

## Conclusion

This project demonstrates an end-to-end machine learning workflow for predicting heart disease status from clinical attributes.

Four classification algorithms were compared, and Logistic Regression was selected for further development. After standardization and five-fold GridSearchCV tuning, the final model achieved **85.19% accuracy on the held-out test set**.

The project also demonstrates model evaluation, coefficient-based feature analysis, visualization, model saving, and prediction on new patient data.

Overall, it provides a practical introduction to applying classification techniques to structured medical data.

---

## Disclaimer

This project is intended for educational and research purposes only. The model has not been established as a clinically validated diagnostic tool and must not be used to diagnose heart disease, guide treatment, or replace advice from qualified healthcare professionals.

---

## Author

**Your Name**

- GitHub: [Your GitHub Profile](https://github.com/your-username)

