# Car Insurance Claim Prediction

## Project Overview
This project predicts whether a car insurance policyholder will file a claim based on demographic, behavioral, and vehicle-related features. The goal is to help insurance companies identify high-risk customers and price policies more accurately.

## Research Question
**Can we predict whether a car insurance policyholder will file a claim using features such as driving experience, age, vehicle type, and credit score?**

## Dataset
- **Source:** [Car Insurance Data — Kaggle (sagnik1511)](https://www.kaggle.com/datasets/sagnik1511/car-insurance-data)
- **Size:** ~10,000 rows
- **Target Variable:** `OUTCOME` — 1 if a claim was filed, 0 if not
- **Key Features:** AGE, GENDER, DRIVING_EXPERIENCE, VEHICLE_TYPE, CREDIT_SCORE, VEHICLE_OWNERSHIP, ANNUAL_MILEAGE

> **Note:** The dataset CSV is not included in this repository due to Kaggle's terms of use. Download it from the link above and place it in the project root as `Car_Insurance_Claim.csv` before running the notebook.

## Repository Structure
```
├── README.md
├── capstone_eda.ipynb        # Main EDA and baseline model notebook
└── Car_Insurance_Claim.csv   # Download from Kaggle (not committed)
```

## Methodology
1. **Data Cleaning** — handled missing values via median/mode imputation, removed duplicates
2. **EDA** — visualized distributions, claim rates by category, correlations
3. **Feature Engineering** — encoded categorical variables, created AGE_GROUP and EXP_RISK ordinal features
4. **Baseline Modeling** — Logistic Regression with StandardScaler

## Results
### EDA Findings
- Dataset has a **38.98% claim rate**, indicating a moderately imbalanced class distribution
- Younger drivers (under 25) show higher claim rates than experienced drivers
- Lower credit scores are associated with higher claim likelihood
- Driving experience is one of the strongest predictors of claim behavior
- Vehicle ownership status and annual mileage also show meaningful differences in claim rates

### Baseline Model Performance (Logistic Regression)
| Metric | Score |
|--------|-------|
| Accuracy | 0.7355 |
| ROC-AUC | 0.7898 |
| Precision (Claim class) | 0.68 |
| Recall (Claim class) | 0.60 |

**Evaluation Metric Rationale:** ROC-AUC was selected as the primary metric because:
- It is robust to class imbalance
- It evaluates model performance across all classification thresholds
- In insurance, missing high-risk customers (false negatives) is costly — AUC captures this better than accuracy alone

## Next Steps
- Compare against ensemble models: Random Forest, XGBoost, LightGBM
- Tune hyperparameters using GridSearchCV or RandomizedSearchCV
- Address class imbalance using SMOTE or `class_weight='balanced'`
- Add SHAP values for model explainability and feature importance validation
- Evaluate precision-recall tradeoff for business use case (cost of false negatives vs false positives)

## Tools and Libraries
- Python 3.11
- pandas, numpy
- matplotlib, seaborn
- scikit-learn

## Link to Notebook
[capstone_eda.ipynb](./capstone_eda.ipynb)
