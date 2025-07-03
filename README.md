# Confidence-Based Prediction Optimization 

This repository provides a Jupyter notebook demonstrating a **general method for optimizing machine learning models to make confident predictions**. The approach is designed to be adaptable across domains where it is important to distinguish between high-confidence and uncertain predictions, supporting robust and trustworthy decision-making.

## Method Overview

The goal is to train models that not only maximize accuracy, but also **prioritize confident predictions**—clearly identifying cases where the model is highly certain, and flagging uncertain cases for further review. This is achieved through:

- A custom **shifted quadratic loss function** that encourages the model to make more confident predictions.
- A custom scoring metric that rewards correct, high-confidence outputs.
- A two-threshold strategy to separate confident positive, confident negative, and uncertain predictions.

The workflow includes:

- Data preprocessing and splitting into train, validation, and test sets.
- Hyperparameter tuning using grid search with a custom scoring function.
- Model evaluation on an independent test set with metrics such as accuracy, AUROC, AUPRC, and precision-recall analyses.
- Threshold analysis to optimize positive and negative predictive values (PPV and NPV), and to quantify the proportion of high-confidence predictions.

## Two-Threshold Approach and Handling Uncertainty

This model applies a **two-threshold decision strategy** to enhance reliability and safety in automated predictions:

- **Confident Negative:** Predictions with probability below 5% (confidence ≥ 95%) are classified as confidently negative.
- **Confident Positive:** Predictions with probability at or above 80% are classified as confidently positive.
- **Uncertain Zone:** Predictions between these thresholds are considered uncertain and are flagged for human or expert review.

This approach allows the model to abstain from making a decision when confidence is low, ensuring that only high-certainty predictions are automated, while ambiguous cases are reviewed by human experts. This is especially valuable in high-stakes applications such as healthcare, finance, or safety-critical systems.

## General Application

The approach is **domain-agnostic** and can be applied to any binary classification problem where confident decision-making is essential.

## How to Use

- Replace the placeholder dataset with your own data and specify the appropriate target variable.
- Run the notebook to preprocess data, train the model, tune hyperparameters, and evaluate performance.
- Use the threshold analysis plots to select decision thresholds aligned with your priorities.

## Example: Application to ENT Surgery Triage

As an example, this method was applied to predict surgical triage in an ENT (Ear, Nose, and Throat) clinical setting. The model was trained to identify patients who are highly likely or unlikely to need surgery, while referring uncertain cases for further clinical review. This improved both the efficiency and safety of patient selection.

## Acknowledgements

This work is a collaboration between Alexandra-Catalina Negoita, Prof. Santiago Romero-Brufau, Valentina Carducci, and Doug Snyder.
