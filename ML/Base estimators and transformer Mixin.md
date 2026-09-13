# Base Estimators and TransformerMixin
In the Scikit-Learn framework, all objects share a highly consistent and heavily optimized API driven by inheritance from core base classes. 

## BaseEstimator
Any object that estimates some parameters based on a dataset is an estimator. If you create custom models, inheriting from `sklearn.base.BaseEstimator` avoids the need to write `get_params()` and `set_params()` methods yourself. These are required if you want your custom model to be compatible with `GridSearchCV` and pipelining.

## TransformerMixin
Transformers are estimators that additionally transform a dataset. By inheriting from `sklearn.base.TransformerMixin` and implementing `fit()` and `transform()`, Scikit-Learn will automatically provide you with the `fit_transform()` method. 

```python
from sklearn.base import BaseEstimator, TransformerMixin

class CustomTransformer(BaseEstimator, TransformerMixin):
    def fit(self, X, y=None):
        return self # nothing else to do
    
    def transform(self, X, y=None):
        return X ** 2
```
This design is what allows the `Pipeline` class to easily chain arbitrary preprocessing steps together seamlessly.

### Related Links
[[Bias-Variance Tradeoff]] - [[Generalization]] - [[Cross Validation]] - [[Holdout Validation]] - [[GRID SEARCH]] - [[Early stopping]] - [[Root Mean Squared Error (RMSE)]] - [[Feature Scaling]] - [[Min-max scaling]] - [[pseduinverse of matrix]] - [[Computational Complexity]] - [[TF-IDF]]
