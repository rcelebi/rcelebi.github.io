---
title: 'Data Visualization and Exploration: A Scientific Necessity'
date: 2026-04-15
permalink: /posts/2026/04/data-visualization/
tags:
  - Data Visualization
  - Data Science
  - Data Exploration
  - Machine Learning
  - Exploratory Data Analysis
---

Data visualization is far more than creating aesthetic charts; it is a critical scientific tool for understanding trends and patterns. Our biological capacity to process information is physically limited, but our visual sense acts as a high-bandwidth "network cable" for the brain. While hearing has a bandwidth comparable to a hard drive and touch to a USB port, our **visual senses are approximately ten times more powerful**, allowing us to ingest and process complex data flows far more efficiently than through tables alone.

When we discuss data processing, we often treat it as a purely digital challenge. But as an architect designs a building to fit the physical constraints of its site, we must design our data analysis to fit the biological hardware of the human user. Our senses are the primary "input ports" for information, and their bandwidth varies wildly.

Our senses of taste and smell have almost negligible data transfer rates. Hearing is more robust, functioning similarly to an external hard drive with a transfer speed of approximately 12.5 MB/s — sufficient for processing speech or a symphony, but a narrow pipe that would quickly "choke" on the complexity of a modern dataset.

To bypass this bottleneck, we turn to our most powerful input: vision. Human sight functions like a high-speed optical cable, providing massive bandwidth that allows us to absorb complex environments instantly. Visualization isn't about making data "pretty"; it is a technical necessity — the only way to maximise our visual system's bandwidth to catch patterns that would be lost in the noise of a spreadsheet.

## The Four Pillars of Visualization

To effectively use visualization in research, you must first identify your core scientific question. Most visualization tasks fall into four primary categories: **Relationship, Comparison, Composition, and Distribution**.

### 1. Relationship Analysis: Finding Connections

Relationship analysis explores correlations between two or more variables.

- **Scatter Plots:** The gold standard for identifying linear relationships and patterns between two variables.
- **Bubble Charts:** When dealing with three or more variables, extend a 2D plot by using the size or colour of "bubbles" to represent additional dimensions, such as a country's population size alongside its energy usage.

### 2. Comparison Analysis: Benchmarking Groups

This approach compares different groups, categories, or situations.

- **Line and Bar Plots:** The most common tools for comparison. A bar chart can effectively display average salary differences across employee positions, making distinct patterns immediately visible. Aggregated values — such as mean and max-min ranges — can be added to provide deeper scientific meaning.

### 3. Distribution Analysis: Understanding Variability

Before performing complex analysis, you must understand the "shape" of your data.

- **Histograms:** Reveal the **variability, skewness, and presence of outliers**. For example, data from an eye clinic might show a skewed distribution toward older ages — a vital characteristic to note before further modelling.
- **Box Plots:** Essential for identifying the "sanity" of your data by showing the mean, max, min, and the 25th/75th percentiles. Data points appearing far outside these ranges are flagged as outliers that may need to be corrected or removed.

### 4. Composition Analysis: The Parts of the Whole

This analysis views data components as part of a total sum.

- **Pie and Stacked Bar Charts:** Help visualise label distributions. If one category represents only a tiny fraction of the data, predicting that specific case in later machine learning stages will be significantly more challenging.
- **Spider (Radar) Plots:** For complex data with many parameters — such as measuring energy efficiency through multiple factors — a spider plot can visualise how different datasets compare across all metrics simultaneously.

## The Scientific "Sanity Check": Data Exploration

A critical phase of any project is **Data Exploration** — "playing with the data" before applying machine learning. This stage involves testing hypotheses and ensuring data reliability.

Scientific rigour requires a sanity check. If a dataset for human ages contains a value of 150 or -1, and you proceed without checking, your final results will be compromised. Visualization tools like histograms and box plots allow you to see if your data is noisy, missing information, or simply too small to support a robust pattern.

## Conclusion

By mastering these four pillars of visualization, you ensure that your data is not just seen, but truly understood. The goal is not to produce a polished figure — it is to build an honest understanding of your data before you ask a machine to learn from it.

---

*Remzi Celebi is an Assistant Professor at the Department of Advanced Computing Sciences (DACS), Maastricht University. His research focuses on knowledge graphs, neuro-symbolic AI, and FAIR data for personalized health and drug discovery.*
