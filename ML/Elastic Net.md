
**Elastic Net** is a form of regularized Linear Regression that represents a **middle ground between Ridge Regression and Lasso Regression**. 
- It combines the penalty terms from both methods to achieve a model that benefits from the strengths of both L1 and L2 regularization.

### Mechanism of Combination

The core mechanism involves mixing the $\ell_1$ penalty (from Lasso) and the $\ell_2$ penalty (from Ridge) into the cost function.

This mix is governed by a hyperparameter known as the **mix ratio**, $r$ (or $l1_ratio$ in Scikit-Learn):

- If the mix ratio $r$ is set to **0**, the Elastic Net regularization term vanishes, and the model is equivalent to **Ridge Regression**.
- If the mix ratio $r$ is set to **1**, the Elastic Net regularization term is purely the L1 norm, and the model is equivalent to **Lasso Regression**.

### Key Benefits

1. **Regularization (Overfitting Reduction):** Like all regularized linear models, Elastic Net constrains the weights of the model, which makes the model simpler and helps reduce the risk of **overfitting**.
2. **Feature Selection:** Since it includes the $\ell_1$ (Lasso) penalty, Elastic Net retains the valuable ability to perform **automatic feature selection**, driving the weights of the least important features down to exactly zero, resulting in a sparse model.
3. **Stability in Complex Scenarios:** Elastic Net addresses certain erratic behaviors that Lasso Regression can exhibit when dealing with complex datasets. This is the primary reason why **Elastic Net is generally preferred over Lasso**.

---

## Detailed Notes on Elastic Net

### 1. Context and Preference

- Elastic Net is categorised as one of the **regularized linear models** used to constrain weights and thus reduce the risk of overfitting the training data.
- It is a **middle ground** between [[Ridge Regression]] and [[Lasso Regression]]
- It is generally recommended to **avoid plain Linear Regression** in favour of models with at least a little regularization.
- **Ridge Regression is considered a good default** regularization method.
- If one suspects that **only a few features are actually useful** (i.e., desiring a sparse model), then Elastic Net or Lasso should be preferred over Ridge, because they tend to reduce the useless features’ weights down to zero.
- **Elastic Net is generally preferred over Lasso**.

### 2. Situations Where Elastic Net Excels Over Lasso

Lasso Regression may behave **erratically** under two specific conditions, making Elastic Net the more stable alternative:

1. When the **number of features ($n$) is greater than the number of training instances ($m$)**.
2. When **several features are strongly correlated**.

### 3. Cost Function Formulation

The Elastic Net cost function combines the Mean Squared Error (MSE) with a mix of the $\ell_1$ (Lasso) and $\ell_2$ (Ridge) regularization terms.

The cost function $J(\theta)$ is given by Equation 4-12:

$$\text{J}(\theta) = \text{MSE}(\theta) + r\alpha\sum_{i = 1}^{n} |\theta_i| + \frac{1 - r}{2} \alpha\sum_{i = 1}^{n} \theta_i^2$$

- The term $r\alpha\sum_{i = 1}^{n} |\theta_i|$ represents the **Lasso ($\ell_1$) regularization term**.
- The term $\frac{1 - r}{2} \alpha\sum_{i = 1}^{n} \theta_i^2$ represents the **Ridge ($\ell_2$) regularization term**.
- $\alpha$ is the hyperparameter that controls the **overall amount of regularization** applied.
- $r$ is the **mix ratio** hyperparameter that controls the balance between the $\ell_1$ and $\ell_2$ components.
- As with Ridge and Lasso, the **bias term ($\theta_0$) is not regularised**; the summation starts at $i=1$.

### 4. Scikit-Learn Implementation

- In Scikit-Learn, Elastic Net is implemented via the `ElasticNet` class.
- The mix ratio $r$ corresponds to the **`l1_ratio`** parameter in the Scikit-Learn implementation.

A short example of using Elastic Net in Scikit-Learn involves setting the overall regularization strength ($\alpha$) and the mix ratio ($l1_ratio$):

```
>>> from sklearn.linear_model import ElasticNet
>>> elastic_net = ElasticNet(alpha=0.1, l1_ratio=0.5)
>>> elastic_net.fit(X, y)
```

### Related Links
[[Linear Regression]] - [[Logistic Regression]] - [[Logistic Regression 1]] - [[Polynomial regression]] - [[Ridge Regression]] - [[Lasso Regression]] - [[Softmax Regression]] - [[softmax regression 1]]
