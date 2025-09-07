# Bank Marketing Campaign: Predictive Analytics for Term Deposit Subscription

## 📖 Project Overview

This project tackles a classic business problem in the financial sector: **optimizing marketing campaign efficiency**. Using a real-world dataset from a Portuguese banking institution, we developed a machine learning pipeline to predict whether a client will subscribe to a term deposit. The goal is to shift from a broad, scatter-shot marketing approach to a targeted, data-driven strategy, saving resources and maximizing subscription rates.

## 🎯 Business Objective

The core business challenge is the **high cost of ineffective marketing**. By blindly contacting thousands of clients, the bank wastes significant time and money on leads with a very low probability of conversion. This project provides a solution by building an intelligent system to identify the clients most likely to subscribe, allowing the marketing team to focus their efforts where they are most effective.

## 📊 Dataset

The [Bank Marketing Dataset](https://archive.ics.uci.edu/ml/datasets/Bank+Marketing) contains information on over 11,000 client contacts.
- **Features:** 16 attributes including client demographics (age, job, education), previous campaign contact details, and macroeconomic indicators.
- **Target Variable:** A binary `deposit` field indicating 'yes' or 'no' for term deposit subscription.

## 🛠️ Technical Approach

The project follows a complete CRISP-DM data science lifecycle:

1.  **Data Preprocessing & EDA:**
    - Handled unknown values and encoded categorical variables.
    - Performed correlation analysis and feature engineering (e.g., creating `duration` bins).
    - Used stratified sampling to maintain class imbalance in train/test splits.

2.  **Feature Engineering:**
    - Applied `StandardScaler` to numerical features and `OneHotEncoder` to categorical features using a `ColumnTransformer`.
    - Engineered new features like `marital/education` to capture combined demographic effects.

3.  **Model Benchmarking & Hyperparameter Tuning:**
    - Benchmarked 9 classification algorithms (Logistic Regression, Random Forest, XGBoost, etc.) on training speed and accuracy.
    - Performed rigorous hyperparameter tuning using **GridSearchCV with 3-fold Stratified Cross-Validation** to prevent overfitting and find the optimal model configuration.

4.  **Model Evaluation:**
    - Evaluated models on key metrics: **Accuracy, Precision, Recall, F1-Score, and ROC-AUC**.
    - The final model was selected based on its ability to generalize well and its high recall, ensuring we capture most potential subscribers.

## 🏆 Results & Key Findings

The **XGBoost classifier** emerged as the best-performing model:
- **Accuracy:** 82.8%
- **ROC-AUC:** 90.4%
- **Recall:** 83.7%

### 🔍 Critical Business Insights:
- **Call Duration is King:** The single most important factor is the duration of the call. Clients engaged for longer than 485 seconds had a **78% subscription rate**.
- **Model-Driven Targeting:** The predictive model can accurately score clients, allowing the bank to prioritize leads with a high probability of conversion.
- **Beyond Demographics:** While demographics are useful, the model found that client behavior (e.g., response to previous campaigns) and engagement level are more powerful predictors than age or job alone.

## 💡 Data-Driven Recommendations

1.  **Deploy the Predictive Model:** Integrate the XGBoost model into the lead management system to score clients *before* calling. Focus efforts only on the high-probability segment.
2.  **Quality Over Quantity:** Train agents to focus on **driving engagement and longer conversations** rather than maximizing call volume. Implement better call scripts to achieve this.
3.  **Implement a Call Policy:** Analysis suggests diminishing returns after multiple calls to the same client. A policy limiting contacts per client could improve overall team efficiency.
