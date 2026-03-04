related- [[Ensemble Learning]],[[Decision Trees]]
- These techniques involve training the same learning algorithm on different random subsets of the training set to create a diverse set of classifiers. 
- The ensemble's final prediction is determined by aggregating the predictions of all individual predictors, typically using the statistical mode (most frequent prediction) for classification tasks or the average for regression tasks.

### 1. Definitions and Mechanisms

**Bagging (Bootstrap Aggregating/Bootstrapping)**:

- Bagging is a method where sampling of the training set is performed **with replacement**.
- The name "bagging" is short for **bootstrap aggregating**.
- Since sampling is performed with replacement (known in statistics as **bootstrapping**), **individual instances may be sampled several times for the same predictor.** 
- ==Consequently, only about 63% of the training instances are sampled on average for each predictor.==
- Bagging increases diversity in the subsets used for training each predictor compared to pasting.

**Pasting**:

- Pasting is a method where sampling of the training set is performed **without replacement**.
- When using pasting, instances may still be sampled multiple times across _different_ predictors, but they cannot be sampled several times for the _same_ predictor.

### 2. Implementation in Scikit-Learn

Scikit-Learn implements both bagging and pasting using the `BaggingClassifier` class (or `BaggingRegressor` for regression):

- To use **bagging**, the `bootstrap` hyperparameter is set to `True` (the default value).
- To use **pasting**, the `bootstrap` hyperparameter must be set to `False`.

The `BaggingClassifier` automatically utilizes soft voting (if the base classifier supports estimating class probabilities via a `predict_proba()` method) instead of hard voting.

The sources provide an example of training an ensemble of 500 Decision Tree classifiers using bagging (where sampling is with replacement, `bootstrap=True`), with each tree trained on 100 randomly sampled instances:

```
bag_clf = BaggingClassifier(
    DecisionTreeClassifier(), n_estimators=500,
    max_samples=100, bootstrap=True, n_jobs=-1)
bag_clf.fit(X_train, y_train)
y_pred = bag_clf.predict(X_test)
```


![[Pasted image 20251116172524.png]]
- The following code trains an ensemble of 500 Decision Tree classifiers,5 each trained on 100 training instances ran domly sampled from the training set with replacement .
- The n_jobs param eter tells Scikit-Learn the number of CPU cores to use for training and predictions (–1 tells Scikit-Learn to use all available cores):


### 3. Impact on Bias and Variance

Both bagging and pasting generally result in an ensemble that has a **similar bias but a lower variance** compared to a single predictor trained on the entire original training set.

**Bagging vs. Pasting Trade-offs**:

- **Bagging** introduces more diversity in the training subsets because of sampling with replacement (bootstrapping). This generally leads to a slightly **higher bias** for the ensemble.
- However, this increased diversity means the individual predictors are **less correlated**, resulting in a further **reduction in the overall variance** of the ensemble.
- Overall, bagging often produces better models, which is why it is generally preferred over pasting.

If computational resources allow, it is recommended to use **cross-validation** to evaluate both bagging and pasting to select the method that works best for a specific dataset.

### 4. Computational Efficiency

A major advantage of both bagging and pasting is that the individual predictors can be trained **in parallel** (using different CPU cores or servers). Predictions can also be made in parallel. This characteristic makes them highly scalable and popular methods.

In contrast, other ensemble methods like **Boosting** train predictors sequentially, which limits parallelization and thus scaling.

### 5. Out-of-Bag (OOB) Evaluation (Specific to Bagging)

Because bagging samples the training instances with replacement (bootstrapping), some instances are not sampled for a given predictor; these are called **out-of-bag (oob) instances**.

- On average, about 37% of the training instances are left out for each predictor.
- Since a predictor never sees its OOB instances during training, these instances can be used to evaluate that predictor.
- The entire ensemble can be evaluated by averaging the OOB evaluations of each predictor, eliminating the need for a separate validation set.

In Scikit-Learn, this evaluation is requested by setting `oob_score=True` in `BaggingClassifier`. The resulting score is accessed via the `oob_score_` instance variable.

---

**Analogy for Bagging and Pasting**:

Imagine you are trying to guess the location of a sunken treasure (the ideal model).

- **Training a single model** is like sending one expert diver down to search the seabed. They might be very skilled, but they only cover one specific area, and if they miss the spot, you're out of luck (high variance, prone to error).
- **Bagging** is like sending ten different teams of divers, but because some divers are on multiple teams, the overall search effort is robust to individual bad decisions and biases. Each team focuses on a slightly different, randomized version of the map (sampling with replacement/bootstrapping). Even if one team misinterprets its map or has a bad day, averaging the search locations from all ten teams leads to a much more reliable final location (lower variance).
- **Pasting** is similar, but each diver is assigned exclusively to one team (sampling without replacement). This guarantees broader coverage but provides slightly less diversity across the teams' efforts.