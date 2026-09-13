The dual problem is a mathematical concept derived from a constrained optimization problem, which is referred to as the **primal problem**. It is a closely related problem to the primal problem.

The solution obtained from the dual problem typically serves as a **lower bound** for the solution of the primal problem. However, for certain problems, such as the Support Vector Machine (SVM) problem, the conditions are met such that solving the dual problem yields the **same solution** as solving the primal problem.

The context in which the sources discuss the dual problem is primarily related to Support Vector Machines (SVMs).

### The Dual Form of the Linear SVM Objective

The soft margin linear SVM classifier objective is a constrained optimization problem known as a Quadratic Programming (QP) problem. When training a linear SVM classifier, one can choose to solve either the primal or the dual problem, as both will yield the same solution.

The dual form of the linear SVM objective is represented by Equation 5-6: $$ \text{minimize } \alpha \quad \frac{1}{2} \sum_{i=1}^{m} \sum_{j=1}^{m} \alpha^{(i)} \alpha^{(j)} t^{(i)} t^{(j)} \mathbf{x}^{(i)T} \mathbf{x}^{(j)} - \sum_{i=1}^{m} \alpha^{(i)} $$ subject to $\alpha^{(i)} \ge 0$ for $i = 1, 2, \dots, m$.

Once the vector $\alpha$ that minimizes this dual objective is found (typically using a QP solver), the weights ($\mathbf{w}$) and bias ($b$) that minimize the primal problem can be computed using Equation 5-7.

### Why the Dual Problem is Important

The decision of whether to use the primal or the dual form depends on the characteristics of the dataset. The dual problem offers two critical advantages:

1. **Computational Efficiency:** The **dual problem is faster to solve than the primal when the number of training instances ($m$) is smaller than the number of features ($n$)**.
2. **Enabling the Kernel Trick:** More importantly, the **dual problem makes the kernel trick possible, while the primal does not**.

The kernel trick is crucial for allowing SVMs to perform nonlinear classification.

#### Connection to the Kernel Trick

When applying a nonlinear transformation (represented by the function $\phi$) to a dataset, the dual problem involves the dot product of the transformed vectors: $\phi(\mathbf{x}^{(i)})^T \phi(\mathbf{x}^{(j)})$.

The key insight of the kernel trick is that, for certain transformations (such as the 2nd-degree polynomial mapping), the dot product of the transformed vectors is equivalent to a simpler computation involving only the original vectors. For example, for a 2nd-degree polynomial mapping, $\phi(\mathbf{a})^T \phi(\mathbf{b}) = (\mathbf{a}^T \mathbf{b})^2$.

A **kernel** function, $K(\mathbf{a}, \mathbf{b})$, is a function capable of computing the dot product $\phi(\mathbf{a})^T \phi(\mathbf{b})$ based solely on the original vectors $\mathbf{a}$ and $\mathbf{b}$, without needing to explicitly compute (or even know about) the transformation $\phi$.

Because the dual formulation relies on these dot products, using a kernel allows one to replace the complex operation involving transformed vectors simply by the kernel function result. This means **you do not actually need to transform the training instances at all** to fit a complex nonlinear SVM model, making the process much more computationally efficient.

In the case of a kernelized SVM, making predictions for a new instance ($\mathbf{x}^{(n)}$) involves computing the dot product with only the **support vectors** (the training instances where $\alpha^{(i)} \ne 0$). This prediction relies entirely on the kernel function, $K(\mathbf{x}^{(i)}, \mathbf{x}^{(n)})$, applied within Equation 5-11.

|Kernel Type|Function $K(\mathbf{a}, \mathbf{b})$|
|:--|:--|
|Linear|$\mathbf{a}^T \mathbf{b}$|
|Polynomial|$(\gamma \mathbf{a}^T \mathbf{b} + r)^d$|
|Gaussian RBF|$\exp(-\gamma\|
|Sigmoid|$\tanh(\gamma \mathbf{a}^T \mathbf{b} + r)$|

### Related Links
[[Support Vector Machines]] - [[Polynomial Kernel]] - [[Selecting Kernel and Tuning hyperparams]] - [[Kernel PCA (kPCA)]]
