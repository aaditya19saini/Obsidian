Cross-validation is a crucial technique used in Machine Learning to evaluate a model's performance and generalization ability. It is frequently used for selecting models and tuning hyperparameters.

### What Is Cross-Validation?

Cross-validation is an evaluation strategy that estimates how well a model will **generalize to new cases**.

- The only way to determine how well a model performs on new data (its generalization error) is to test it on instances it has never seen before. 

- While simply holding out a separate test set works well for a final evaluation, it introduces problems when selecting models or tuning hyperparameters.

- If you measure generalization error multiple times on a single test set and adapt the model based on those results, the resulting error estimate will be **too optimistic**, and the final model is unlikely to perform as well on truly new, unknown data.

To solve this, cross-validation provides a method for **better evaluation** by generating a more accurate measure of a model's performance without contaminating the final test set.

### Advantages over single validation 
Cross-validation offers several advantages over using a single validation set:

- **Accuracy of Performance Estimate:** By averaging out multiple evaluations, cross-validation provides a **much more accurate measure** of a model's performance.
- **Precision Measure:** It allows you to obtain not only an estimate of the performance but also a **measure of how precise that estimate is** (i.e., its standard deviation).

### How Cross-Validation Is Performed (K-fold Cross-Validation)

The sources detail **K-fold cross-validation** as a widely used method in Scikit-Learn.

1. **Splitting the Training Set into Folds:** The training set is randomly divided into $K$ distinct subsets, which are called **folds**.     For example, $K$ is often set to 10 ($10$-fold cross-validation).
2. **Iterative Training and Evaluation:** The model is trained and evaluated $K$ times:
    - In each iteration, a **different fold is picked for evaluation**, serving as a temporary validation set.
    - The model is trained on the **remaining $K-1$ folds**.
3. **Aggregation of Results:** The result is an array containing the $K$ evaluation scores. By averaging these scores, you obtain a highly accurate measure of the model's performance.

**Example Implementation (Scikit-Learn):** Scikit-Learn provides the `cross_val_score()` function to perform $K$-fold cross-validation. For example, using `cv=10` splits the training set into 10 folds and returns 10 scores.

**Note on Scoring:** Scikit-Learn's cross-validation features expect a utility function (where "greater is better") rather than a cost function (where "lower is better"). Therefore, if evaluating a measure like Mean Squared Error (MSE), the evaluation is performed using the negative MSE, and the sign must be flipped before taking the square root to calculate RMSE.

### Alternatives and Related Techniques

The sources discuss several variants and related applications of cross-validation:

#### 1. [[Holdout Validation]]

This is the simplest solution to the issue of testing on the same set used for tuning. You **hold out part of the original training set** to act as a **validation set** (or _dev set_).

- You train candidate models on the _reduced training set_ (full training set minus the validation set).
- You select the model that performs best on the validation set.
- The best model is then retrained on the _full training set_ (including the validation set) to create the final model.
- Finally, the generalization error is estimated using the **test set**, which was kept untouched.

A major drawback of this method is the size tradeoff:

- If the validation set is **too small**, model evaluations may be imprecise, leading to the selection of a suboptimal model.
- If the validation set is **too large**, the reduced training set is significantly smaller than the full training set, making the comparison of candidate models trained on this small set inaccurate for the final model trained on the full set.

##### How is the size of validation set determined?


#### 2. [[Repeated Cross-Validation]]

This technique is a solution to the instability caused by a single, small validation set. In repeated cross-validation, multiple small validation sets are used. Each model is evaluated once per validation set after being trained on the rest of the data. The trade-off here is that the training time is multiplied by the number of validation sets used.

#### 3. Stratified K-Fold

When dealing with classification problems, particularly those with skewed datasets (where some classes are much more frequent than others), the `StratifiedKFold` class ensures that the folds used in cross-validation contain a **representative ratio of each class**. It performs stratified sampling to maintain class proportions across all folds.

### Applications of Cross-Validation

Cross-validation is primarily used during the **model selection** phase of a project:

- **Hyperparameter Tuning:** It is used extensively in systematic searches like **Grid Search** (`GridSearchCV`) to evaluate combinations of hyperparameter values. For instance, `GridSearchCV` trains a model multiple times using cross-validation (e.g., 5-fold cross-validation) for every hyperparameter combination specified.
- **Comparing Models:** It is the standard way to compare different model types (e.g., Linear Regression vs. Decision Tree) to determine which is overfitting or underfitting.
- **Soft Voting Ensembles:** The `predict_proba()` method for soft voting requires classifiers to estimate class probabilities, often requiring them to use cross-validation internally.
- **Cross-Validation Prediction (`cross_val_predict`):** This function performs K-fold cross-validation but returns the **predictions made on each test fold** instead of the evaluation scores. This results in a "clean prediction" for every instance in the training set (meaning the prediction was made by a model that never trained on that instance), which is useful for generating a Confusion Matrix or inspecting decision scores.