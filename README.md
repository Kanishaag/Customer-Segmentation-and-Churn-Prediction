# 📡 Telco Customer Churn Prediction & Segmentation

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Machine_Learning-Scikit--Learn-orange.svg)](https://scikit-learn.org/)

Customer churn is one of the most critical challenges in the telecom sector. This end-to-end machine learning project analyzes customer behavior, builds a predictive model to flag high-risk accounts, and utilizes unsupervised learning to segment the customer base for targeted retention strategies.

---

## 🎯 Project Objectives

* **Exploratory Data Analysis (EDA):** Discover the behavioral and financial drivers behind customer attrition.
* **Predictive Modeling:** Build and optimize a robust classifier to predict churn.
* **Model Optimization:** Benchmark multiple approaches to maximize **Recall**, ensuring fewer high-risk customers are missed.
* **Customer Segmentation:** Apply unsupervised clustering to group customers by value and stability risk.
* **Business Intelligence:** Translate model metrics into actionable, data-driven retention plays.

---

## 📂 Dataset Profile

The project utilizes the **IBM Telco Customer Churn dataset**, which tracks customer demographics, account characteristics, and service subscriptions.

### Key Features Analyzed
* **Demographics & Account:** Tenure Months, Monthly Charges, Total Charges, Contract Type, Payment Method, Customer Lifetime Value (CLTV).
* **Services:** Internet Service, Technical Support.
* **Target Variable:** `Churn Label` (1 = Churned, 0 = Retained)

---

## 🛠️ Tech Stack & Libraries

* **Data Wrangling:** `Pandas`, `NumPy`, `OpenPyXL`
* **Visualization:** `Matplotlib`, `Seaborn`
* **Machine Learning:** `Scikit-learn` (Random Forest, K-Means, StandardScaler)

---

## 📈 Exploratory Data Analysis & Insights

### Key Behavioral Discoveries
* **The Critical Window:** Customers with lower tenure exhibit significantly higher churn rates.
* **Contract Friction:** Month-to-month contracts are overwhelmingly linked to higher churn compared to long-term commitments.
* **Pricing Sensitivity:** Higher monthly charges drastically escalate the risk of customer drop-off.
* **Support Anchor:** Customers who subscribe to **Technical Support** show drastically lower churn, highlighting its value as a retention tool.

---

## ⚙️ Data Preprocessing Pipeline

1. **Type Conversion:** Handled formatting anomalies by forcing `Total Charges` into a clean numeric format.
2. **Imputation:** Identified and resolved missing data gaps.
3. **Feature Clean-up:** Extracted data-leakage elements and non-predictive identifiers.
4. **Categorical Encoding:** Executed **One-Hot Encoding** across multi-class categorical variables.
5. **Validation Strategy:** Split data into stratified training and testing partitions.

---

## 🤖 Churn Prediction: Modeling & Evaluation

The core architecture relies on a tuned **Random Forest Classifier**. Because a missed churn event represents direct lost revenue, the optimization process deliberately tuned the model to favor **Recall (Class 1)** over baseline accuracy.

### Iterative Approach Comparison

| Model Architecture | Description | Accuracy | Precision (Class 1) | Recall (Class 1) | F1-Score |
| :--- | :--- | :---: | :---: | :---: | :---: |
| **Base Model** | Default Hyperparameters | 0.79 | 0.66 | 0.51 | 0.58 |
| **Approach 1** | Class Imbalance Handling (`balanced`) | 0.79 | 0.67 | 0.52 | 0.59 |
| **Approach 2** | Hyperparameter Tuning | 0.78 | 0.59 | **0.75** | 0.66 |
| **Approach 3** | Feature Importance Pruning | 0.78 | 0.60 | 0.74 | 0.66 |
| **Final Model** | **Optimized RF (300 Trees, Depth 10)** | **0.78** | **0.60** | **0.74** | **0.66** |

### 🛠️ Validation Metrics
* **Stratified K-Fold Cross-Validation:** Accuracy Mean = **0.779** | Recall Mean = **0.733**
* **ROC-AUC Analysis:** The optimized model demonstrates a strong, balanced separation threshold between active and churning classes.

---

## 📊 Feature Importance

The top features driving the model's predictions, ranked by weight:
1. **Tenure Months** (Strongest negative correlation with churn)
2. **Monthly Charges** (Strongest positive correlation with churn)
3. **Contract Type** 4. **Total Charges**
5. **Internet Service**

> **💡 Summary Insight:** A customer with **low tenure** paired with **high monthly charges** represents the maximum immediate churn risk profile.

---

## 👥 Customer Segmentation (K-Means Clustering)

Using `StandardScaler` normalized data containing tenure, monthly spend, total spend, and model-derived churn probabilities, an **Elbow Method** analysis established the optimal cluster count.

### Identified Customer Personas

* 🟢 **Budget Loyalists:** Low monthly spend, long-term tenure, and negligible churn risk. High lifetime value via stability.
* 🔴 **High-Risk Newcomers:** High monthly charges paired with minimal tenure. This cohort exhibits a severe churn probability and requires immediate customer success outreach.
* 🟡 **Premium Champions:** High-value accounts with robust spending patterns, long-term tenure, and exceptionally stable retention metrics. Ideal candidates for loyalty rewards.

---

## 🚀 Future Roadmap

* [ ] Benchmark boosting variants such as **XGBoost** and **LightGBM**.
* [ ] Build and launch an interactive web dashboard using **Streamlit**.
* [ ] Engineer a real-time inference pipeline for streaming customer profile data.

---

## 📄 Conclusion

This repository demonstrates a clean, production-minded machine learning blueprint. It successfully closes the loop between data processing, iterative model validation, unsupervised customer tiering, and strategic business takeaways.
