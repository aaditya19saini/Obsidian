### Overview and Core Concepts

A Support Vector Machine (SVM) is defined as a **"very powerful and versatile Machine Learning model"** capable of performing linear or nonlinear classification, regression, and even outlier detection. They are considered one of the most popular models in Machine Learning and are particularly well suited for the classification of complex but small- or medium-sized datasets. SVMs are categorized as **supervised learning algorithms**.

The **fundamental idea behind SVMs is large margin classification**. This concept involves fitting the **widest possible street (or margin)** between the different classes in the training data.

#### Support Vectors

The decision boundary of an SVM classifier is fully determined (or **"supported"**) by the instances located exactly on the edge of this widest street. These influential instances are specifically called the **support vectors**. Remarkably, adding or moving training instances that are "off the street" will not affect the final decision boundary at all.

#### Sensitivity to Feature Scales

It is crucial to note that **SVMs are sensitive to the feature scales**. Scaling the features (for example, using a `StandardScaler`) helps produce a much better decision boundary.

### Hard Margin vs. Soft Margin Classification

The margin determines the flexibility of the model and how strictly it separates the data:

1. **Hard Margin Classification:** This is the strict approach where all training instances must be located strictly off the street and on the correct side.
    
    - **Limitations:** Hard margin classification only works if the data is **linearly separable**. Furthermore, it is highly **sensitive to outliers**; a single outlier can drastically change the decision boundary or make it impossible to find a hard margin altogether.
2. **Soft Margin Classification:** To handle data that is not perfectly separable or contains outliers, soft margin classification is preferred, as it is a more flexible model. The objective here is to find a good balance between maintaining the largest possible margin and **limiting margin violations** (instances that end up either in the middle of the street or on the wrong side).
    
    - **C Hyperparameter:** This crucial balance is controlled by the hyperparameter $C$.
        - A **smaller $C$ value** leads to a wider street but tolerates more margin violations, effectively **regularizing the model**. If the SVM model is overfitting the training data, you can attempt to correct this by **reducing $C$**.
        - A **high $C$ value** prioritizes making fewer margin violations but results in a smaller margin.

### Nonlinear SVM Classification using the Kernel Trick

In cases where datasets are not linearly separable, SVMs can still perform nonlinear classification.

1. **Adding Features:** One approach is to manually introduce more features, such as polynomial features, which can transform the data into a higher-dimensional space where it may become linearly separable. However, this can be computationally slow if high-degree polynomials are used, leading to a huge number of features.
    
2. **The Kernel Trick:** Fortunately, SVMs can utilize an advanced mathematical technique called the **kernel trick**.
    
    - The kernel trick allows the SVM to achieve the same result as if you had added many polynomial or similarity features, without the need to explicitly calculate or store those potentially huge numbers of features. This avoids a combinatorial explosion in the number of features.
    - This technique is primarily implemented via the `SVC` class in Scikit-Learn.

#### Common Kernels

The kernel trick uses kernel functions $K(a, b)$ to implicitly compute the dot product of the transformed vectors $\phi(a)^T \phi(b)$ based only on the original vectors $a$ and $b$. Common kernels include:

- **Polynomial Kernel:** $K(a, b) = (\gamma a^T b + r)^d$. The hyperparameter `coef0` controls how much the model is influenced by high-degree polynomials versus low-degree polynomials.
- **Gaussian RBF Kernel** (Radial Basis Function): $K(a, b) = \exp(-\gamma \parallel a - b \parallel^2)$.
    - **Gamma ($\gamma$) Hyperparameter:** $\gamma$ acts as a **regularization hyperparameter** for the RBF kernel. Increasing $\gamma$ makes the decision boundary more irregular (potentially overfitting). Decreasing $\gamma$ results in a smoother decision boundary (potentially underfitting).

**Kernel Selection Guideline:** As a rule of thumb, you should first try the linear kernel (using `LinearSVC`). If the training set is not too large, the Gaussian RBF kernel is a good second choice, as it works well in most cases.

### SVM Regression

The SVM algorithm is also capable of performing **linear and nonlinear regression (SVM Regression)**.

For regression, the objective is reversed: instead of maximizing the margin while limiting violations, SVM Regression aims to **fit as many instances as possible on the street while limiting margin violations**. The width of this street is controlled by the hyperparameter $\epsilon$. Because adding more training instances within the margin does not change the model’s predictions, the model is described as **$\epsilon$-insensitive**.

- The `LinearSVR` class can be used for linear SVM Regression.
- The `SVR` class supports kernelized SVM Regression.

### Implementation and Performance Notes

- **Decision Scores vs. Probabilities:** Unlike Logistic Regression classifiers, standard SVM classifiers **do not output probabilities** for each class. They output a decision score based on the function $w^T x + b$.
- **Loss Function:** Online linear SVM classifiers often use Gradient Descent (such as implemented in `SGDClassifier`) to minimize the **hinge loss function**, defined as $\max(0, 1 – t)$.
- **Computational Scalability:**
    - The `LinearSVC` class is highly efficient for linear SVMs, scaling almost linearly with the number of instances ($m$) and features ($n$): roughly $O(m \times n)$.
    - The `SVC` class, which supports the kernel trick, scales poorly with the number of training instances, with a training time complexity typically between $O(m^2 \times n)$ and $O(m^3 \times n)$. This makes `SVC` dreadfully slow for large datasets (hundreds of thousands of instances).

### Related Links
[[Dual problem]] - [[Polynomial Kernel]] - [[Selecting Kernel and Tuning hyperparams]] - [[Kernel PCA (kPCA)]]
