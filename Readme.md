# 🏥 Medical Insurance Cost Prediction using Machine Learning

## 📌 Project Overview

This project aims to predict an individual's medical insurance charges based on demographic and health-related attributes using supervised machine learning.

The objective is to understand the factors affecting insurance costs and build predictive regression models capable of estimating medical charges with high accuracy.

This project follows the complete Machine Learning pipeline including:

- Problem Understanding
- Data Exploration
- Exploratory Data Analysis (EDA)
- Data Preprocessing
- Feature Engineering
- Model Building
- Model Evaluation
- Model Comparison

---

# 📂 Dataset Information

**Dataset Name**

Medical Insurance Cost Prediction Dataset

**Target Variable**

```
charges
```

**Dataset Size**

- Rows : 1338
- Columns : 7

---

# 📋 Dataset Features

| Feature | Description |
|----------|-------------|
| age | Age of the policy holder |
| sex | Gender of the individual |
| bmi | Body Mass Index |
| children | Number of dependent children |
| smoker | Smoking status |
| region | Residential region |
| charges | Medical insurance cost (Target Variable) |

---

# 🎯 Problem Statement

Predict the medical insurance charges of an individual based on personal and health-related information.

Since the target variable is continuous, this is a **Regression Problem**.

---

# 🎯 Project Objectives

- Understand the dataset thoroughly.
- Identify important factors affecting insurance charges.
- Perform detailed Exploratory Data Analysis.
- Clean and preprocess the data.
- Train multiple regression algorithms.
- Compare model performance.
- Select the best-performing model.

---

# 🛠 Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-Learn
- Jupyter Notebook

---

# Phase 1 — Problem Understanding

## Objective

Understand the business problem and identify:

- Problem Type
- Input Features
- Target Variable
- Suitable Machine Learning Algorithms

### Findings

- Problem Type → Regression
- Target Variable → charges
- Evaluation Metrics

  - MAE
  - MSE
  - RMSE
  - R² Score

---

# Phase 2 — Data Exploration

## Dataset Inspection

Performed:

- Head()
- Shape
- Info
- Describe
- Missing Value Analysis
- Duplicate Check
- Unique Values
- Target Variable Analysis

## Findings

- Dataset contains **1338 observations**
- No missing values
- One duplicate record
- Mixed numerical and categorical features
- Target variable is continuous

---

# Phase 3 — Exploratory Data Analysis (EDA)

EDA was performed to understand feature distributions, relationships, and patterns.

---

## 1. Target Variable Analysis

Performed:

- Distribution Plot
- Histogram
- Boxplot
- Mean
- Median
- Skewness
- Kurtosis

### Observation

- Insurance charges are positively skewed.
- Majority of customers have lower insurance charges.
- A few customers have very high medical expenses.
- High-value observations are genuine and not data errors.

---

## 2. Numerical Feature Analysis

Features analyzed:

- Age
- BMI
- Children
- Charges

### Findings

Age

- Nearly uniform distribution.
- No significant skewness.

BMI

- Approximately normal distribution.
- Few high BMI values.

Children

- Majority have 0–2 children.

Charges

- Strong positive skew.
- Large spread of values.

---

## 3. Outlier Analysis

Used:

- Boxplots
- IQR Method

### Findings

| Feature | Outliers |
|----------|----------|
| Age | No |
| BMI | Few |
| Children | No |
| Charges | Many |

### Decision

Outliers in insurance charges were **not removed** because they represent genuine high-cost medical cases.

Removing them would reduce the model's ability to predict expensive insurance claims.

---

## 4. Categorical Feature Analysis

Analyzed:

- Sex
- Smoker
- Region

### Key Findings

Gender

- Almost equally distributed.

Smoker

- Around 20% smokers.
- Around 80% non-smokers.

Region

- Nearly balanced across all four regions.

---

## 5. Correlation Analysis

Temporary One-Hot Encoding was performed only for EDA to calculate correlations involving categorical variables.

### Why Temporary Encoding?

Correlation calculations require numerical values.

Categorical features were temporarily converted into numeric form solely for visualization and analysis.

This encoding was **not** considered final preprocessing.

### Correlation Findings

Strongest relationships with insurance charges:

| Feature | Correlation |
|----------|------------:|
| Smoker | ~0.79 |
| Age | ~0.30 |
| BMI | ~0.20 |

Weak relationships:

- Sex
- Children
- Region

### Conclusion

Unlike the previous Student Marks dataset, this dataset contains strong predictive relationships.

---

## 6. Bivariate Analysis

Relationships analyzed:

- Age vs Charges
- BMI vs Charges
- Children vs Charges
- Smoker vs Charges
- Region vs Charges
- Sex vs Charges

