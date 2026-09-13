The **Out-of-Bag (OOB) Evaluation** mechanism is a convenient and efficient way to assess the performance of an ensemble model trained using the [[Bagging and Pasting]] technique. This method **allows for model validation without setting aside a separate validation set.**

OOB evaluation relies entirely on the nature of **bagging** (Bootstrap Aggregating), where predictors are trained on subsets of the training data sampled _with replacement_ (bootstrapping).

Here is a detailed explanation of OOB evaluation:

### 1. Definition of Out-of-Bag Instances

Since bagging involves sampling the training instances _with replacement_ for each individual predictor, some instances are inevitably left out of the subset used for training that specific predictor.

- The instances that are **not sampled** for a given predictor's training are referred to as **out-of-bag (oob) instances**.
- On average, because of the sampling-with-replacement process, only about **63%** of the total training instances are sampled for each predictor.
- Consequently, the remaining **37%** of the training instances are considered OOB for that specific predictor.
- It is important to note that the 37% of instances left out are generally **not the same** for every single predictor in the ensemble.

### 2. Mechanism and Purpose

The primary advantage of OOB instances is that they act as a **free validation set**: since a predictor never observes its OOB instances during its own training phase, those instances can be used to evaluate that predictor.

The full ensemble's performance can then be evaluated by **averaging out the OOB evaluations of each predictor**.

This technique eliminates the need for partitioning the original dataset into separate training and validation sets, allowing the model to be trained using a larger portion of the available data while still providing a robust estimate of generalization error.

### 3. Implementation in Scikit-Learn

In Scikit-Learn, OOB evaluation is integrated into the `BaggingClassifier` class (and presumably `BaggingRegressor`):

- To activate this mechanism, the hyperparameter `oob_score` must be set to **`True`** when creating the `BaggingClassifier`.
- The resulting evaluation score (typically accuracy for a classifier) is automatically computed after training and can be retrieved via the **`oob_score_`** instance variable.
- The OOB score often provides an estimate of the ensemble's performance on the test set that is "close enough" to the actual accuracy achieved on the test set.

If the base estimator used within the bagging ensemble supports the `predict_proba()` method (like a Decision Tree Classifier), the OOB evaluation also provides access to the **OOB decision function** through the **`oob_decision_function_`** variable. This function returns the class probabilities for each training instance, based on the votes of the predictors for which that instance was OOB.

### OOB Context and Bagging Preference

Bagging is often preferred over pasting (sampling without replacement) because **bootstrapping introduces more diversity** in the subsets used for training each predictor. While this results in slightly higher bias, the greater diversity leads to less correlated predictors, which ultimately results in a **lower overall variance** for the ensemble. The ability to perform convenient internal cross-validation through OOB evaluation adds another practical benefit to choosing bagging.

### Related Links
[[Ensemble Learning]] - [[Decision Trees]] - [[Random Forests]] - [[Bagging and Pasting]]
