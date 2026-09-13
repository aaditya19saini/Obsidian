- Uses the entire training set; **Terribly slow** on very large training sets.

## GRADIENT COMPUTATION: 

- WRT model param $θj$ . (need to calculate how much the cost function will change if you change θj just a little bit/ **PARTIAL DEREVATIVE**)

![[Pasted image 20250820000629.png]]
- this calculates the partial derivatives individually.

### 1. computation in one go...
- instead of partial derivatives being calculated individually they can be calculated in one go. 
- the [[GRADIENT VECTOR]]: 
               $∇θ MSE(θ)$ contains all the partial derivatives of the cost function. 
![[Pasted image 20250820134737.png]]

### 2. gradient decent 

- Once you have the [[GRADIENT VECTOR]], which points uphill, just go in the opposite direction to go downhill. 
- This means subtracting ==∇θ MSE(θ) from θ.
- multiply the gradient vector by **η** to determine the [[size of the downhill step]]
- ![[Pasted image 20250820141121.png]]



## [[Learning Rate]] and GD

![[Pasted image 20250820141220.png]]
1. Left: **learning rate is too low**: the algorithm will eventually reach the solution, but it will take a long time.
2. Middle: the **learning rate looks pretty good**: in just a few iterations, it has already converged to the solution
3. Right: the **algorithm diverges**, jumping all over the place and actually getting further and further away from the solution at every step.


to find a good learning rate you can use grid search.



### Related Links
[[Gradient descent]] - [[Stochastic Gradient Descent]] - [[Mini-batch Gradient Descent]] - [[Optimization algorithms]] - [[cost function]] - [[Learning Rate]] - [[Sensitivity to learning rate--- Gradient Descent]] - [[Issues during Gradient descent]] - [[Slow Convergence]] - [[Convergence Rate]] - [[GRADIENT VECTOR]] - [[normal equation]] - [[size of the downhill step]]
