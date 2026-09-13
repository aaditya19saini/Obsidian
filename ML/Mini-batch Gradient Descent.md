tags: [[Linear Regression]] , [[Gradient descent]]

- - A hybrid of Batch GD and Stochastic GD.

- Computes gradients using small random subsets of the training data (mini-batches).

- Each mini-batch typically contains 32–256 samples.


#### Advantages: 
1. faster than Batch GD due to fewer samples per step
2. more stable than [[Stochastic Gradient Descent]] due to avergaing over mini batch descent 
3. Uses GPU's accerlation for matrix ops 


#### Limitations
1.  May struggle to escape local minima (important for non-convex problems).
2. Still requires a good learning rate schedule to converge properly.





### Related Links
[[Gradient descent]] - [[Batch Gradient Descent]] - [[Stochastic Gradient Descent]] - [[Optimization algorithms]] - [[cost function]] - [[Learning Rate]] - [[Sensitivity to learning rate--- Gradient Descent]] - [[Issues during Gradient descent]] - [[Slow Convergence]] - [[Convergence Rate]] - [[GRADIENT VECTOR]] - [[normal equation]] - [[size of the downhill step]]
