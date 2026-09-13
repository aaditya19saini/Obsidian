**Normal Equation** is a **direct, closed-form mathematical equation** used in Machine Learning, specifically for [[Linear Regression]], to **compute the value of the model parameters (θ) that minimises the cost function**

![[Pasted image 20250815233526.png]]

- linear regression (scikit learn) is based on **scipy.linalg.ltsqr()** this computes
![[Pasted image 20250816000618.png]]
[[pseduinverse of matrix]]
Ref: [[Singular Value Decomposition (SVD)]]

- Normal Equation computes the inverse of $X^T X,$ 
	- which is an (n + 1) × (n + 1) matrix (where n is the number of features).


### Related Links
[[Gradient descent]] - [[Batch Gradient Descent]] - [[Stochastic Gradient Descent]] - [[Mini-batch Gradient Descent]] - [[Optimization algorithms]] - [[cost function]] - [[Learning Rate]] - [[Sensitivity to learning rate--- Gradient Descent]] - [[Issues during Gradient descent]] - [[Slow Convergence]] - [[Convergence Rate]] - [[GRADIENT VECTOR]] - [[size of the downhill step]]
