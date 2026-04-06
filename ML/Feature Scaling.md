- **Feature scaling** is a crucial data transformation process applied to numerical input attributes in Machine Learning. 
- **primary purpose**: is to ensure that all input numerical attributes have similar scales, as most Machine Learning algorithms do not perform well when input numerical attributes have very different scales.(why?)

There are two common methods for feature scaling:

• **Min-max scaling** (often called **normalization**)- 
1. shifts and rescales values so they typically range from 0 to 1
2. performed by s**ubtracting the minimum value from each data point and then dividing by the difference between the maximum and minimum values**
3. Scikit-Learn provides a `MinMaxScaler` for this, which includes a `feature_range` hyperparameter to adjust the output range if needed.


 **DRAWBACK**: min-max scaling can be significantly affected by outliers

- standardization:
1. first subtracts the mean value from each data point, resulting in standardized values that always have a zero mean

### Related Links
[[Bias-Variance Tradeoff]] - [[Generalization]] - [[Cross Validation]] - [[Holdout Validation]] - [[GRID SEARCH]] - [[Early stopping]] - [[Root Mean Squared Error (RMSE)]] - [[Min-max scaling]] - [[pseduinverse of matrix]] - [[Computational Complexity]] - [[Base estimators and transformer Mixin]] - [[TF-IDF]]
