Total [[Generalization]] error of the machine learning model can be analyzed as the sum of three types of error components: 
1. Bias
2. Variance 
3. Irreducible Error


*This relationship between the model complexity and these errors is known as the Bias/Variance Tradeoff. The key is to find the right balance*


| error component   | Cause                                                                                                                                            | Model complexity connection                                                       | Resulting problem                                                                  |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| Bias              | This part of the error is due to **wrong assumptions** made by the model. For example, assuming the data is linear when it is actually quadratic | **High-bias models** are typically **too simple**                                 | **Underfitting** the training data                                                 |
| Variance          | This part of the error is due to the model's **excessive sensitivity** to small variations in the training data                                  | **High-variance models** tend to be complex, often having many degrees of freedom | **Overfitting** the training data                                                  |
| Irreducible Error | This is the error due to the **inherent noisiness** of the data itself                                                                           | This error cannot be reduced by changing the model                                | It can only be addressed by cleaning up the data (e.g., removing noise or outliers |
The Tradeoff

There is an unavoidable tension between bias and variance:

• If you **increase a model's complexity** (e.g., using a high-degree polynomial model), you generally **reduce bias** but **increase variance**.

• If you **reduce a model's complexity** (e.g., via regularization), you generally **increase bias** but **reduce variance**.

The ***goal*** is to select a model that is:

1. Complex enough to capture the underlying patterns (resulting in low bias).

2. Simple enough not to be overly sensitive to the noise in the training data (resulting in low variance).

### Related Links
[[Generalization]] - [[Cross Validation]] - [[Holdout Validation]] - [[GRID SEARCH]] - [[Early stopping]] - [[Root Mean Squared Error (RMSE)]] - [[Feature Scaling]] - [[Min-max scaling]] - [[pseduinverse of matrix]] - [[Computational Complexity]] - [[Base estimators and transformer Mixin]] - [[TF-IDF]]
