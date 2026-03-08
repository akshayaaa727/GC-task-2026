

# Concrete Compressive Strength Analysis using AdaBoost.R2

## 1. Project Overview

This project predicts the compressive strength of concrete based on its chemical composition and age. It features a custom "from-scratch" implementation of the **AdaBoost.R2** algorithm, compared against the standard Scikit-Learn library.

## 2. Dataset & Preprocessing

* **Source:** UCI Machine Learning Repository (Concrete Compressive Strength Dataset).
* **Cleaning:** Identified and removed **25 duplicate entries** to ensure unbiased testing.
* **Imputation:** Zero missing values were found across all features (Cement, Water, Age, etc.).
* **Splitting:** Data was split into **70% Training**, **15% Validation**, and **15% Testing** sets.

## 3. Data Insights (EDA)

* **Age Correlation:** A strong non-linear relationship exists where concrete strength gains are most rapid in the first 28 days.
* **Water Content:** Observed a negative correlation with strength, confirming that excess water weakens the cement matrix (Abrams' Law).
* **Feature Influence:** Cement content remains the most significant positive predictor of final strength.

## 4. Implementation Details

* **Weak Learner:** Decision Tree "stumps" (`max_depth=1`) were used as individual regressors to build the ensemble.
* **Optimization:** Evaluated $M$ (number of learners) from 5 to 10,000 using the validation set.
* **Optimal M:** Selected **$M = 60$** as the optimal point before the $R^2$ score plateaued.

## 5. Performance Comparison

The models were evaluated using the $R^2$ (Coefficient of Determination) score on unseen test data:

| Implementation | Test $R^2$ Score |
| --- | --- |
| **Custom From-Scratch** | **0.4417** |
| **Scikit-Learn** | **0.4428** |

## 6. Conclusions

* **Accuracy:** The near-identical $R^2$ scores (0.0011 difference) validate the mathematical correctness of the from-scratch weighted median logic.
* **Model Depth:** The score of $\approx 0.44$ indicates that while AdaBoost captures general trends, simple stumps struggle to model the complex chemical interactions of concrete perfectly.
