
**Singular Value Decomposition (SVD)** is a powerful and widely used **matrix factorization technique** in machine learning. It decomposes a matrix, such as the training set matrix **X**, into the product of three other matrices: **U**, **Σ (Sigma)**, and **Vᵀ (V transpose)**.

Here's how SVD works and its applications, particularly in the context of Linear Regression and Principal Component Analysis (PCA):

### What SVD Is

- **Decomposition:** SVD decomposes a matrix **X** into **X = U Σ Vᵀ**.
    - **U** is a unitary matrix.
    - **Σ** is a diagonal matrix containing the **singular values**. These singular values represent the "strength" or "importance" of each component (implied by the process of forming Σ⁺ for the pseudoinverse).
    - **Vᵀ** is a unitary matrix whose columns (or rows in V) contain the **principal components**.

### SVD in Linear Regression (Normal Equation Context)

In the context of Linear Regression, SVD is utilised to find the optimal parameter vector **θ** that **minimises the cost function.**

- **Pseudoinverse Calculation:** The `LinearRegression` class in Scikit-Learn, and the `scipy.linalg.lstsq()` function, compute the parameter vector **θ** using the formula **θ = X⁺y**, where **X⁺** is the **pseudoinverse** of the training set matrix **X**.
- **How X⁺ is derived:** The pseudoinverse **X⁺** is computed using SVD as **X⁺ = VΣ⁺Uᵀ**.
    - To compute **Σ⁺**, the algorithm takes the matrix **Σ** (from the SVD of X), sets all values smaller than a tiny threshold to zero, replaces all non-zero values with their inverse, and then transposes the resulting matrix.
- **Advantages over direct Normal Equation:** This SVD-based approach is more efficient than directly calculating the Normal Equation and, crucially, **it handles edge cases gracefully**. The Normal Equation may not work if the matrix **XᵀX** is not invertible (e.g., if there are fewer training instances than features, or if some features are redundant), but the **pseudoinverse is always defined**.
- [[Computational Complexity]]  The SVD approach for Linear Regression has a computational complexity of about **O(n²)**, where 'n' is the number of features. While this is still slow for a very large number of features (e.g., 100,000), it's generally faster than the direct Normal Equation's complexity, which can range from O(n²⁴) to O(n³). Both methods are linear with respect to the number of training instances (O(m)).

### SVD in Principal Component Analysis (PCA)

PCA is a dimensionality reduction technique that identifies a hyperplane that lies closest to the data and then projects the data onto it. SVD is the fundamental mathematical tool used to achieve this.

- **Identifying Principal Components:** PCA identifies axes that account for the largest amount of variance in the training set. SVD is the standard matrix factorization technique that directly provides these principal components.
- **V Matrix Contains PCs:** In the SVD decomposition **X = U Σ Vᵀ**, the matrix **V** contains all the principal components that are being sought. For example, the first principal component is often represented by the first column of V (or first row of Vᵀ).
- **Scikit-Learn Implementation:** Scikit-Learn's `PCA` class implements PCA using SVD decomposition.

In essence, SVD is a foundational mathematical tool that provides robust and efficient methods for tasks like finding optimal parameters in Linear Regression and performing dimensionality reduction with PCA.