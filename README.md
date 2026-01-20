## Overview

This project analyzes how **different sampling techniques** influence the performance of various **machine learning models** on a **credit card fraud detection dataset**.
Since fraud datasets are typically **highly imbalanced**, the study focuses on balancing the data, creating multiple samples using different sampling strategies, and evaluating model accuracy on each sample.

The aim is to identify **which sampling technique works best for each model**.

---

## Dataset Description

* **Dataset:** `Creditcard_data.csv`
* **Target Column:** `Class`

  * `0` → Non-Fraudulent Transaction
  * `1` → Fraudulent Transaction
* The original dataset is **severely imbalanced**, with far fewer fraud cases compared to non-fraud cases.

---

## Data Preparation and Balancing

* The dataset was first examined to understand class distribution.
* **Random Over-Sampling** was applied using the `imbalanced-learn` library to balance the fraud and non-fraud classes.
* This step ensures that models do not become biased toward the majority class.

---

## Sample Size Calculation

To create representative subsets of the balanced data, **Slovin’s Formula** was used.
---

## Sampling Techniques Used

Five different sampling techniques were applied to generate distinct datasets:

1. **Simple Random Sampling**
   Randomly selects `n` data points from the dataset.

2. **Systematic Sampling**
   Selects every `k`th record from the dataset based on a fixed interval.

3. **Stratified Sampling**
   Divides data into strata based on class labels and samples proportionally to preserve class balance.

4. **Cluster Sampling**
   Groups the data into clusters and randomly selects entire clusters for training.

5. **Bootstrap Sampling**
   Randomly samples `n` records **with replacement**, allowing duplicate entries.

---

## Machine Learning Models Used

Each sampled dataset was trained and evaluated using the following models:

* Logistic Regression
* Decision Tree Classifier
* Random Forest Classifier
* Support Vector Machine (SVM)
* K-Nearest Neighbors (KNN)

---

## Model Evaluation

* Data was split into **80% training** and **20% testing** sets using stratified sampling.
* Feature scaling was applied for:

  * Logistic Regression
  * SVM
  * KNN
* Tree-based models were trained on unscaled data.
* **Accuracy (%)** was used as the evaluation metric.

---

## Results Summary

### Accuracy (%) Across Sampling Techniques

| Model               | Simple Random | Bootstrap | Stratified | Systematic | Cluster   |
| ------------------- | ------------- | --------- | ---------- | ---------- | --------- |
| Logistic Regression | 90.62         | 85.94     | 92.19      | 92.19      | **98.44** |
| Decision Tree       | **100.00**    | 93.75     | 95.31      | 98.44      | 98.44     |
| Random Forest       | 98.44         | 95.31     | **100.00** | **100.00** | 98.44     |
| SVM                 | 81.25         | 71.88     | 73.44      | 70.31      | **98.44** |
| KNN                 | 95.31         | 89.06     | **98.44**  | 89.06      | 98.44     |

---

## Best Sampling Technique per Model

* **Logistic Regression:** Cluster Sampling
* **Decision Tree:** Simple Random Sampling
* **Random Forest:** Stratified Sampling
* **SVM:** Cluster Sampling
* **KNN:** Stratified Sampling

---

## Key Observations

* **Stratified and Cluster Sampling** consistently produced high accuracy across multiple models.
* **Random Forest** showed stable and strong performance regardless of sampling method.
* **SVM** benefited significantly from Cluster Sampling, showing a major improvement.
* **Bootstrap Sampling** generally resulted in lower accuracy for most models.
* Sampling strategy plays a critical role in performance, especially for imbalanced datasets.

---

## Tools and Platform

* **Platform:** Google Colab
* **Libraries Used:**

  * pandas
  * numpy
  * scikit-learn
  * imbalanced-learn

---

## How to Run

1. Open `Sampling-Techniques.ipynb` in Google Colab.
2. Run all cells sequentially.
3. The notebook will:

   * Balance the dataset
   * Apply sampling techniques
   * Train models
   * Display accuracy results and best sampling methods

---

## Conclusion

This project demonstrates that **handling class imbalance and choosing the right sampling technique** are essential for building effective fraud detection models. While tree-based models perform well across most scenarios, models like SVM and KNN show significant dependence on the sampling strategy. Proper sampling combined with appropriate models leads to better and more reliable performance in fraud detection tasks.

---
