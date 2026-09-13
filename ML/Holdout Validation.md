# Holdout Validation
Holdout validation is the absolute simplest form of model evaluation. It involves splitting your available dataset into two mutually exclusive sets:
1. **Training Set:** Used to train the model's parameters (usually 70-80% of data).
2. **Test (Holdout) Set:** Used exclusively to evaluate the final model's performance (usually 20-30% of data).

## Pros & Cons
- **Pros:** Fast to compute, straightforward, exactly simulates how the model will perform on completely unseen data.
- **Cons:** Highly sensitive to the specific data points that ended up in the test set. If the dataset is small, the test set might not be representative.

Because of the high variance in small datasets, **$k$-Fold Cross Validation** is often preferred over simple Holdout Validation unless the dataset is massive enough that a single holdout set is reliably representative.

### Related Links
[[Bias-Variance Tradeoff]] - [[Generalization]] - [[Cross Validation]] - [[GRID SEARCH]] - [[Early stopping]] - [[Root Mean Squared Error (RMSE)]] - [[Feature Scaling]] - [[Min-max scaling]] - [[pseduinverse of matrix]] - [[Computational Complexity]] - [[Base estimators and transformer Mixin]] - [[TF-IDF]]
