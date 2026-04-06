# Random Forests
A Random Forest is an **ensemble** of Decision Trees, typically trained via the **bagging** (Bootstrap Aggregating) method. The core principle is that a group of weak learners can form a strong learner.

## How it Works
1. **Bagging:** Train $N$ different Decision Trees on different random subsets of the training data (samples are drawn with replacement).
2. **Feature Randomness:** When finding the best split in a node, only a random subset of all features is searched. This injects further randomness, making trees more independent.
3. **Aggregation:** For a final prediction, output the **mode** of the classes (for classification) or the **mean** prediction (for regression) of all individual trees.

## Why use Random Forests?
Random Forests fundamentally address the largest weakness of single Decision Trees: **overfitting**. By averaging out multiple independent trees, the variance is heavily reduced, yielding a much more robust and generalized model out-of-the-box.

- done by bagging ([[Bagging and Pasting]])
- 

### Related Links
[[Ensemble Learning]] - [[Decision Trees]] - [[Bagging and Pasting]] - [[Out of bag Evaluation]]
