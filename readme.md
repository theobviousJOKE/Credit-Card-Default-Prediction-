# 🏦 Credit Card Default Prediction Hackathon - README

## 📘 Overview
This project was built for a credit risk modeling hackathon, where the goal was to **predict whether a customer will default on their credit card payment in the next billing cycle**. The dataset consisted of historical behavioral and demographic data of over 30,000 customers.

> **Target Variable:** `default.payment.next.month` (Binary: 1 = default, 0 = no default)

## 🎯 Objective
Develop a machine learning pipeline that:
- Accurately flags high-risk customers in advance
- Prioritizes **recall** using **F2 score** to minimize missed defaults
- Remains robust, interpretable, and deployable

---

##  Dataset Description

The dataset includes the following feature categories:

- `LIMIT_BAL`: Credit limit
- `AGE`: Customer age
- `BILL_AMT1-6`, `PAY_AMT1-6`: Monthly bill and repayment history
- `PAY_0` to `PAY_6`: Payment delay in months
- `SEX`: Gender (1 = male, 2 = female)
- `EDUCATION`: Education level
- `MARRIAGE`: Marital status

---

##  Preprocessing & Feature Engineering

###  Preprocessing Steps:
- Checked for missing/null values
- Converted categorical features to proper format
- Handled outliers using **capping** and **Winsorization**

###  Feature Engineering:
- `repayment_ratio`, `utilization_ratio`, `delinquency_streak`
- Derived trends from delay patterns and payments
- Created bins for utilization, age, and credit limit (where useful)

---

##  Exploratory Data Analysis

- **Univariate Analysis**: Histograms, KDEs to understand feature distributions
- **Bivariate Analysis**: Boxplots, countplots to explore feature-target relationships
- **Outlier Detection**: IQR and z-score methods to flag extreme behaviors

---

##  Model Training & Evaluation

###  Metric Priority
- **Primary**: F2 Score (recall-focused)
- **Secondary**: ROC AUC, Accuracy, Precision

###  Class Imbalance Handling
- Used **SMOTE** to oversample the minority class (defaults)

###  Models Trained:
- Logistic Regression
- Decision Tree
- Random Forest
- Gradient Boosting, AdaBoost
- KNN, Naive Bayes
- **XGBoost**, **LightGBM**, **CatBoost** (tuned)
- **Voting Ensemble** (XGB + LGBM + CatBoost)

###  Hyperparameter Tuning
- Done using `GridSearchCV` with **F2 scorer**
- Optimized parameters like `max_depth`, `learning_rate`, `n_estimators`, etc.

###  Best Performing Model
- **CatBoostClassifier (Fine-tuned)**
  - F2 Score: **0.5706**
  - ROC AUC: 0.745
  - Balanced recall and generalization

---

##  Final Results (Test Set)

| Model         | F2 Score | ROC AUC | Recall | Precision |
|---------------|----------|---------|--------|-----------|
| CatBoost      | 0.5706 | 0.745   | 0.64   | 0.39      |
| LightGBM      | 0.5664   | 0.755   | 0.63   | 0.40      |
| XGBoost       | 0.5338   | 0.780 | 0.56 | 0.46      |
| Voting Ensemble | 0.5331 | 0.776   | 0.55   | 0.47 |

---

##  Visualizations
- Correlation heatmap
- Class distributions pre/post SMOTE
- KDE plots for age vs credit limit
- Boxplots showing behavior differences in defaulters vs non-defaulters


---

##  Thank You!
Built with care and model discipline to optimize decision-making in credit risk 🚀

