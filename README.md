# 🚜 Heavy Equipment Selling Price Prediction

## 📌 Project Overview

This project was developed as part of the **Heavy Equipment Selling Price Prediction Challenge** on Kaggle.

The objective is to build a machine learning regression model that predicts the **selling price of heavy equipment** based on equipment characteristics, transaction information, usage information, specifications, and other available features.

The project follows a complete machine learning workflow, including:

* Exploratory Data Analysis (EDA)
* Missing-value analysis
* Feature engineering
* Data preprocessing
* Multiple model training
* Model comparison
* Hyperparameter tuning
* Feature importance analysis
* Final price prediction
* Kaggle submission generation

---

## 🎯 Problem Statement

The goal of this competition is to predict the selling price of heavy equipment using historical transaction and equipment-related information.

This is formulated as a **regression problem**, where:

**Target Variable:** `TargetValue`

The model learns relationships between equipment attributes and their historical selling prices and then predicts prices for unseen test data.

---

## 📊 Dataset

The competition dataset contains:

* `train.csv` — Training data containing the target variable
* `test.csv` — Test data used for final predictions
* `metadata.csv` — Dataset metadata
* `sample_submission.csv` — Sample submission format

### Dataset Size

| Dataset  |    Rows | Columns |
| -------- | ------: | ------: |
| Training | 138,701 |      50 |
| Test     |  15,000 |      49 |

The training dataset contains the target variable `TargetValue`, while the test dataset is used for generating the final predictions.

---

## 🔍 Exploratory Data Analysis

The notebook performs several EDA steps to understand the dataset.

### Data Inspection

The dataset was examined using:

* Data types
* Number of observations
* Numerical statistics
* Categorical variables
* Missing values

### Missing Value Analysis

A missing-value analysis was performed to identify columns with a high percentage of missing observations.

Some columns contain substantial missing values, including equipment specification and configuration-related variables.

### Target Distribution

The distribution of the `TargetValue` variable was analyzed to understand the selling-price distribution.

The target was subsequently transformed using a **log transformation** during model development.

### Correlation Analysis

Correlation analysis was performed on numerical variables to investigate their relationship with the target variable.

---

## 🛠️ Feature Engineering

Several domain-inspired features were created to improve the model's ability to capture relationships in the data.

### 📅 Date-Based Features

`TransactionDate` was converted into a datetime representation and additional time-related features were created, including:

* `sale_year`
* `DateElapsed`

### 🚜 Machine Age Features

Machine age was derived from the manufacturing year and transaction year.

Additional features were created:

* `machine_age`
* `age_squared`
* `log_age`

Invalid manufacturing-year values were also handled during preprocessing.

### ⚙️ Equipment Usage Features

Equipment usage information from `OperationalHoursMeter` was incorporated into the feature engineering process.

Additional interaction features were created between:

* Date-related variables
* Machine age
* Operational hours

Examples include:

* `date_x_age`
* `date_x_hours`

---

## 🧹 Data Preprocessing

A preprocessing pipeline was developed to handle numerical and categorical variables.

### Numerical Features

Numerical features were processed using:

* Median imputation
* Standard scaling

### Categorical Features

Categorical features were automatically detected and processed through the preprocessing pipeline.

Missing-value indicator features were also created for columns containing missing values.

The preprocessing pipeline ensures that the same transformations are applied consistently to the training, validation, and test datasets.

---

## 🤖 Machine Learning Models

Three gradient-boosting-based regression models were trained and compared.

### 1. LightGBM

A `LGBMRegressor` model was trained with a large number of estimators and a low learning rate.

### 2. XGBoost

An `XGBRegressor` model was trained for nonlinear regression and later tuned using `GridSearchCV`.

### 3. CatBoost

A `CatBoostRegressor` model was also trained and evaluated.

---

## 📈 Model Comparison

The three models were evaluated using **Validation RMSE**.

The workflow compared:

```text
LightGBM
   │
   ├── Validation
   │
XGBoost
   │
   ├── Validation
   │
CatBoost
   │
   └── Validation
          ↓
    Model Comparison
```

After the initial comparison, XGBoost was further tuned to improve its validation performance.

---

## 🎛️ Hyperparameter Tuning

Hyperparameter tuning was performed using **GridSearchCV** on the XGBoost model.

The tuning process explored regularization parameters including:

* `reg_alpha`
* `reg_lambda`

The tuned XGBoost model was then compared against the previously trained models.

---

## ⭐ Feature Importance

Feature importance analysis was performed using the final tuned XGBoost model.

This analysis helps identify which original and engineered features contribute most to the model's predictions.

---

## 🏆 Final Model

After comparing the different models and performing hyperparameter tuning, the **tuned XGBoost model** was used for generating the final test predictions.

The model predictions were transformed back from the logarithmic scale using the exponential function.

The final predictions were then placed into the required Kaggle submission format.

---

## 📤 Submission

The final predictions were generated for the test dataset and saved in the competition submission format.

The submission contains:

* `TransactionID`
* Predicted `TargetValue`

---

## 🧰 Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Seaborn**
* **Scikit-learn**
* **LightGBM**
* **XGBoost**
* **CatBoost**
* **Jupyter Notebook**
* **Kaggle**

---

## 📁 Project Structure

```text
heavy-equipment-selling-price-prediction/
│
├── README.md
├── heavy_equipment_price_prediction.ipynb
├── requirements.txt
│
└── images/
    ├── target_distribution.png
    ├── missing_values.png
    ├── model_comparison.png
    └── feature_importance.png
```

> The dataset files are not included in this repository because they are provided through the Kaggle competition environment.

---

## 📓 Notebook

The complete implementation is available in:

```text
heavy_equipment_price_prediction.ipynb
```

The notebook contains the complete workflow from data loading and EDA to model training, tuning, feature importance analysis, and final prediction generation.

---

## 🌐 Kaggle

**Kaggle Competition:**
[Heavy Equipment Selling Price Prediction Challenge](https://www.kaggle.com/competitions/heavy-equipment-selling-price-prediction-challenge)

**Kaggle Notebook:**
*Add your personal Kaggle notebook link here*

---

## 📌 Key Takeaways

This project demonstrates an end-to-end machine learning regression workflow involving:

* Handling a large tabular dataset
* Exploratory data analysis
* Missing-value handling
* Feature engineering
* Numerical and categorical preprocessing
* Gradient boosting models
* Model comparison
* Hyperparameter tuning
* Feature importance analysis
* Generating competition-ready predictions

---

## 👨‍💻 Author

**Prince Patel**

Data Science | Machine Learning | Python
