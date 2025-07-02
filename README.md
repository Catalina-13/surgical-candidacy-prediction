# Predictive Model for ENT Surgery Adjustment

This repository contains a Jupyter notebook implementing a **customized machine learning model** designed to predict surgical triage in an ENT (Ear, Nose, and Throat) clinical setting.

## Project Overview

The goal is to build a predictive model that supports clinical decision-making by identifying patients who may require surgical intervention, leveraging a tailored loss function and scoring metric to prioritize confident predictions.

The model uses a custom **shifted quadratic loss function** integrated into an XGBoost classifier wrapped for compatibility with scikit-learn tools. The workflow includes:

- Data preprocessing and splitting into train, validation, and test sets.
- Hyperparameter tuning using grid search with a custom scoring function.
- Model evaluation on an independent test set with metrics such as accuracy, AUROC, AUPRC, and precision-recall analyses.
- Threshold analysis to optimize positive and negative predictive values (PPV and NPV).

## Two-Threshold Approach and Handling Uncertainty

This model applies a **two-threshold decision strategy** to improve clinical utility and safety:

- Patients with **less than 5% predicted probability** (confidence of at least 95%) are classified as **confidently not needing surgery**.
- Patients with **greater than or equal to 80% predicted probability** are classified as **confidently needing surgery**.

Patients with predicted probabilities **between these two thresholds represent uncertain cases** where the model’s confidence is insufficient for a definitive decision. These cases are flagged for **review by human clinical experts**, ensuring that uncertain predictions receive careful consideration and additional clinical judgment.

This approach aligns with best practices in medical machine learning, where **quantifying and communicating uncertainty is critical** for safe and trustworthy clinical decision-making. By allowing the model to abstain on uncertain cases, clinicians can focus on high-confidence predictions while carefully evaluating ambiguous cases, improving overall patient safety and care quality.

## Application to ENT Case

The model is applied to an ENT dataset to predict the need for surgical adjustments, aiming to improve patient outcomes by identifying confident true positives and true negatives. This approach helps clinicians prioritize cases and optimize treatment plans.

## Usage

- Replace the placeholder dataset with your own data.
- Run the notebook to preprocess data, train the model, tune hyperparameters, and evaluate performance.
- Use the threshold analysis plots to select decision thresholds aligned with your priorities.

## Acknowledgements

This work is a collaboration between Alexandra-Catalina Negoita, Prof. Santiago Romero-Brufau, Valentina Caducei, and Doug Snyder.
