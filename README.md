# Credit Card Fraud Detection

## Overview

This project focuses on detecting fraudulent credit card transactions using machine learning on a highly imbalanced dataset. The objective is to build a model that can effectively identify fraud while maintaining a practical balance between false positives and false negatives.

---

## Problem Statement

Credit card fraud detection is challenging due to extreme class imbalance (~0.17% fraud cases) and the high cost of misclassification. Traditional accuracy is not a reliable metric, making it necessary to evaluate models using precision, recall, and PR-AUC.

---

## Dataset

* Source: Kaggle Credit Card Fraud Detection dataset
* Total Transactions: 284,807
* Fraud Cases: 492 (~0.17%)
* Features:

  * V1–V28: PCA-transformed anonymized features
  * Time and Amount (scaled)
  * Target: Class (0 = Non-Fraud, 1 = Fraud)

---

## Approach

### 1. Data Preprocessing

* Scaled `Amount` and `Time` using StandardScaler
* Addressed extreme class imbalance

### 2. Baseline Model

* Logistic Regression
* Observed high accuracy but poor fraud detection (low recall)

### 3. Threshold Tuning

* Adjusted decision threshold from 0.5 → 0.2
* Significantly improved recall while maintaining reasonable precision

### 4. Imbalance Handling Techniques

* Class Weighting
* SMOTE (Synthetic Minority Oversampling Technique)

---

## Results

| Method          | Recall | Precision | False Positives | Verdict          |
| --------------- | ------ | --------- | --------------- | ---------------- |
| Baseline (0.5)  | 0.64   | 0.83      | 13              | Too conservative |
| Threshold (0.2) | 0.76   | 0.74      | 26              | Best trade-off   |
| Class Weight    | 0.92   | 0.06      | 1389            | Too aggressive   |
| SMOTE           | 0.92   | 0.06      | 1458            | Similar issue    |

---

## Key Insights

* Accuracy is misleading for highly imbalanced datasets
* Threshold tuning can outperform more complex techniques
* Improving recall often leads to reduced precision
* Imbalance handling methods can overcompensate if not carefully controlled

---

## Business Interpretation

* False Negatives (missed fraud) result in direct financial loss
* False Positives impact user experience and transaction flow
* A threshold of 0.2 provides a balanced and practical solution
* Model choice should align with business objectives (security vs user experience)

---

## Future Work

* Implement real-time fraud detection pipeline
* Experiment with advanced models (XGBoost, Neural Networks)
* Introduce cost-sensitive learning
* Deploy as an API for production use

---

## Conclusion

A simple Logistic Regression model combined with threshold tuning achieved the best balance between fraud detection and operational feasibility. This project highlights that model performance is not just about algorithms, but about aligning evaluation and decisions with real-world business objectives.

