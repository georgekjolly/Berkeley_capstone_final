# 🏆 Capstone Project: Credit Card Fraud Detection

## 📌 Final Report

Notebook : https://github.com/georgekjolly/Berkeley_capstone_final/blob/main/capstone-phase-1_v2.ipynb

---

### 1. Problem Statement

Credit card fraud is a growing concern that causes significant financial loss to both financial institutions and customers. Our goal is to build a machine learning model that can accurately **detect fraudulent transactions** in real time. The primary challenge is the **extreme class imbalance** — fraudulent transactions make up a very small fraction of all records. The solution must minimize false positives while capturing as many fraudulent cases as possible. This project aims to support fraud analysts by reducing manual review time and improving detection accuracy.

---

### 2. Model Outcomes or Predictions

This is a **supervised learning** problem focused on **binary classification**.

- **Objective**: Predict whether a transaction is **fraudulent (1)** or **legitimate (0)**.
- **Output**: A probability score and binary label per transaction.
- **Approach**: Test multiple supervised classifiers including Logistic Regression, Random Forest, Support Vector Classifier (SVC), and XGBoost.

---

### 3. Data Acquisition

We used a comprehensive and realistic **credit card transaction dataset** from Kaggle, which includes various transaction features and a fraud label.

- **Source**: [Kaggle - Credit Card Transactions Dataset](https://www.kaggle.com/datasets/tjverry/credit-card-transactions)
- **Records**: ~1 million+ transactions
- **Frauds**: Representing a small percentage of total transactions
- **Features**: Includes `merchant`, `category`, `amount`, `gender`, `city`, `state`, `transaction_date`, and `is_fraud`.

#### 🔍 Data Visualization

- Exploratory Data Analysis (EDA) on transaction amount, time patterns, location-based fraud hotspots
- Fraud class distribution visualization
- Correlation heatmaps to identify key predictors

---

### 4. Data Preprocessing/Preparation

**a. Data Cleaning**:
- Handled missing values in categorical fields.
- Encoded categorical features using one-hot and label encoding.
- Parsed and standardized `transaction_date`.

**b. Train-Test Split**:
- Used `train_test_split()` with `stratify=y` to maintain class distribution.
- 80% training, 20% testing.

**c. Preprocessing Steps**:
- Standardized numerical features using `StandardScaler`.
- Addressed class imbalance using **SMOTE**.
- Combined steps in a pipeline using `ImbPipeline` for clean integration.

---

### 5. Modeling

We evaluated the following models using `RandomizedSearchCV` for hyperparameter tuning:

- **Logistic Regression**: Serves as a simple, explainable baseline.
- **Support Vector Classifier (SVC)**: Handles complex boundaries.
- **XGBoost**: Gradient boosting method optimized for performance and imbalance.

---

### 6. Model Evaluation

We used the following **evaluation metrics**, with strong emphasis on **F1-score**, **precision**, and **recall**, due to the high class imbalance:

- **Accuracy**: Overall correctness
- **Recall**: True positive rate (fraud detection sensitivity)
- **Precision**: Correctness of fraud predictions
- **F1-score**: Balance between precision and recall
- **Confusion Matrix**: For understanding false positives/negatives

#### 📈 Results Summary

| Model                | Accuracy | Recall | Precision | F1 Score | False Positives |
|---------------------|----------|--------|-----------|----------|-----------------|
| Logistic Regression | 0.967    | 0.178  | 0.126     | 0.147    | 42,355          |
| SVC                 | 0.972    | 0.160  | 0.146     | 0.153    | 41,803          |
| **XGBoost**         | **0.985**| **0.224**| **0.629** | **0.330**| **28**           |

> ✅ **XGBoost** was selected as the final model due to its superior F1 score, significantly reduced false positives, and high precision — all essential for an effective fraud detection system.
