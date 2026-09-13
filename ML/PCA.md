**Principal Component Analysis (PCA)** is widely considered the most popular algorithm for **dimensionality reduction**. It functions by identifying the hyperplane that lies closest to the data and then **projecting** the data onto it.

### Core Principles

- **Preserving Variance:** To minimize information loss, PCA selects the axis that preserves the **maximum amount of variance**. This choice is mathematically equivalent to minimizing the mean squared distance between the original dataset and its projection.
- **Principal Components (PCs):** The algorithm identifies orthogonal axes that account for the remaining variance. The unit vector defining the $i^{th}$ axis is called the $i^{th}$ **principal component**.
- **Singular Value Decomposition (SVD):** PCA uses a standard matrix factorisation technique called SVD to decompose the training set matrix $X$ into the matrix multiplication of three matrices ($U \Sigma V^T$). The matrix $V$ contains the principal components. It is crucial to **center** the data around the origin before applying PCA, a step Scikit-Learn handles automatically.

### Implementation and Usage

- **Explained Variance Ratio:** When using Scikit-Learn, the `explained_variance_ratio_` variable indicates the proportion of the dataset's variance that lies along the axis of each principal component.
- **Choosing Dimensions:** Rather than selecting an arbitrary number of dimensions, it is generally preferable to choose the number of dimensions that add up to a sufficiently large portion of the variance, such as **95%**.
- **Compression:** PCA can significantly reduce the size of a dataset (e.g., compressing MNIST to less than 20% of its original size). It is possible to decompress the data back to the original number of dimensions using the inverse transformation; the mean squared distance between the original and reconstructed data is known as the **reconstruction error**.

### PCA Variants

- [[Randomized PCA ]]A stochastic algorithm that quickly finds an approximation of the first $d$ principal components. It is dramatically faster than full SVD when the number of required dimensions ($d$) is much smaller than the number of features ($n$).
- [[Incremental PCA (IPCA)]] This variant allows you to split the training set into **mini-batches** and feed the algorithm one batch at a time. This is useful for large datasets that do not fit in memory and for online learning.
- [[Kernel PCA (kPCA)]] By using the **kernel trick** (similar to Support Vector Machines), kPCA performs complex **nonlinear projections**. This is particularly useful for preserving clusters of instances after projection or unrolling datasets that lie close to a twisted manifold.

---

**Concise Answer:** **PCA** (Principal Component Analysis) is a dimensionality reduction technique that uses **projection** to reduce the feature space while preserving the maximum amount of **variance**. It relies on **Singular Value Decomposition (SVD)** to identify the **Principal Components** (orthogonal axes) of the data. It is useful for **data compression**, visualisation, and speeding up training. Variants include **Randomized PCA** for speed, **Incremental PCA** for large datasets (mini-batches), and **Kernel PCA** for nonlinear projections.

[[Selecting Kernel and Tuning hyperparams ]]

### Related Links
[[Kernel PCA (kPCA)]] - [[Singular Value Decomposition (SVD)]] - [[Manifold learning]]
