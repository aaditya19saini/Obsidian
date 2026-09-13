# Part I: Fundamentals of Machine Learning

Based on Chapters 1-4 of Geron's book.

## 1. The Machine Learning Landscape
- **Supervised vs Unsupervised:** Labeled data (Classification/Regression) vs Unlabeled data (Clustering, Anomaly Detection).
- **Batch vs Online Learning:** Training completely offline vs incrementally feeding data instances as they arrive.
- **Instance-based vs Model-based:** Memorizing data (k-NN) vs building a mathematical model (Linear Regression).
- **Main Challenges:** Insufficient data, non-representative data, poor quality data, irrelevant features, overfitting, and underfitting.

## 2. End-to-End Project (California Housing)
The standard workflow for any Scikit-Learn project:
1. Frame the problem.
2. Get the data.
3. Explore the data (Visualizations, correlation matrices).
4. Prepare the data (Imputers, OneHotEncoders, Feature Scaling).
   - *Scikit-Learn API: `fit()`, `transform()`, `fit_transform()`, `Pipeline`.*
5. Short-list promising models.
6. Fine-Tune the system (`GridSearchCV`, `RandomizedSearchCV`).

## 3. Classification Metrics
- **Confusion Matrix:** True Positives, False Positives (Type I), True Negatives, False Negatives (Type II).
- **Precision:** $TP / (TP + FP)$. Accuracy of positive predictions.
- **Recall (Sensitivity):** $TP / (TP + FN)$. Ratio of positive instances correctly detected.
- **F1 Score:** Harmonic mean of precision and recall.
- **ROC Curve:** Plots True Positive Rate (Recall) vs False Positive Rate ($1 - Specificity$). Area under the curve (AUC) is the key aggregate metric.

## 4. Training Models
- **Linear Regression:** Solved via Normal Equation or Gradient Descent (Batch, Stochastic, Mini-batch).
- **Polynomial Regression:** Adding powers of each feature. Prone to severe overfitting without regularization.
- **Regularization:** 
  - Ridge ($L_2$ penalty)
  - Lasso ($L_1$ penalty, yields sparse models)
  - Elastic Net (mix of both).
- **Logistic Regression:** Uses the sigmoid function for binary classification, trained via Log Loss penalty.
- **Softmax Regression:** Generalizes Logistic Regression to multi-class problems.
