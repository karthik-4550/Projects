# Semiconductor Manufacturing — Signal Prediction & Yield Classification

![Python](https://img.shields.io/badge/Python-3.x-blue) ![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-orange) ![Status](https://img.shields.io/badge/Status-Completed-brightgreen) ![Dataset](https://img.shields.io/badge/Dataset-Kaggle-orange)

## Project Overview

Binary classification project on real semiconductor manufacturing sensor data to predict product yield outcomes (Pass/Fail). The dataset presents a classic imbalanced classification challenge — a critical problem in manufacturing where correctly identifying rare passing units is as important as overall accuracy.

---

## Business / Research Question

> **Can sensor signal data from the semiconductor manufacturing process predict whether a unit will Pass or Fail quality inspection — and how do we handle extreme class imbalance to make the model practically useful?**

In semiconductor manufacturing, a false negative (predicting Fail when the unit actually Passes) leads to scrapping good product and direct revenue loss. This makes precision and recall on the minority class the real success metric — not overall accuracy.

---

## Dataset

- **Source:** Kaggle — SECOM Semiconductor Manufacturing Dataset
- **Size:** 1,567 rows × 592 columns (sensor signal features)
- **Target Variable:** `Pass/Fail` — binary (1,463 Fail vs. 104 Pass)
- **Challenge:** Severe class imbalance (~93.4% Fail, ~6.6% Pass)

---

## Tools & Libraries

| Tool | Purpose |
|------|---------|
| Python | Core programming language |
| Pandas / NumPy | Data cleaning & preprocessing |
| Scikit-learn | ML models & evaluation |
| Imbalanced-learn (SMOTE) | Class imbalance handling |
| Matplotlib / Seaborn | EDA visualisations |

---

## Data Preprocessing

- **Missing values:** Dropped columns with >50% missing data; imputed remaining missing values with column median
- **Feature reduction:** Dropped `Time` column (non-predictive identifier)
- **Class imbalance:** Applied **SMOTE (Synthetic Minority Oversampling Technique)** to training data → balanced to 1,170 samples per class
- **Univariate analysis:** Several features showed highly skewed distributions
- **Correlation analysis:** No individual feature showed strong linear correlation (|r| > 0.2) with target — confirming the need for ensemble/non-linear models

---

## Models Trained & Results

| Model | Overall Accuracy | Pass Precision | Pass Recall | Notes |
|-------|-----------------|---------------|-------------|-------|
| Random Forest | 92.99% | 0.00 | 0.00 | Failed to predict minority class entirely |
| **SVC (Support Vector Classifier)** | **93.63%** | **1.00** | 0.0476 | Perfect precision on Pass class |
| Gaussian Naive Bayes | 25.48% | 0.0723 | 0.8571 | High recall but very low precision |

**Best model: SVC** — achieved the highest overall accuracy (93.63%) and perfect precision (1.0) on the minority Pass class. Every unit it predicts as Pass is actually a Pass — critical in manufacturing to avoid wrongly approving defective units.

---

## Key Findings

- High-dimensional sensor data (592 features) with heavy missingness requires aggressive preprocessing before modelling
- Overall accuracy is a **misleading metric** for imbalanced datasets — a model predicting all Fail achieves ~93% accuracy while being completely useless
- SMOTE effectively balanced the training set but did not fully resolve the recall challenge for the minority class
- SVC's perfect Pass precision makes it the most production-viable model — it never wrongly approves a failing unit, though it misses most passing ones
- Random Forest, despite its popularity, completely failed on the minority class without further tuning

---

## Insights & Next Steps

- **Threshold tuning:** Adjusting SVC decision threshold could improve Pass recall while maintaining acceptable precision
- **Advanced feature selection:** PCA or recursive feature elimination (RFE) could reduce the 592-feature space and improve model generalisation
- **Gradient Boosting (XGBoost/LightGBM):** Likely to outperform on this type of structured, high-dimensional sensor data
- **Cost-sensitive learning:** Assigning higher misclassification cost to the Pass class could directly optimise for the business objective

---

## How to Run

```bash
# Clone the repository
git clone https://github.com/karthik-4550/Projects.git

cd Projects

# Install dependencies
pip install pandas numpy scikit-learn imbalanced-learn matplotlib seaborn

# Open notebook
jupyter notebook Signal_prediction_analysis.ipynb
```

---

## About the Author

**Karthik K** — Data Analyst | Chennai, India
[LinkedIn](https://linkedin.com/in/karthik-k-4525k005) | [GitHub](https://github.com/karthik-4550)
