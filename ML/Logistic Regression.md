# Logistic Regression
Despite its name, Logistic Regression is a **classification** algorithm commonly used to estimate the probability that an instance belongs to a particular class. If the estimated probability is greater than 50%, the model predicts the positive class (1).

## The Sigmoid Function
Instead of outputting a continuous value like Linear Regression, Logistic Regression passes its output through a logistics (sigmoid) function $\sigma(t)$, restricting values between 0 and 1:
$$ \sigma(t) = \frac{1}{1 + e^{-t}} $$

The estimated probability is:
$$ \hat{p} = h_{\theta}(\mathbf{x}) = \sigma(\mathbf{\theta}^T \mathbf{x}) $$

## Cost Function (Log Loss)
Because MSE is non-convex for Logistic Regression, we use the **Log Loss** (binary cross-entropy) cost function to ensure Gradient Descent finds the global minimum:
$$ J(\theta) = -\frac{1}{m} \sum_{i=1}^{m} \left[ y^{(i)} \log(\hat{p}^{(i)}) + (1 - y^{(i)}) \log(1 - \hat{p}^{(i)}) \right] $$

### Related Links
[[Linear Regression]] - [[Logistic Regression 1]] - [[Polynomial regression]] - [[Ridge Regression]] - [[Lasso Regression]] - [[Elastic Net]] - [[Softmax Regression]] - [[softmax regression 1]]
