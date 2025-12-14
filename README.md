# Skin Cancer Detection Optimization using Genetic Algorithms

![License](https://img.shields.io/badge/license-MIT-blue.svg) ![Python](https://img.shields.io/badge/python-3.8%2B-blue) ![Scikit-Learn](https://img.shields.io/badge/library-scikit--learn-orange)

## Project Overview

Early detection of skin cancer is critical for patient prognosis. Medical datasets often contain high-dimensional data with redundant or irrelevant features that can hinder model performance and interpretability.

This project implements a **Genetic Algorithm (GA)** from scratch to perform **Feature Selection**. The goal is to identify the optimal subset of clinical and image-derived features to maximize the predictive performance of a machine learning classifier (Random Forest) on a binary classification task (Malignant vs. Benign).

## Key Results

By evolving a population of feature subsets over several generations, the algorithm achieved significant improvements over the baseline models trained on the full dataset.

| Metric | Baseline (All 40 features) | Genetic Algorithm (Best Individual) | Improvement |
| :--- | :---: | :---: | :---: |
| **F1-Score** | 82.4% | **90.8%** | +8.4% |
| **Accuracy** | 0.88 | **0.92** | +4.0% |
| **Feature Count**| 40 | **18** | -55% (Reduction) |

*The best model retained only 18 relevant features out of 40, effectively reducing noise and computational cost.*

## Methodology

The project follows a bio-inspired optimization pipeline:

1.  **Preprocessing:** One-Hot Encoding and data splitting (Train/Test).
2.  **Baseline Evaluation:** Comparison of Logistic Regression, SVM, KNN, and Random Forest.
3.  **Genetic Algorithm Implementation:**
    * **Encoding:** Binary chromosome representation (1 = feature selected, 0 = ignored).
    * **Fitness Function:** F1-Score/Accuracy of a Random Forest trained on the selected subset.
    * **Selection:** Tournament & Sorting-based selection.
    * **Crossover:** Multi-point crossover.
    * **Mutation:** Random bit-flipping to maintain diversity.
    * **Replacement:** Elitist strategy (preserving top performers).
