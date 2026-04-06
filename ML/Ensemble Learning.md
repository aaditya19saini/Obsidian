**Ensemble Learning** is a machine learning technique that involves aggregating the predictions of a group of predictors (called an ensemble) to achieve better results than the best individual predictor. This concept is often referred to as the "wisdom of the crowd".

### Voting Classifiers

One simple method is to train diverse classifiers and aggregate their predictions:

- **Hard Voting:** The ensemble predicts the class that receives the majority of votes from the individual classifiers.
- **Soft Voting:** If the classifiers can estimate class probabilities, the ensemble predicts the class with the highest probability, averaged over all individual classifiers. This often yields better results than hard voting as it gives more weight to highly confident votes.

Even if the individual predictors are **weak learners** (only slightly better than random guessing), the ensemble can become a **strong learner** provided there are enough predictors and they are sufficiently diverse and independent.

### [[Bagging and Pasting]]

This approach involves using the _same_ training algorithm for every predictor but training them on different random subsets of the training set.

- **Bagging (Bootstrap Aggregating):** Sampling is performed **with replacement**.
- **Pasting:** Sampling is performed **without replacement**.

These methods effectively reduce **variance** while keeping bias comparable to a single predictor. A major advantage is that predictors can be trained in **parallel**, making the method highly scalable. Bagging also allows for **Out-of-Bag (OOB) evaluation**, where the model is validated on the instances that were not sampled during training.

### Boosting

Boosting refers to ensemble methods that combine several weak learners into a strong learner by training predictors **sequentially**, with each new predictor trying to **correct its predecessor**.

- **AdaBoost:** Each new predictor pays more attention to the training instances that the previous predictor underfitted (misclassified) by increasing their relative weights.
- **Gradient Boosting:** Instead of tweaking weights, this method tries to fit the new predictor to the **residual errors** made by the previous predictor.

Because boosting trains predictors sequentially, it cannot be parallelised and does not scale as well as bagging.

### Stacking

**Stacking** (Stacked Generalization) is based on the idea that instead of using a trivial function (like hard voting) to aggregate predictions, one should **train a model** to perform this aggregation. The final predictor, called a **blender** or meta-learner, takes the predictions of the other predictors as inputs and makes the final prediction.

### Related Links
[[Decision Trees]] - [[Random Forests]] - [[Bagging and Pasting]] - [[Out of bag Evaluation]]
