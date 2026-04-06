# Linear Regression
Linear regression is a foundational statistical method used to model the relationship between a scalar response (dependent variable) and one or more explanatory variables (independent variables). 

## Core Concepts
- **Hypothesis Function:** The model predicts the output $\hat{y}$ using a linear combination of features:
  $$ \hat{y} = \theta_0 + \theta_1 x_1 + \dots + \theta_n x_n $$
  or in vectorized form: $\hat{y} = h_{\theta}(\mathbf{x}) = \mathbf{\theta}^T \mathbf{x}$
- **Cost Function (MSE):** Measures the average squared difference between predictions and actual values.
  $$ J(\theta) = \frac{1}{m} \sum_{i=1}^{m} (\mathbf{\theta}^T \mathbf{x}^{(i)} - y^{(i)})^2 $$
- **Optimization:** The cost function can be minimized analytically using the **Normal Equation** or iteratively via **Gradient Descent**.

## Assumptions
1. **Linearity:** The relationship between features and the target is linear.
2. **Independence:** Observations are independent of each other.
3. **Homoscedasticity:** Constant variance of errors.
4. **Normality:** Errors are normally distributed.

### Related Links
[[Logistic Regression]] - [[Logistic Regression 1]] - [[Polynomial regression]] - [[Ridge Regression]] - [[Lasso Regression]] - [[Elastic Net]] - [[Softmax Regression]] - [[softmax regression 1]]
