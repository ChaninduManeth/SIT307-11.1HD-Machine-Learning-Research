# SIT307 11.1HD – Machine Learning Research

## Project Overview

This repository contains the implementation and experimental work for the
SIT307 11.1HD Machine Learning Research task.

The project reproduces and critically evaluates the machine learning methods
presented in:

"An efficient stacking-based ensemble technique for early heart attack prediction"

The project contains two main stages:

1. Reproduction and evaluation of the machine learning methods presented in
   the selected research paper.
2. Development and evaluation of an improved leakage-resistant stacking
   approach based on limitations identified during the reproduction study.

## Dataset

The project uses the Heart Disease Dataset containing:

- 1,025 observations
- 13 predictor variables
- 1 binary target variable

Dataset location:

`data/heart.csv`

## Project Structure

- `data/` – Dataset used for the experiments
- `notebooks/` – Jupyter notebook containing the complete analysis
- `results/figures/` – Generated figures and plots
- `results/tables/` – Experimental result tables
- `requirements.txt` – Required Python packages

## Work Completed

### Part 1 – Reproduction

- Reproduced six individual classifiers:
  - Logistic Regression
  - Decision Tree
  - Random Forest
  - XGBoost
  - Naive Bayes
  - K-Nearest Neighbors
- Reproduced the five-fold stacking ensemble
- Compared published and reproduced results using Accuracy, Precision,
  Recall, F1 Score and AUC

### Critical Analysis

- Identified 723 duplicate rows in the 1,025-row dataset
- Identified only 302 unique feature records
- Found that 97.07% of the original test observations had an identical
  feature vector in the training set
- Evaluated models after removing duplicate rows
- Performed group-aware validation to prevent identical feature patterns
  from appearing across training and testing data
- Investigated inconsistencies in the published results

### Part 2 – Proposed Solution

A fully group-aware stacking procedure was developed in which duplicate
feature groups are separated during both:

- the external train-test split; and
- the internal cross-validation used to generate stacking features.

Final proposed model performance:

- Accuracy: 87.92%
- Precision: 87.16%
- Recall: 89.62%
- F1 Score: 88.37%
- Specificity: 86.14%
- MCC: 0.7585
- AUC: 0.9508

## Reproducing the Results
1. Install the required Python packages:
```bash
pip install -r requirements.txt
```

2. Open the notebook:
notebooks/SIT307_11.1HD.ipynb

3. Run all cells from top to bottom.
The notebook reproduces the original classifiers and stacking ensemble,
performs the duplicate and group-aware validation experiments, and implements
the proposed fully group-aware stacking approach.

## Key Findings
The published stacking model reports 98.53% accuracy, while the reproduced random-split stacking model achieved 98.54%.
However, 97.07% of the original test observations had an identical feature pattern in the training set. When identical feature groups were prevented from crossing the train-test boundary, stacking accuracy decreased to 87.92%.
The proposed fully group-aware stacking method also achieved 87.92% accuracy and an AUC of 0.9508. Its main contribution is therefore a more rigorous and leakage-resistant evaluation procedure rather than an increase in headline accuracy.

## Status
Implementation, reproduction, critical analysis, and Part 2 proposed solution completed.


