# Selecting Kernel and Tuning Hyperparameters
Support Vector Machines and kPCA rely heavily on the explicit choice of kernel and its specific hyperparameters. Because there is no generalized analytical way to know which kernel is best, we must use empirical tuning.

## Common Kernels
1. **Linear:** Use for massive datasets or datasets with huge feature spaces (like text classification). It is the fastest.
2. **RBF (Gaussian):** The default "go-to" for non-linear data.
3. **Polynomial:** Often used in image processing NLP but slower than RBF.

## Hyperparameter Grid Search
When using an RBF kernel in Scikit-Learn, two hyperparameters are strictly necessary to tune:
- **`C` (Regularization):** Controls the tradeoff between a wider margin and fewer margin violations. A smaller `C` creates a wider, softer street (more bias, less variance).
- **`gamma` ($\gamma$):** Controls the influence of a single training example. A small $\gamma$ gives a model low bias and high variance (overfitting), whereas a large $\gamma$ makes the decision boundary smoother.

We typically use `GridSearchCV` or `RandomizedSearchCV` paired with Cross-Validation to empirically find the best $(C, \gamma)$ combination.

### Related Links
[[Support Vector Machines]] - [[Dual problem]] - [[Polynomial Kernel]] - [[Kernel PCA (kPCA)]]
