**Ridge Regression is [[Linear Regression]] with a penalty for complexity**

1. **Objective (Linear Regression):** Standard Linear Regression aims to find the model parameters ($\boldsymbol{\theta}$) that minimize the **Mean Squared Error (MSE)** between the model's predictions and the actual data.
2. **Problem (Overfitting):** If a model is too complex (high variance), it can **overfit** the training data, meaning it performs well on the training set but poorly on new instances. Overfitting is countered by ==regularization—constraining the model to make it simpler.==
3. **The Ridge Constraint:** Ridge Regression regularizes the model by adding a penalty term to the [[cost function]]. This penalty term is proportional to the **square of the $\ell_2$ norm of the weight vector**.
    - This forces the learning algorithm not only to **fit the data** (minimize MSE) but also to simultaneously **keep the model weights ($\theta_i$) as small as possible**.
    - The penalty term uses the weights corresponding to the features ($\theta_1$ through $\theta_n$) but generally **excludes the bias term ($\theta_0$)**.
4. **The Result:** By constraining the feature weights to be small, Ridge Regression produces **flatter** (less extreme, more reasonable) predictions. This process **reduces the model’s variance** (reducing overfitting) while slightly **increasing its bias**.

### Key Details

- **Cost Function:** The Ridge Regression cost function includes the standard MSE plus the regularization term: $$J(\boldsymbol{\theta}) = MSE(\boldsymbol{\theta}) + \alpha \frac{1}{2} \sum_{i=1}^{n} \theta_i^2$$
- **Hyperparameter ($\alpha$):** The **hyperparameter $\alpha$** controls the **amount of regularization** applied.
    - If $\alpha = 0$, Ridge Regression is identical to plain Linear Regression (no constraint).
    - If $\alpha$ is very large, all feature weights tend toward zero, resulting in a very flat line approximating the mean of the data.
- **Scaling Requirement:** Ridge Regression is sensitive to the scale of the input features, so it is **important to scale the data** (e.g., using `StandardScaler`) before training.
- **Evaluation:** The regularization term is only added to the cost function **during training**. Once the model is trained, its performance should be evaluated using the **unregularized performance measure** (like RMSE or MSE).
- **Implementation:** Ridge Regression can be solved either using a **closed-form equation** or through **Gradient Descent**. When using the `SGDRegressor` class in Scikit-Learn, specifying `penalty="l2"` applies Ridge Regression regularization.

### Related Links
[[Linear Regression]] - [[Logistic Regression]] - [[Logistic Regression 1]] - [[Polynomial regression]] - [[Lasso Regression]] - [[Elastic Net]] - [[Softmax Regression]] - [[softmax regression 1]]
