# Bank Marketing — Comparing Classifiers

## Overview
This is my Practical Application III assignment where I compare four classification algorithms — **Logistic Regression**, **K-Nearest Neighbors (KNN)**, **Decision Trees**, and **Support Vector Machines (SVM)** — on a bank telemarketing dataset. The goal is to predict whether a client will subscribe to a term deposit.

## Dataset
- **Source**: [UCI Machine Learning Repository — Bank Marketing](https://archive.ics.uci.edu/ml/datasets/bank+marketing)
- **Records**: 41,188 contacts from a Portuguese bank (May 2008 – Nov 2010)
- **Features**: 20 input features (client demographics, campaign details, economic indicators)
- **Target**: Binary — did the client subscribe to a term deposit? (yes/no)

## What I Found

### Class Imbalance
Only about **11.3%** of contacts resulted in a subscription. A model that just predicts "no" every time gets 88.7% accuracy, so I used **F1-score** as my main evaluation metric instead of accuracy.

### Model Performance (After Tuning)

| Model               | Test Accuracy | Test F1-Score | Train Time |
|---------------------|--------------|---------------|------------|
| Logistic Regression | ~90.1%       | ~0.34         | Fast       |
| KNN                 | ~89.4%       | ~0.37         | Fast       |
| Decision Tree       | ~90.1%       | ~0.38         | Fast       |
| SVM                 | ~89.6%       | ~0.37         | Very Slow  |

- **Decision Tree** (with max_depth=5) got the best F1-score after tuning.
- **Logistic Regression** was fast and easy to understand.
- **SVM** took a really long time to train and didn't perform much better than the others.

### Important Features
- Economic indicators (euribor3m, emp.var.rate, nr.employed) were strong predictors.
- Previous campaign success was a big signal — people who subscribed before are likely to do it again.
- Contact month matters — March, September, October, December had better results.
- Cellular contact worked better than telephone.
- Retired people and students had higher subscription rates.

## Recommendations
1. Call back clients who subscribed before — they're the best targets.
2. Try to run campaigns in March, September, October, or December.
3. Use cellular contact over telephone when possible.
4. Pay more attention to retired and student clients.
5. Keep an eye on economic conditions — they seem to affect subscription rates.

## Next Steps
- Try ensemble methods (Random Forest, Gradient Boosting).
- Handle class imbalance with oversampling or class weights.
- Experiment with different probability cutoffs.
- Get more client data if possible.

## Files
- `bank-marketing-classifier-comparison.ipynb` — Complete Jupyter Notebook with analysis
- `data/bank-additional-full.csv` — Full dataset

## How to Run
```bash
jupyter notebook bank-marketing-classifier-comparison.ipynb
```

## Link to Notebook
[bank-marketing-classifier-comparison.ipynb](bank-marketing-classifier-comparison.ipynb)
