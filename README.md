# Evaluation-of-a-Stroke-Prediction-System


**Critical Evaluation of an Automated Decision System (ADS) for Hospital Admissions and Stroke Detection**

In this project, we critically assessed an Automated Decision System (ADS) implemented by Saimon Dahal, designed for hospital admission and early disease detection, specifically stroke. Our evaluation highlights several concerns regarding its performance, fairness, and overall appropriateness for real-world applications.

**Techniques and Toolkits Used:**

- **SMOTE** (Synthetic Minority Over-sampling Technique) to address data imbalance issues.
- **SHAP Analysis** for model interpretability:
  - **Feature Importance (Global Interpretability)** to explain overall feature importance across the model.
  - **Forceplot (Local Interpretability)** to analyze and visualize how specific features impact individual predictions.
- **Equal Opportunity Framework** to evaluate fairness across gender groups.

**Performance Analysis:**

- The ADS exhibits **low precision (11%)** and **low recall (16%)** on the test set, making it unsuitable for critical healthcare decisions where accurate identification of positive cases is vital.
- The system was optimized for high accuracy rather than addressing the needs of key stakeholders: healthcare providers, who require high precision, and patients, who need high recall.
- The ADS performs comparably to a naive model that predicts the majority class, failing to add meaningful value in stroke prediction.

**Data and Bias Concerns:**

- The dataset used for training is highly imbalanced, leading to poor generalization to unseen cases and exacerbating gender-based biases.
- The application of SMOTE to address data imbalance may have unintentionally worsened bias, especially across gender groups.
- The model systematically underestimates stroke risk for females and other gender groups, resulting in a higher False Negative Rate (FNR) for these groups, which is unacceptable in high-stakes medical applications.

**Fairness and Interpretability:**

- The ADS violates the fairness principle of Equal Opportunity by introducing bias in error rates across gender groups.
- Using SHAP techniques, we identified issues with feature processing that undermine the model's trustworthiness, including sub-optimal feature encoding.

**Recommendations for Improvement:**

1. **Balanced Dataset:** Train the model on a more balanced dataset that adequately represents each label and includes diverse feature distributions.
2. **Appropriate Metrics:** Optimize the model based on metrics like FPR, FNR, or F1-score, aligning with stakeholder needs rather than focusing solely on accuracy.
3. **Bias Monitoring:** Implement custom metrics (e.g., SIF) to track changes in sensitive feature distributions during data processing to prevent technical bias.
4. **Feature Encoding:** Avoid ordinal encoding for categorical features that do not have a natural order; instead, use one-hot encoding to prevent false numerical relationships.
5. **Fairness Evaluation:** Continuously monitor fairness metrics across groups, and if biases are detected, consider post-processing techniques, such as threshold adjustment, to minimize disparities.
