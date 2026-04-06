# Kernel PCA (kPCA)
Principal Component Analysis (PCA) performs very well on linear data but fails on highly complex, non-linear datasets (such as the Swiss Roll). **Kernel PCA** leverages the *kernel trick* to implicitly map data into a higher-dimensional space where linear PCA can be applied to separate it.

## The Kernel Trick
Projecting data into extreme high-dimensional space is computationally explosive. The kernel trick circumvents this by computing the dot product of the data in the higher-dimensional space *without ever explicitly transforming the data*. 
Common kernels used for kPCA:
- **Linear Kernel:** Equivalent to standard PCA.
- **RBF (Gaussian) Kernel:** Excellent at preserving local distances, often handling highly non-linear clusters well.
- **Polynomial Kernel:** Good for data polynomial relationships.

This technique allows for non-linear dimensionality reduction, helping models like SVMs perform faster.

### Related Links
[[PCA]] - [[Singular Value Decomposition (SVD)]] - [[Manifold learning]]
