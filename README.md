# Credit-Risk-Prediction

This project develops and evaluates machine learning models to classify loan applicants as **Good (1)** or **Bad (0)** credit risks, with a strong focus on **business-aligned decision making** rather than just model accuracy.
It demonstrates how credit risk models can be translated into lending policies through **threshold tuning**, **risk banding**, and **lending policy simulations**.
The analysis is implemented in Jupyter notebook, written as a narrative workflow with short cells and inline commentary explaining each modeling choice, threshold decision, and business insight.


---

## 🔎 Quick Snapshot

| Aspect                        | Summary |
|------------------------------|---------|
| Problem                      | Predict whether an applicant is a good or bad credit risk. |
| Dataset                      | German Credit Dataset (1,000 records, mixed numerical & categorical features). |
| Algorithms                   | Logistic Regression, Decision Tree, Random Forest, XGBoost. |
| Final Model                  | XGBoost with tuned decision threshold. |
| Key Metrics (Test Set)       | 73% accuracy, 68% recall for Bad class, 85% precision for Good class. |
| Business Layer               | Risk banding and lending policy simulation on test set. |

---
## 📌 Project Overview

Financial institutions need to balance **risk** (avoiding defaults) and **growth** (approving more loans).  
This project builds a credit risk model and then connects it to **practical decision frameworks** that a bank could use in production.

Core objectives:
- Build interpretable models to classify applicants as Good (1) or Bad (0).
- Improve detection of bad-credit applicants using **threshold tuning**.
- Segment applicants into **risk bands** (Low, Medium, High).
- Simulate **lending policies** under different risk appetites.

---

## 📊 Dataset Summary
- German Credit Dataset
- Mix of numerical and categorical features
- Target variable: **Risk**  
  - `0` → Bad credit risk  
  - `1` → Good credit risk

Due to the limited dataset size, the project focus is on robust methodology, interpretability, and decision frameworks rather than overfitting for marginal metric gains.

---

## 🔍 Exploratory Data Analysis (EDA)

Key analyses performed:
- Descriptive statistics and value counts
- Missing value handling (treated as a separate category where applicable)
- Correlation heatmap
- Group-wise analysis (credit amount by sex, job, housing, etc.)
- Risk-wise visualizations:
  - Box plots and violin plots
  - Scatter plots (Credit Amount vs Age, sized by Duration)
  - Count plots for categorical features split by risk class

EDA was used to understand *customer behavior* and *risk patterns* before modeling.

---

## 🛠 Feature Engineering & Encoding
- **One-hot encoding**: purpose, sex
- **Ordinal encoding**:
  - Saving accounts: `none < little < moderate < rich < quite rich`
  - Checking account: `none < little < moderate < rich`
- Target variable encoded using label encoding
- Train-test split applied after encoding

---

## 🤖 Models Implemented
The following models were trained and evaluated:

- Logistic Regression (baseline)
- Decision Tree
- Random Forest
- XGBoost

Evaluation focused on:
- Accuracy
- Precision & Recall (especially for **Bad class**)
- Classification analysis
- Confusion matrix

---

## 🎯 Threshold Tuning
Instead of relying on the default 0.5 threshold, custom threshold tuning was applied to improve detection of **bad credit applicants**, which is critical in financial risk scenarios.

- Model probabilities were analyzed
- Threshold adjusted to optimize *Bad-class recall*
- Final decision threshold chosen based on *business risk tolerance*

---

## 🧠 Final Model Performance (XGBoost – Threshold Tuned)

| Metric | Bad (0) | Good (1) |
|------|--------|---------|
| Recall | **68%** | 74% |
| Precision | 53% | **85%** |
| Overall Accuracy | **73%** |

This configuration achieves a strong balance between identifying *risky applicants* and maintaining loan *approval quality*.

---

## 📈 Feature Importance
XGBoost feature importance highlights:
- Credit Amount
- Age
- Duration
- Checking Account
- Saving Account
- Job
- Purpose

This supports model interpretability and trust.

---

## 🏦 Lending Policy Simulation (Test Set)

| Policy | Approved | Expected Defaults | Default Rate |
|------|---------|------------------|--------------|
| Approve All | 200 | 60 | 30.0% |
| Low + Medium Risk | 181 | 46 | 25.41% |
| Low Risk Only | 146 | 28 | **19.18%** |

**Default Rate:**  
The proportion of approved loan applications that are classified as *bad risk*, indicating loans that are expected to result in default or serious repayment issues.


### Key Takeaways
- Risk banding enables controlled reduction in *default rates*
- Banks can choose policies based on *risk appetite*
- Demonstrates how ML outputs translate into *real-world decisions*

---



## 🧠 Key Learnings
- Accuracy alone is insufficient in credit risk modeling
- Threshold tuning is critical for aligning models with business goals
- Risk banding adds significant real-world value
- Simple datasets still allow strong insights when approached methodically

---

## 🚀 Tools & Technologies
- Python
- Pandas, NumPy
- Matplotlib, Seaborn
- Scikit-learn
- XGBoost

---

---

## 📌 Conclusion
Through interpretability-driven modeling, threshold optimization, and policy simulation, this project bridges the gap between data science and practical credit risk management. It reflects workflows used in modern financial analytics teams.

---

## 🔮 Future Improvements & Extensions

This project focuses on building an interpretable and business-oriented credit risk model using a limited set of applicant-level features. Possible future enhancements include:

1. **Richer Feature Availability**
   - Incorporating additional financial attributes such as income, existing liabilities, or historical repayment behavior could improve risk discrimination.
   - With the current dataset, feature engineering options are intentionally limited.

2. **Policy-Level Optimization**
   - Further analysis could be performed to identify optimal approval thresholds based on different business objectives, such as maximizing approved volume under a fixed default-rate constraint.

3. **Out-of-Sample Validation**
   - Testing the framework on a larger or more recent credit dataset would help assess model stability and generalizability across populations.

4. **Deployment-Oriented Monitoring**
   - In a real-world setting, model performance and default rates would need continuous monitoring to detect performance drift over time.

These extensions focus on data and decision-level improvements, which are often more impactful than additional model complexity in practical credit risk systems.

---
