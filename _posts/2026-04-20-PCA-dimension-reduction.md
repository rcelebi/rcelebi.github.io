---
title: 'Principal Component Analysis: Cutting Through High-Dimensional Data to Find What Actually Matters'
date: 2026-04-20
permalink: /posts/2026/04/PCA-dimension-reduction/
tags:
  - Machine Learning
  - Dimensionality Reduction
  - PCA
  - Data Science
  - Statistics
---

## 1. Introduction: The Curse of Dimensionality

Imagine you are trying to describe a complex, three-dimensional object to someone over the phone, but you are only allowed to use two or three words to capture its entire essence. In data science, we face a similar struggle known as the **curse of dimensionality**. When you are staring at a dataset with a massive number of features, it becomes nearly impossible to see the patterns hidden within the noise. It feels like trying to navigate a dense forest where every tree represents a different variable — eventually, you lose sight of the landscape entirely.

**Principal Component Analysis (PCA)** is the fundamental technique designed to solve this problem. It is a dimensionality reduction tool that helps us make sense of high-dimensional data by identifying what actually matters and discarding the rest. PCA allows us to see the "big picture" of a dataset without getting lost in the overwhelming details of its individual parts.

## 2. Variation is the Only Data That Matters

To understand PCA, we must first change how we value data. We often assume that every column in our spreadsheet is equally important, but PCA teaches us that importance is defined by **variation** — or spread.

Think of a graph with two axes, X1 and X2. If all your data points are clustered tightly on the X1 axis but spread widely across X2, then X2 is doing a much better job of summarising the differences between those points. If there is no variation along an axis, that axis provides almost no informational value.

To determine importance, we project the data and quantify the distance of points from the origin. Crucially, we aren't looking for points that are far away in isolation; we are looking for the **variance** of those distances across the whole dataset. If every point is the same distance from the origin, there is no spread — and therefore no information.

This is often counter-intuitive. We tend to focus on individual values, but PCA shifts our focus to the *differences* between values. If a feature doesn't show quantifiable spread, it isn't helping us distinguish one data point from another.

## 3. Stop Choosing Columns — Start Creating New Ones

The brilliance of PCA is that it doesn't force you to choose between Column A or Column B. Instead, it **creates entirely new axes**. When traditional columns don't clearly summarise the data, PCA performs a rotational shift: it moves the origin to the centre of your data cloud and draws a new axis through the data at an angle that captures the maximum possible spread.

This new axis is a **linear combination of existing features**. Think of it as a recipe: instead of picking just Feature X or Feature Y, PCA might find that a new direction — perhaps a mix of 70% of Feature X and 30% of Feature Y — summarises the data more effectively.

Rather than losing information by deleting columns, PCA *condenses* the information. It summarises each data point by finding the direction in which the data is most stretched out. By shifting the centre and drawing these new lines, we can represent a complex cloud of points using a much simpler coordinate system.

## 4. The Mathematics Behind PCA: Eigenvectors and Eigenvalues

Behind the scenes of PCA is a sophisticated mathematical engine called **Singular Value Decomposition (SVD)**. This process uncovers **Eigenvectors** and **Eigenvalues** — compressed summaries of your data matrix. An Eigenvector is the direction of the new axis; the Eigenvalue is the numerical weight that tells you exactly how much variation is captured in that direction.

The "rank" of your PCA determines how many of these vectors you decide to keep. In many cases, you don't need all of them to get an accurate picture of your data. Often, just one, two, or three vectors can capture 90% of the information in a dataset that originally had dozens or hundreds of columns. By focusing only on the vectors with the highest eigenvalues, we can confidently ignore the minor variations that are likely just noise.

> *"If you have one vector that can explain half the variation and another that explains 30%, then with only two vectors you can already explain 80% of the variation."*

## 5. Knowing When to Stop: Visualisation vs. Clustering

How you apply PCA depends on your specific goal:

- **For Visualisation:** Stick to two or three components. Because we live and think in three dimensions, reducing your data to two components allows for a clear plot where clusters and patterns become instantly visible to the human eye.

- **For Data Processing and Clustering:** You can afford to be more granular. If you are preparing data for a clustering algorithm rather than a human viewer, keeping a higher number of components allows the algorithm to catch subtle variations while still benefiting from reduced computational noise.

**A practical rule of thumb:** always check the cumulative percentage of variation explained. If three components capture 90% of your data's spread, adding a fourth might contribute only 1% of extra detail — which is often noise you're better off leaving behind.

## 6. Conclusion: The Elegance of Simplicity

PCA is a transformative tool that takes a very complex problem and shrinks it to a manageable size. By converting raw features into a smaller set of principal components, we transition from a cluttered, high-dimensional space to a streamlined environment where the most important patterns — the signal — are clear.

The process of moving from N dimensions to R components is about more than just mathematics; it is about finding the **essence** of your data. It turns a massive, unreadable matrix into a few key vectors that represent the soul of the dataset — and in doing so, reveals the structure that was always there, waiting to be seen.

---

*Remzi Celebi is an Assistant Professor at the Department of Advanced Computing Sciences (DACS), Maastricht University. His research focuses on knowledge graphs, neuro-symbolic AI, and FAIR data for personalized health and drug discovery.*