### Key Findings

Smoker

The strongest predictor of insurance charges.

Age

Insurance charges generally increase with age.

BMI

Higher BMI tends to increase insurance costs.

Children

Weak relationship.

Sex

Minimal effect.

Region

Small differences among regions.

---

# Phase 4 — Data Preprocessing

Performed:

- Duplicate Removal
- Missing Value Verification
- Label Encoding
- One-Hot Encoding
- Train-Test Split
- Feature Scaling

---

## Duplicate Removal

Removed:

- 1 duplicate record

Dataset after cleaning:

- 1337 rows

---

## Missing Values

No missing values were found.

---

## Label Encoding

Applied to:

- Sex
- Smoker

Reason:

Binary categorical variables.

---

## One-Hot Encoding

Applied to:

- Region

Reason:

Avoid introducing ordinal relationships.

---

## Train-Test Split

Train:

80%

Test:

20%

Random State:

42

Reason:

Ensures unbiased model evaluation.

---

## Feature Scaling

Used:

**StandardScaler**

Reason:

- Standardizes numerical features.
- Required for Linear Regression optimization.
- Prevents features with larger values from dominating the model.

Scaling was performed **after** train-test split to avoid data leakage.

---

# Phase 5 — Linear Regression

## Model Training

The Linear Regression model was trained on the scaled training dataset.

---

## Linear Regression Results

| Metric | Value |
|----------|-------:|
| MAE | 4177.05 |
| MSE | 35,478,020.68 |
| RMSE | 5956.34 |
| R² Score | 0.81 |

---

## Interpretation

The model successfully explained approximately **81%** of the variation in insurance charges.

The predictions closely followed the actual values, indicating that the dataset contains strong linear relationships.

---

# Phase 6 — Decision Tree Regression

## Why Decision Tree?

Unlike Linear Regression, Decision Trees can learn:

- Non-linear relationships
- Feature interactions
- Complex decision boundaries

without requiring manual feature engineering.

---

## Decision Tree Results

| Metric | Value |
|----------|-------:|
| MAE | 2556.03 |
| MSE | 18,457,318.00 |
| RMSE | 4296.20 |
| R² Score | 0.90 |

---

# Model Comparison

| Metric | Linear Regression | Decision Tree |
|----------|-----------------:|--------------:|
| MAE | 4177.05 | 2556.03 |
| MSE | 35,478,020.68 | 18,457,318.00 |
| RMSE | 5956.34 | 4296.20 |
| R² Score | 0.81 | 0.90 |

---

# Model Improvement

Compared with Linear Regression:

✅ MAE reduced by approximately **39%**

✅ MSE reduced by approximately **48%**

✅ RMSE reduced by approximately **28%**

✅ R² Score improved from **0.81 → 0.90**

---

# Why Did Decision Tree Perform Better?

The Medical Insurance dataset contains several non-linear relationships.

The Decision Tree successfully captured interactions between:

- Smoking Status
- Age
- BMI

which Linear Regression cannot fully model due to its linear assumptions.

---

# Comparison with Student Marks Dataset

## Student Marks Dataset

- Weak feature-target relationships.
- Low predictive power.
- Negative/low R² scores.
- Changing algorithms provided little improvement because the dataset itself lacked informative features.

---

## Medical Insurance Dataset

- Strong relationships between features and target.
- Smoking status has a very high influence on insurance charges.
- Age and BMI also contribute significantly.
- Models achieve high predictive accuracy.

This demonstrates an important machine learning principle:

> **A high-quality dataset with meaningful feature-target relationships is often more important than using increasingly complex algorithms.**

---

# Final Conclusion

This project successfully developed regression models capable of predicting medical insurance costs.

Key achievements include:

- Complete machine learning pipeline implementation.
- Comprehensive Exploratory Data Analysis.
- Effective preprocessing and feature engineering.
- Training and evaluation of multiple regression models.
- Detailed performance comparison.

Among the evaluated models:

**Decision Tree Regressor achieved the best overall performance**, explaining approximately **90%** of the variation in insurance charges while significantly reducing prediction errors compared to Linear Regression.

The results also validate the insights discovered during EDA, confirming that smoking status, age, and BMI are the primary factors influencing medical insurance costs.

Overall, the project demonstrates the importance of data understanding, exploratory analysis, proper preprocessing, and model comparison in building accurate machine learning solutions.

---

# Future Improvements

- Random Forest Regression
- Gradient Boosting Regressor
- XGBoost Regressor
- Hyperparameter Tuning using GridSearchCV
- Cross Validation
- Model Deployment using Flask or Streamlit

---

# Author

**Ayush**

Machine Learning Regression Project

Medical Insurance Cost Prediction