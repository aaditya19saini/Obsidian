### The Need for Nonlinear Classification

- Although Linear [[Support Vector Machines]] classifiers are highly effective in many scenarios, many datasets in the real world are not close to being **linearly separable**. 
- To tackle these nonlinear datasets, one approach is to manually add more features, such as polynomial features, which can potentially make the resulting dataset linearly separable in a higher-dimensional space.
- For example, a dataset with only one feature ($x_1$) that is not linearly separable can become perfectly linearly separable if a second feature, $x_2 = (x_1)^2$, is added, resulting in a 2D dataset. 
- This concept of enhancing the feature set is foundational to both methods below.

### 1. Polynomial Kernel

- Adding explicit polynomial features works well but has limitations: for complex datasets, it may require a high polynomial degree, which in turn generates a **huge number of features**, making the model **too slow** to train.

- Fortunately, when utilizing SVMs, an "almost miraculous mathematical technique" known as the **kernel trick** can be applied.

- The kernel trick makes it possible to obtain the exact same result as if you had explicitly added many polynomial features, even those of a **very high degree**, **without actually having to add them**. 
- This elegantly avoids the "combinatorial explosion of the number of features".

The Polynomial Kernel function $K(a, b)$ implicitly computes the dot product of the transformed vectors, $\phi(a)^T \phi(b)$, based only on the original vectors $a$ and $b$. The equation for the Polynomial Kernel is:

$$K(a, b) = (\gamma a^T b + r)^d$$

- The function $K(a, b) = (a^T b)^2$ is called a **2nd-degree polynomial kernel**. 
- By substituting this kernel into the dual problem's optimization equation, you get the same result as if you had explicitly calculated all the 2nd-degree polynomial features and then fitted a linear SVM, but the kernel trick is significantly more ==computationally efficient.==

When using a Polynomial Kernel in SVMs, the relevant hyperparameters include:

- **Degree ($d$):** This controls the complexity of the polynomial transformation. If a model is **overfitting**, you might **reduce the polynomial degree**. If it is **underfitting**, you might try **increasing it**.
- **$coef0$ ($r$):** This hyperparameter controls how much the model is **influenced by high-degree polynomials versus low-degree polynomials**.

The implementation of the kernel trick is typically handled by the `SVC` class in Scikit-Learn.

### 2. Adding Similarity Features

Another technique to handle nonlinear problems involves introducing **similarity features**. This method measures how much each instance resembles a specific _landmark_.

1. **Defining the Landmark:** You start by defining one or more landmarks. The simplest approach is to create a landmark at the location of **each and every instance in the dataset**.
2. **The Similarity Function ([[Gaussian Radial Basis Function (RBF).]]):** The similarity features are typically computed using a **similarity function**, such as the [[Gaussian Radial Basis Function (RBF).]]
    - The RBF is a **bell-shaped function** that ranges from 0 (when far away from the landmark) to 1 (when exactly at the landmark).
    - The formula is given by: $$\phi_\gamma(x, \ell) = \exp(-\gamma\parallel x - \ell \parallel^2)$$
    - Here, $x$ is the instance, $\ell$ is the landmark, and $\gamma$ is a hyperparameter.
3. **Transformation:** If you select the location of every instance as a landmark, a training set with $m$ instances and $n$ features gets transformed into a new training set with $m$ instances and $m$ features (assuming the original features are dropped). This greatly **increases the dimensionality**, which in turn **increases the chances that the transformed training set will be linearly separable**.

#### The Gaussian RBF Kernel Trick

- While manually adding similarity features can work with any Machine Learning algorithm, it can be computationally expensive on large training sets due to the resulting large number of features ($m$ features for $m$ instances).

- Fortunately, just as with polynomial features, the kernel trick performs its SVM magic here as well, allowing for a result similar to having explicitly added all those similarity features, but without actually adding them. This is implemented using the **Gaussian RBF Kernel**.

- The Gaussian RBF Kernel is defined as:

$$K(a, b) = \exp(-\gamma\parallel a - b \parallel^2)$$

- In the case of the Gaussian RBF kernel, the corresponding underlying transformation function $\phi$ actually maps each training instance to an **infinite-dimensional space**, making it beneficial that the mapping does not need to be explicitly calculated.

The $\gamma$ hyperparameter in the RBF kernel acts as a **regularization hyperparameter**.

- **Increasing $\gamma$:** Makes the bell-shaped curve narrower, reducing each instance’s range of influence. This leads to a decision boundary that is **more irregular** (which may cause overfitting).
- **Decreasing $\gamma$:** Makes the bell-shaped curve wider, giving instances a larger range of influence. This results in a **smoother decision boundary** (which may cause underfitting).

### Related Links
[[Support Vector Machines]] - [[Dual problem]] - [[Selecting Kernel and Tuning hyperparams]] - [[Kernel PCA (kPCA)]]
