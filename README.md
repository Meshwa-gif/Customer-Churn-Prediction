# Customer Churn Prediction — SQL + Machine Learning

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat&logo=mysql&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat)

End-to-end churn prediction pipeline on **7,043 telecom customers** — SQL segment analysis to identify churn drivers, then Logistic Regression and Random Forest models to predict at-risk customers, with 5 actionable business retention recommendations.

---

## Project Preview

![Customer Churn Prediction Overview](charts/page1_overview.jpg)

---

## Key Results

| Metric | Value |
|--------|-------|
| Overall Churn Rate | **26.6%** |
| Month-to-Month Churn Rate | **42.7%** |
| Best Model ROC-AUC | **0.834** (Logistic Regression) |
| Random Forest ROC-AUC | 0.816 |
| Customers Analyzed | **7,043** |
| Churners Correctly Identified | 297 of 374 (**79%**) |
| Churned Avg Monthly Charges | $74.44 |
| Retained Avg Monthly Charges | $61.31 |

---

## Part 1 — SQL Segment Analysis

### Churn Rate by Contract Type
![Tenure, Internet & Payment Analysis](charts/page2_tenure_internet_payment.jpg)

| Contract Type | Churn Rate |
|---------------|------------|
| Month-to-month | **42.7%** |
| One year | 11.3% |
| Two year | 2.8% |

Month-to-month customers churn at over **3x** the rate of one-year contracts and **15x** the rate of two-year contracts. Contract length is the single clearest lever for reducing churn.

### Churn Rate by Tenure Group

| Tenure | Churn Rate |
|--------|------------|
| 0–1 Year | **47.7%** |
| 1–2 Years | 28.7% |
| 2–4 Years | 20.4% |
| 4+ Years | 9.5% |

The first year is the highest-risk period — churn drops from 47.7% to 9.5% for long-tenure customers. First-year onboarding is the best window for retention efforts.

### Churn Rate by Internet Service & Payment Method

| Internet Service | Churn Rate |
|-----------------|------------|
| Fiber optic | **41.9%** |
| DSL | 19.0% |
| No internet | 7.4% |

| Payment Method | Churn Rate |
|---------------|------------|
| Electronic check | **45.3%** |
| Mailed check | 19.2% |
| Bank transfer (auto) | 16.7% |
| Credit card (auto) | 15.3% |

Fiber optic customers churn at 41.9% despite paying premium prices — suggesting service quality or pricing concerns. Electronic check users churn at 45.3%, far above automatic payment methods.

---

## Part 2 — Predictive ML Model

### Churn Distribution & Monthly Charges
![Model ROC Curve & Distributions](charts/page3_model_roc_curve.jpg)

26.6% of customers churned overall. Churned customers pay **$74.44/month** on average vs **$61.31** for retained customers — higher bills strongly correlate with churn risk.

### Model Comparison: ROC Curve

| Model | ROC-AUC |
|-------|---------|
| Logistic Regression | **0.834** ✅ Best |
| Random Forest | 0.816 |
| Baseline (random) | 0.500 |

Logistic Regression slightly outperformed Random Forest on this dataset — both scores indicate strong predictive power well above the 0.5 baseline of random guessing.

### Confusion Matrix — Logistic Regression
![Confusion Matrix & Feature Importance](charts/page4_confusion_matrix_features.jpg)

|  | Predicted: Stayed | Predicted: Churned |
|--|-------------------|--------------------|
| **Actual: Stayed** | 725 | 308 |
| **Actual: Churned** | 77 | **297** |

Of 374 actual churners in the test set, the model correctly identified **297 (79%)** — with class weighting applied specifically to prioritize catching at-risk customers rather than optimizing overall accuracy.

### Top 10 Features Driving Churn (Random Forest)

| Rank | Feature | Importance |
|------|---------|------------|
| 1 | TotalCharges | Highest |
| 2 | MonthlyCharges | High |
| 3 | Tenure | High |
| 4 | Contract type | Medium-High |
| 5 | OnlineSecurity | Medium |
| 6 | PaymentMethod | Medium |
| 7 | TechSupport | Medium |
| 8 | InternetService | Lower |
| 9 | OnlineBackup | Lower |
| 10 | Gender | Lowest |

TotalCharges, MonthlyCharges, tenure, and Contract type are the four strongest predictors — together accounting for over half of the model's decision-making power.

---

## Business Recommendations
![Business Recommendations](charts/page5_recommendations.jpg)

**1. Convert month-to-month customers**
Offer incentives (discounts, bundled services) to shift month-to-month customers (42.7% churn) toward 1–2 year contracts (2.8–11.3% churn).

**2. Strengthen first-year onboarding**
New customers churn at 47.7% in year one vs 9.5% after 4 years. A dedicated onboarding and check-in program in months 1–12 could significantly reduce early churn.

**3. Investigate fiber optic experience**
Fiber customers churn at 41.9% despite paying premium prices — review service reliability, pricing perception, and support quality for this segment.

**4. Encourage automatic payment methods**
Electronic check users churn at 45.3% vs 15–19% for automatic payments. Incentivize switching to autopay (credit card or bank transfer).

**5. Deploy the churn model for proactive retention**
With ROC-AUC of 0.834, the model can flag at-risk customers in advance, enabling targeted retention offers before they cancel.

---

## Tech Stack

`Python` `SQL (SQLite)` `Pandas` `scikit-learn` `Logistic Regression` `Random Forest` `Matplotlib` `Seaborn` `Excel Export`

---

## Dataset

- **Source:** IBM Telco Customer Churn dataset
- **Records:** 7,043 customers
- **Features:** 21 columns — demographics, services, contract, billing, churn label
- **Download:** [Kaggle — Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)

---

## Project Context

Built as part of my data analytics portfolio to demonstrate:
- SQL-driven business segmentation and churn driver analysis
- End-to-end ML pipeline: data cleaning → feature engineering → model training → evaluation
- Imbalanced classification with class weighting to maximize recall on minority class
- ROC-AUC model comparison and confusion matrix interpretation
- Translating model outputs into actionable business recommendations

---

## Author

**Meshwa Patel** — Data Analyst  
[Portfolio](https://meshwa-gif.github.io) · [LinkedIn](https://www.linkedin.com/in/meshwapatel-2b24a8385) · [Email](mailto:meshwapatel2508@gmail.com)
