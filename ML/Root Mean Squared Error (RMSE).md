- RMSE is the **square root of the average of squared errors** between predicted and actual values.
![[Pasted image 20251011152625.png]]



- **Interpretability**: RMSE is in the same unit as the target variable, making it intuitive to understand.
- **Sensitivity to Large Errors**: Squaring the errors before averaging gives **more weight to larger deviations**, which is useful when big mistakes are costly or critical.

- **Smooth Visualization**: RMSE tends to produce smoother curves than raw error metrics, helping you spot trends like underfitting or overfitting more clearly

### Conditions for Using RMSE

- **Regression Tasks:** RMSE is a typical performance measure for problems involving the prediction of a target numeric value, known as **regression tasks**. Examples of such tasks include predicting the median housing price in a district.

- **General Preference:** The RMSE is generally the **preferred performance measure for regression tasks**.

- **Sensitivity to Outliers:** RMSE is more sensitive to outliers than the Mean Absolute Error (MAE).
- **Bell-Shaped Curve:** When outliers are **exponentially rare** (such as in a bell-shaped curve or Gaussian distribution), the RMSE performs very well and is generally preferred.

### Alternatives to RMSE

While RMSE is preferred for regression tasks, other functions may be preferred in certain contexts.

The sources explicitly mention the following alternatives:

1. **Mean Absolute Error (MAE):** Also known as the Average Absolute Deviation, the MAE is calculated using the sum of the absolute differences between predictions and target values.
    
    - **Formula:** $MAE(X, h) = \frac{1}{m} \sum_{i=1}^{m} |h(\mathbf{x}^{(i)}) - y^{(i)}|$.
    - **Use Case:** You might consider using the MAE if there are **many outlier districts** in the dataset.
    - **Norm Equivalent:** Computing the sum of absolutes corresponds to the $\ell_1$ norm, sometimes called the Manhattan norm. The $\ell_1$ norm is less sensitive to outliers than the $\ell_2$ norm (RMSE).
2. **Mean Squared Error (MSE):** Minimizing the Mean Squared Error (MSE) is simpler than minimizing the RMSE, and it leads to the same result (because the value that minimizes a function also minimizes its square root).
    
    - **Formula:** $MSE(\mathbf{X}, h_{\boldsymbol{\theta}}) = \frac{1}{m} \sum_{i=1}^{m} (\boldsymbol{\theta}^{\text{T}} \mathbf{x}^{(i)} - y^{(i)})^2$.
    - **Minimization Objective:** For training a Linear Regression model, the objective is to find the value of $\boldsymbol{\theta}$ that minimizes the MSE.

More generally, both RMSE and MAE are ways to measure the distance between the vector of predictions and the vector of target values, using different distance measures or norms.

- **Euclidean Norm ($\ell_2$ norm):** Computing the root of a sum of squares (RMSE) corresponds to the Euclidean norm, noted $| \cdot |_2$.
- **Manhattan Norm ($\ell_1$ norm):** Computing the sum of absolutes (MAE) corresponds to the $\ell_1$ norm, noted $| \cdot |_1$.
- **General $\ell_k$ norm:** The $\ell_k$ norm of a vector $\mathbf{v}$ with $n$ elements is generally defined as $| \mathbf{v} |_k = \left( \sum_{j=0}^{n} |v_j|^k \right)^{\frac{1}{k}}$. The higher the norm index $k$, the more the measure focuses on large values and neglects small ones.
links: [[Linear Regression]]