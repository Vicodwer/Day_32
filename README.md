# Day_32_AM
# 🏦 Loan Approval System  
**Decision Tree vs Random Forest | IIT Gandhinagar – PG Diploma AI/ML**

---

## 📌 Problem Statement

A bank requires a loan approval system that is:
- ✅ Accurate  
- ✅ Interpretable (regulatory requirement)  

We built and compared:
- Decision Tree (DT)
- Random Forest (RF)
- Extra Trees (Stretch Study)

---

## 📊 Dataset

Synthetic dataset (2000 records) with features:

- annual_income  
- credit_score  
- loan_amount  
- employment_years  
- debt_to_income  
- num_credit_cards  

Target:
- approved (1 = Approved, 0 = Rejected)

---

## 🌳 Model 1: Decision Tree (max_depth=4)

### Why?
- Highly interpretable
- Easy to extract decision rules

### Sample Extracted Rules

- IF credit_score > 700 AND debt_to_income < 0.35 → APPROVE  
- IF credit_score ≤ 650 → REJECT  
- IF employment_years > 5 → APPROVE  

### Pros
✔ Transparent  
✔ Easy to explain to regulators  

### Cons
✘ High variance  
✘ Can overfit  

---

## 🌲 Model 2: Random Forest (Tuned with RandomizedSearchCV)

### Why?
- Reduces variance via bagging
- More stable performance

### Tuning Strategy
- RandomizedSearchCV
- 5-Fold Cross Validation
- Optimized for F1 score

### Results (Typical)

| Model           | Accuracy | F1 | ROC-AUC |
|----------------|----------|----|---------|
| Decision Tree | ~0.88    | ~0.82 | ~0.86 |
| Random Forest | ~0.92    | ~0.89 | ~0.93 |

---

## 📌 Feature Importance

Compared:
- Default Gini importance (MDI)
- Permutation importance

Permutation importance is more reliable because it measures actual impact on predictions.

---

## ⚖ Interpretability vs Accuracy Tradeoff

- Decision Tree → High interpretability, moderate accuracy  
- Random Forest → High accuracy, lower interpretability  

---

## 📝 Final Recommendation

Deploy **Random Forest** for prediction accuracy and use a **shallow Decision Tree for explanation** during audits and regulatory reviews.

This hybrid approach ensures:
- High predictive performance
- Regulatory compliance
- Business reliability

---

## 🎯 Key Concepts Demonstrated

- Gini Impurity  
- Overfitting & Pruning  
- Bias-Variance Tradeoff  
- Bagging  
- RandomizedSearchCV  
- Permutation Importance  
- Cross-Validation  

---

## 📂 Repository Structure


# Day_32_PM
# 🛡 Insurance Fraud Detection System  
**Decision Tree vs Random Forest | Business-Constrained Model Selection**

---

## 📌 Problem Statement

An insurance company wants to detect fraudulent claims.

Constraints:
1. Regulators require explanations.
2. Missing fraud (False Negative) costs 10x more than a false alarm.

---

## 📊 Dataset

Synthetic dataset (3000 records) with:

- claim_amount  
- customer_age  
- num_previous_claims  
- policy_years  
- incident_severity  
- num_witnesses  

Target:
- fraud (1 = Fraud, 0 = Legitimate)

---

## 🌳 Model 1: Decision Tree (max_depth=5)

### Purpose:
- Extract interpretable fraud rules

### Sample Fraud Rules:

- IF claim_amount > 70000 AND num_previous_claims > 3 → FRAUD  
- IF incident_severity ≥ 3 → FRAUD  
- IF num_previous_claims ≤ 1 → NOT FRAUD  

### Strengths:
✔ Easy to explain  
✔ Regulator-friendly  

### Weakness:
✘ Misses more fraud cases compared to RF  

---

## 🌲 Model 2: Random Forest (Tuned for Recall)

### Why Recall?
Fraud miss cost = 10 × False Alarm cost  

We optimized using:
- RandomizedSearchCV
- 5-Fold CV
- Scoring = Recall

---

## 📊 Performance Comparison

| Model           | Accuracy | Recall | F1 | ROC-AUC |
|----------------|----------|--------|----|---------|
| Decision Tree | ~0.85    | ~0.70  | ~0.74 | ~0.82 |
| Random Forest | ~0.91    | ~0.84  | ~0.86 | ~0.89 |

---

## 💰 Cost-Sensitive Evaluation

Cost Formula:

Cost = (10 × False Negatives) + (1 × False Positives)

Result:
- Random Forest → Lower business cost  
- Decision Tree → Higher fraud miss cost  

---

## ⚖ Deployment Recommendation

### Performance Perspective:
Random Forest significantly reduces fraud misses, lowering total financial loss.

### Regulatory Perspective:
Decision Tree provides human-readable explanations.

### Final Strategy:
Deploy:
- Random Forest → Automated fraud scoring  
- Decision Tree → Human review explanation  

This ensures:
✔ Cost minimization  
✔ High recall  
✔ Regulatory compliance  

---

## 📘 Stretch Learning: Boosting vs Bagging

- Bagging (RF): Reduces variance  
- Boosting (GBM): Reduces bias sequentially  

Boosting trains models sequentially correcting previous errors.

---

## 🎯 Key Concepts Demonstrated

- Recall Optimization  
- Cost-Sensitive Learning  
- RandomizedSearchCV  
- Bias-Variance Tradeoff  
- OOB Error  
- Feature Importance Stability  
- Production Tradeoffs (100 vs 1000 trees)

---

## 📂 Repository Structure


---

## 🚀 Author

Vishal Pagadala  
PG Diploma in AI-ML & Agentic AI Engineering  
IIT Gandhinagar
