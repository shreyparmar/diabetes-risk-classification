# Diabetes Risk Classification

A hands-on machine learning classification project using the **Diabetes Risk Prediction** dataset from Kaggle to predict a patient's diabetes risk category — **Low, Moderate, or High** — using demographic, lifestyle, and health-related parameters.

This is my first end-to-end machine learning project, built to apply practical concepts such as data preprocessing, exploratory data analysis, model training, evaluation, cross-validation, and hyperparameter tuning.

## Problem Definition

Build a **multiclass classification model** that predicts the `diabetes_risk` category using all available patient parameters in the dataset.

Classes:

* Low
* Moderate
* High

## Dataset

**Source:** [Kaggle — Diabetes Risk Prediction](https://www.kaggle.com/datasets/mansiaggarwal88/diabetes-risk-prediction/data)

The dataset contains approximately **15,000 records** and includes demographic, lifestyle, and health-related features.

`patient_id` is excluded because it is an identifier rather than a predictive feature.

The dataset is **synthetically generated**. The original dataset and generation script were provided by the Kaggle source; they were not created by me.

## Workflow

```text
Problem Definition
        ↓
Dataset Understanding
        ↓
Exploratory Data Analysis
        ↓
Data Preprocessing
        ↓
Train / Validation / Test Split
        ↓
Baseline Models
        ↓
Model Evaluation
        ↓
Cross-Validation
        ↓
Hyperparameter Tuning
        ↓
Final Model Evaluation
```

## Preprocessing

* Train / validation / test split with stratification
* Missing-value handling
* One-hot encoding of categorical features
* Feature scaling where appropriate
* Preprocessing fitted only on training data

## Models

The project explores:

* **Logistic Regression**
* **Decision Tree**
* **Random Forest**

Random Forest is further optimized using **GridSearchCV** and 5-fold cross-validation.

## Evaluation

The primary metric is **Macro F1 Score**, giving equal importance to all three risk categories.

Other evaluation tools include:

* Accuracy
* Precision
* Recall
* F1 Score
* Classification Report
* Confusion Matrix
* Stratified K-Fold Cross-Validation
* GridSearchCV

The final test set is kept separate and is used only for final evaluation.

## Results

Final results will be added after completing model selection and hyperparameter tuning.

| Model               | Validation Macro F1 | Validation Accuracy |
| ------------------- | ------------------: | ------------------: |
| Logistic Regression |                 TBD |                 TBD |
| Decision Tree       |                 TBD |                 TBD |
| Random Forest       |                 TBD |                 TBD |
| Tuned Random Forest |                 TBD |                 TBD |

## Project Structure

```text
diabetes-classification/
│
├── data/
│   ├── diabetes_risk.csv
│   ├── diabetes_risk_missing_values_filled.csv
│   └── generate_dataset.py
│
├── diabetes_risk-classifier.ipynb
├── feature-research.md
├── README.md
├── requirements.txt
└── .gitignore
```

## Technologies

* Python
* NumPy
* Pandas
* Matplotlib
* Scikit-learn
* Jupyter Notebook
* Git & GitHub

## Limitations

* The dataset is synthetic and does not represent a real patient population.
* Model performance must not be interpreted as clinical accuracy.
* This project is intended for **educational and machine learning purposes only**.
* The model must not be used for medical diagnosis or treatment decisions.

## Future Improvements

* Feature engineering
* Additional classification algorithms
* More systematic hyperparameter tuning
* Feature importance and model interpretation
* Model calibration
* Testing on additional datasets
* Building a prediction API or interface
* Creating a complete scikit-learn Pipeline

## Learning Goals

This project is intended to build practical experience with:

* Classification
* EDA
* Data preprocessing
* Missing-data handling
* One-hot encoding
* Feature scaling
* Model evaluation
* Cross-validation
* Hyperparameter tuning
* Model comparison
* Git and GitHub workflow

## Attribution

The dataset was obtained from **Diabetes Risk Prediction — Mansi Aggarwal** on Kaggle:

https://www.kaggle.com/datasets/mansiaggarwal88/diabetes-risk-prediction/data

The dataset and original generation code belong to their respective source/author. This repository contains my machine learning work performed using that dataset.

## Author

**Shrey**

A hands-on machine learning learning project.