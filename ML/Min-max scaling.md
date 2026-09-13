**MinMaxScaler** is a transformer provided by Scikit-Learn used for [[Feature Scaling]], a technique often referred to as **normalization**.

It functions by shifting and rescaling numerical attributes so that they end up ranging from **0 to 1**. The calculation involves subtracting the minimum value from each data point and then dividing by the difference between the maximum and minimum values (the range).

Key features include:

- **Custom Ranges:** While the default target range is 0 to 1, you can use the `feature_range` hyperparameter to specify a different range if required.
- **Sensitivity to Outliers:** Compared to standardization (which subtracts the mean and divides by the standard deviation), min-max scaling is more sensitive to outliers.
- For example, if a dataset has a single extreme outlier, **MinMaxScaler** may crush all other values into a very small range.


### Related Links
[[Bias-Variance Tradeoff]] - [[Generalization]] - [[Cross Validation]] - [[Holdout Validation]] - [[GRID SEARCH]] - [[Early stopping]] - [[Root Mean Squared Error (RMSE)]] - [[Feature Scaling]] - [[pseduinverse of matrix]] - [[Computational Complexity]] - [[Base estimators and transformer Mixin]] - [[TF-IDF]]
