**Least Absolute Shrinkage and Selection Operator Regression (simply called Lasso Regression)**


## Explanation of Lasso Regression

**Lasso Regression** (short for Least Absolute Shrinkage and Selection Operator Regression) is a **regularised version of [[Linear Regression]]**. It is one of the three main methods—along with [[Ridge Regression]] and Elastic Net—used to constrain the weights of a linear model, thereby mitigating the risk of **overfitting**.

The primary mechanism by which Lasso Regression achieves regularization is by adding a penalty term to the Linear Regression cost function (Mean Squared Error, MSE). This regularization term uses the **$\ell_1$ norm of the weight vector**.

### The Role of $\alpha$

- The extent of regularization applied is controlled by the hyperparameter $\alpha$.
- The learning algorithm is forced to fit the data while simultaneously keeping the model weights as small as possible.

### Key Characteristic: Feature Selection

A critical and highly advantageous characteristic of Lasso Regression is its tendency to **completely eliminate the weights of the least important features** by setting them precisely to zero.

This means that Lasso Regression **automatically performs feature selection**. When a model uses Lasso, it outputs a **sparse model**—one that contains only a few non-zero feature weights. This capability is useful if you suspect that only a few of the input features are truly relevant for making predictions.

For instance, if a high-degree polynomial model is trained using Lasso regularization and a small $\alpha$ value (e.g., $\alpha = 10^{-7}$), the resulting prediction may look quadratic or almost linear because the weights corresponding to the high-degree polynomial features are set to zero.

---

## Detailed Notes on Lasso Regression

### 1. Mathematical Formulation (Cost Function)

The cost function for Lasso Regression is the Mean Squared Error (MSE) plus the $\ell_1$ regularization term:

$$\text{J}(\theta) = \text{MSE}(\theta) + \alpha\sum_{i = 1}^{n} |\theta_i|$$

- The regularization term sums the absolute values of the feature weights ($\theta_i$).
- Note that the **bias term ($\theta_0$) is typically not regularised**; the summation starts from $i=1$.

### 2. Algorithmic Implementation Challenges

#### Non-Differentiability

The Lasso cost function presents a challenge for optimisation algorithms like Gradient Descent because it is **not differentiable at $\theta_i = 0$** (for $i = 1, 2, \dots, n$).

#### Use of Subgradients

Despite the non-differentiability at zero, Gradient Descent can still work effectively if a **subgradient vector** is used when any $\theta_i$ equals zero.

The subgradient vector $\mathbf{g}$ used for Gradient Descent with the Lasso cost function is given by:

$$\mathbf{g}(\theta, \text{J}) = \nabla_\theta \text{MSE}(\theta) + \alpha \begin{pmatrix} \text{sign}(\theta_1) \ \text{sign}(\theta_2) \ \vdots \ \text{sign}(\theta_n) \end{pmatrix}$$

Where the sign function is defined as: $$\text{sign}(\theta_i) = \begin{cases} -1 & \text{if } \theta_i < 0 \ 0 & \text{if } \theta_i = 0 \ +1 & \text{if } \theta_i > 0 \end{cases}$$

#### Convergence Behavior

When using Batch Gradient Descent (BGD) on the Lasso cost function, the path tends to **bounce across the "gutter"** (where weights are close to zero) toward the end due to the abrupt change in slope at $\theta_i = 0$. To achieve convergence to the global minimum, the learning rate must be **gradually reduced**.

### 3. Practical Considerations and Comparison

#### Feature Scaling

Lasso Regression, like most regularised models, is sensitive to the scale of the input features. It is important to scale the data (e.g., using a `StandardScaler`) before performing Lasso Regression.

#### Comparison to Ridge Regression (L2 Norm)

Lasso regularization uses the $\ell_1$ norm (sum of absolute weights), whereas Ridge Regression uses the square of the $\ell_2$ norm ($\frac{1}{2} | \mathbf{w} |_2^2$).

While both push weights towards zero, the key distinction is that the $\ell_1$ penalty (Lasso) is designed to eliminate weights completely (feature selection), while the $\ell_2$ penalty (Ridge) only shrinks weights toward zero without necessarily eliminating them entirely.

#### Comparison to [[Elastic Net]]


Elastic Net represents a middle ground between Ridge and Lasso Regression, where the regularization term is a mix of both the $\ell_1$ and $\ell_2$ regularization terms.

**[[Elastic Net]] is generally preferred over Lasso**. Lasso may behave erratically, especially when either of the following conditions is true:

1. The number of features ($n$) is greater than the number of training instances ($m$).
2. Several features are strongly correlated.

Therefore, while plain Linear Regression is generally avoided (as some regularization is almost always preferable), **[[Ridge Regression]] is a good default**, but if sparsity is suspected (i.e., only a few features are useful), Elastic Net is preferred over Lasso.

### 4. Scikit-Learn Implementation

In Scikit-Learn, Lasso Regression can be implemented using:

- The `Lasso` class.
- The `SGDRegressor` class by setting the `penalty` hyperparameter to `"l1"`.

### Related Links
[[Linear Regression]] - [[Logistic Regression]] - [[Logistic Regression 1]] - [[Polynomial regression]] - [[Ridge Regression]] - [[Elastic Net]] - [[Softmax Regression]] - [[softmax regression 1]]
