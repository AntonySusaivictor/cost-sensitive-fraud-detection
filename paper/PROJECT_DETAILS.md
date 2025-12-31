# Cost-Sensitive Fraud Detection with Threshold Optimization
## Technical Note Supporting PhD Research Proposal

**Author:** Antony Susai Victor

---

## 1. Introduction

Fraud detection in financial transaction systems is characterized by two fundamental challenges:
- **Extreme class imbalance**: Fraudulent transactions typically represent <0.1% of total activity
- **Asymmetric misclassification costs**: False negatives (missed fraud) incur significantly higher costs than false positives

Traditional ML approaches optimize accuracy or AUC metrics, which fail to reflect operational realities of fraud decision systems. This study presents an applied investigation into **cost-sensitive machine learning** with focus on **decision threshold optimization**.

---

## 2. Dataset and Problem Setting

### Dataset: Credit Card Fraud Detection
- **Total Transactions**: 284,807
- **Fraudulent Transactions**: 492 (~0.17% class imbalance)
- **Features**: 30 (PCA-anonymized features + raw amount + time)
- **Objective**: NOT maximum accuracy, but **minimize expected cost** under asymmetric error penalties

---

## 3. Feature Engineering

Intentionally minimal to avoid overfitting and focus on decision optimization:

1. **Log-transformed transaction amount**
   - Stabilizes highly skewed amount distribution
   - Dominant predictor of fraud

2. **Hour of day**
   - Behavioral temporal signal
   - Secondary but complementary contribution

---

## 4. Cost-Sensitive Modeling Approach

### Two Models Trained:

**Model 1: Baseline**
- Trained without class imbalance handling
- Standard random forest classifier

**Model 2: Cost-Sensitive**
- Uses class-weighting inversely proportional to class frequency
- Explicitly penalizes minority class misclassification

**Output**: Probabilistic fraud predictions (not hard labels)
- Enables explicit threshold optimization
- Critical but often overlooked component

---

## 5. Cost-Sensitive Threshold Optimization

### Traditional Approach (Fixed Threshold)
- Uses default threshold = 0.5
- Ignores business cost structure
- Suboptimal for imbalanced, cost-sensitive problems

### Proposed Approach (Threshold Sweep)

Optimize across continuous threshold range:

```
Expected Cost = FN x cost_fraud + FP x cost_false_positive

Where:
- cost_fraud = 10 (missed fraudulent transaction)
- cost_false_positive = 1 (legitimate transaction flagged)
```

**Result**: Optimal threshold selected by minimizing total expected cost

---

## 6. Explainability Analysis

### SHAP (SHapley Additive exPlanations)

**Global SHAP Findings:**
- **Transaction Amount (log-scaled)**: Dominant contributor to predictions
- **Hour of Day**: Secondary but meaningful behavioral signal
- Aligns with domain expectations in fraud analytics
- Demonstrates simple behavioral signals enhance discrimination under extreme imbalance

---

## 7. Key Results

1. **Meaningful performance gains** through decision-level optimization, NOT model complexity
2. **Transaction amount** remains strongest predictor
3. **Threshold optimization** enables improved fraud recall without proportional increase in false positives
4. **Explainability and cost-aware evaluation** are complementary, not competing objectives
5. **Interpretable models** with calibrated decision rules more likely adopted in real-world systems

---

## 8. Relation to Proposed PhD Research

This work represents initial exploration of:

**Pillar 2: Imbalanced Learning and Risk-Optimized Decision Thresholds**
- Foundation for behavior-aware fraud detection systems

**Pillar 1: Behavioral Feature Modeling** (partial)
- Integration of transaction and temporal patterns

### Future PhD Research Extensions:
- Richer temporal behavior modeling
- Adaptive thresholding strategies
- Deployment-aware constraints in real-time decision systems
- Behavioral profiling under concept drift

---

## 9. Conclusion

Cost-sensitive modeling and threshold optimization are **critical components** of effective fraud detection under extreme class imbalance. By prioritizing **decision calibration over model complexity**, this work provides practical and interpretable foundation for doctoral research in:
- Applied fraud analytics
- Cost-aware decision systems
- Interpretable machine learning for finance

---

## References

1. Dal Pozzolo, A., et al. (2018). Credit Card Fraud Detection: A Realistic Modeling and a Novel Learning Strategy. IEEE Transactions on Neural Networks and Learning Systems.

2. Xie, T., et al. (2020). Imbalanced Learning for Fraud Detection. Proceedings of KDD.

3. Bahnsen, A., et al. (2015). Cost-sensitive Decision Trees for Fraud Detection. Expert Systems with Applications.
