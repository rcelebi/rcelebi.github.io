---
title: 'ML Model Evaluation: Why a 99% Accurate Model Can Still Fail in Production'
date: 2026-05-12
permalink: /posts/2026/05/ML-model-evaluation/
tags:
  - Machine Learning
  - Model Evaluation
  - Data Science
  - Bias-Variance Tradeoff
  - Classification
---

## Introduction: The Deployment Dilemma

It is a scenario every data scientist fears: you train a model, achieve a stellar accuracy score, and yet the moment it is deployed into a real-world setting, it fails. This disconnect often stems from a misunderstanding of the **Data Science Life Cycle**. While the cycle begins with data selection and preprocessing, model evaluation is the critical bridge between training and deployment. It is not just a final scorecard — it is a recursive checkpoint. If the evaluation reveals a wide "Generalisation Gap," you must go back — perhaps to collect better data, introduce additional cleaning procedures, or refine your feature engineering. Without a robust evaluation strategy, you aren't building a solution; you are building a liability.

## The "Accuracy Trap" and the Imbalanced Class Problem

High accuracy is often the most misleading metric in machine learning, particularly when dealing with imbalanced datasets. Consider a threat-detection model. In a population where only 0.1% of individuals are actual threats, you don't even need to train a model to achieve 99.9% accuracy — simply predict "no threat" for every single person. The number looks perfect, but the model is useless because it fails its primary objective.

> *"In the case of a terrorist profile... 99% of the time the model will be correct because we have only 0.1% threats... we need to reduce the false negative rate."*

In this context, the "cost" of an error is asymmetrical. A false positive might lead to an unnecessary investigation, but a false negative — missing a real threat — is catastrophic. When class distribution is skewed, accuracy ceases to be a meaningful measure of success.

## The Bias-Variance Trade-off: Finding the Sweet Spot

Building a model requires navigating the relationship between model complexity and error rates. This is the trade-off between **underfitting** (high bias) and **overfitting** (high variance).

- **Underfitting (High Bias):** The model is too simple to capture underlying patterns. Logistic Regression, for instance, tends toward underfitting when the data relationship is complex. It creates a generic pattern that leads to high error on both training and test data.

- **Overfitting (High Variance):** The model is overly complex — Random Forests or Neural Networks can "memorise" training data, including its noise and quirks, rather than learning generalisable patterns. Training error drops to near zero while test error rises.

The ultimate goal is **generalisation, not memorisation**. The "sweet spot" is the point of complexity where test error is at its minimum before it begins to diverge from training error.

## Why How You Split Your Data Matters

The way you divide your data into training and test sets can fundamentally change the behaviour of your model. **Stratification** is essential. If your original data reflects a medical setting where 90% of patients are healthy and 10% have a disease, your training and test sets must maintain that exact ratio to remain representative.

Failing to stratify leads to two major issues:

- **Diverging realities:** If the test set distribution deviates from the training set, the model is being evaluated on a different reality than the one it learned from.
- **Small sample instability:** With small datasets, any split is naturally imperfect. Without stratification, the distribution can shift enough that results won't hold on real-world data.

## Validation Strategies: One Size Does Not Fit All

Choosing an evaluation method depends largely on the size of your dataset:

| Dataset Size | Recommended Method | Reasoning |
|---|---|---|
| Large (>10k samples) | Hold-out | A single stratified split is stable and representative. |
| Medium (1k–10k samples) | K-fold Cross-Validation | Dividing into k folds (standard: 10) ensures every sample is used for both training and testing. |
| Small (<1k samples) | Leave-one-out | Each sample acts as the test set once — a last resort due to high computational cost. |

Leave-one-out is expensive because the model must be retrained n times for n samples. While it extracts the most from a tiny dataset, the lack of stratification (since the test set is only one sample) remains a significant disadvantage.

## The Contextual Cost: When a False Alarm Is Better Than a Miss

A "good" model is defined by the consequences of its mistakes — and error costs are rarely symmetrical.

- **Loan decisions:** A bank typically prioritises avoiding false positives — granting a loan to someone who cannot repay. The cost of losing the principal outweighs the missed interest from a false negative (denying a creditworthy applicant).
- **Medical diagnosis:** In disease screening, a false negative is dangerous — the condition goes untreated and may spread. A false positive is manageable, leading to a more accurate secondary test.

> *"You need to look deeper... look at the matrix that is really important in your context."*

By assigning a numerical cost to each error type, you can override a classifier's raw probability score. If the cost of a "miss" is high enough, even a model with a 60% probability of "healthy" might still flag the patient as positive — because the cost of being wrong is simply too high.

## Conclusion: Beyond the Scorecard

Model evaluation is not a hurdle to clear at the end of a project; it is the compass that guides the entire development process. A high accuracy score is only meaningful if it is achieved through proper stratification, appropriate validation strategies, and a deep understanding of the costs associated with specific errors.

As you refine your next model, ask yourself: is your model truly learning a pattern, or is it just telling you what you want to hear because the data is imbalanced?

---

*Remzi Celebi is an Assistant Professor at the Department of Advanced Computing Sciences (DACS), Maastricht University. His research focuses on knowledge graphs, neuro-symbolic AI, and FAIR data for personalized health and drug discovery.*
