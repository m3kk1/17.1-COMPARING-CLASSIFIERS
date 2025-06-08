# 17.1-COMPARING-CLASSIFIERS

Bank Marketing Classification Project

## Project Overview

This project explores the use of classification algorithms to predict whether a client will subscribe to a term deposit product following a marketing campaign. The dataset comes from a Portuguese banking institution and includes demographic, economic, and campaign-related attributes.

The business objective is to help improve marketing campaign efficiency by identifying potential clients likely to subscribe, allowing for better resource allocation in outreach efforts.

## Dataset Source

* Origin: UC Irvine Machine Learning Repository
* Target Variable: `y` — indicates whether the client subscribed to a term deposit (`yes` or `no`)
* Number of Features: 20
* Key Challenge: Class imbalance (majority class = "no")

## Modeling Approach

The following classification algorithms were evaluated using both default settings and with class balancing:

* Logistic Regression
* Decision Tree
* k-Nearest Neighbors (k-NN)
* Support Vector Machine (SVM)

Each model was evaluated on:

* Accuracy
* F1 Score
* ROC AUC

Where applicable, hyperparameters were tuned using `GridSearchCV`, and model performance was compared on both unbalanced and balanced training setups.

## Unbalanced Model Results

| Model               | Test Accuracy | F1 Score | ROC AUC |
| ------------------- | ------------- | -------- | ------- |
| Logistic Regression | 86.98%        | 0.0000   | 0.5955  |
| Decision Tree       | 85.09%        | 0.1368   | 0.5741  |
| k-NN                | 85.95%        | 0.1370   | 0.5778  |
| SVM                 | 86.98%        | 0.0000   | 0.5581  |

These models achieved high accuracy, but F1 Scores for Logistic Regression and SVM were zero, indicating that they failed to correctly classify any of the positive ("yes") responses.

## Balanced Model Results

| Model               | Test Accuracy | F1 Score | ROC AUC  |
| ------------------- | ------------- | -------- | -------- |
| Decision Tree       | \~84–85%      | \~0.26   | \~0.58   |
| k-NN                | \~85–86%      | \~0.14   | \~0.58   |
| Logistic Regression | \~60–65%      | Improved | Improved |
| SVM                 | Lower         | Improved | Improved |

When class weights were adjusted to account for imbalance, F1 Scores and ROC AUC values improved. The Decision Tree model performed best overall at identifying the positive class, while k-NN also showed moderate gains. Logistic Regression and SVM remained limited without further tuning.

## Key Takeaways

* High accuracy in imbalanced datasets does not reflect actual model performance.
* F1 Score and ROC AUC are more reliable evaluation metrics for this type of classification task.
* Decision Tree and k-NN models performed best when class imbalance was addressed.
* Class weighting was a sufficient and appropriate balancing method given the constraints of the project.

## Recommendations

* Conduct additional hyperparameter tuning and cross-validation for all models.
* Evaluate more advanced classification algorithms such as Random Forest or Gradient Boosting in future work.
* Further explore feature engineering and selection to enhance model signal.
* Consider integrating methods for class balancing such as resampling in future iterations (not implemented here due to course guidelines).

## Project Files

* Notebook: 17.1 Workbook.ipynb: Full modeling notebook with data preprocessing, modeling, evaluation, and tuning. 
            PAIIIcomparingclassifiers.ipynb: Additional notebook comparing multiple classifiers with class balancing.
* Dataset: Provided via course assignment
* Libraries: pandas, numpy, scikit-learn, seaborn, matplotlib

Business Takeaway

While some models appear highly accurate, performance drops significantly when class imbalance is accounted for. This highlights the need for careful metric selection and model evaluation. A model is only useful if it correctly identifies the rare outcomes of interest — in this case, clients who say "yes."

By comparing both unbalanced and balanced versions of the dataset, we demonstrated the importance of class distribution and proper metric use when making data-driven business decisions.
