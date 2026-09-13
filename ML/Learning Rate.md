- Learning rate decides how fast or slow Gradient Descent learns.

#### to find a good learning rate we can use "[[GRID SEARCH]] "

- you may want to limit the number of iterations so that grid search can eliminate models that take too long to converge.
- simple solution is to set a very large number of iterations but to interrupt the algorithm when the gradient vector becomes tiny. 
- when its norm becomes smaller than a tiny number **ϵ (called the tolerance)**—because this happens when Gradient Descent has (almost) reached the minimum



# REPRESENTATION
-  $θnew​=θold​−η⋅gradient$

- **Too small (tiny steps 🐢)** → you’ll reach the bottom, but very slowly.

![[Pasted image 20250819210734.png]]



- **Too big (giant leaps 🦘)** → you might overshoot, bounce around, or even fly off and never settle.
    ![[Pasted image 20250819210757.png]]
- **Just right (steady steps 🚶)** → smooth path to the minimum.

### Related Links
[[Gradient descent]] - [[Batch Gradient Descent]] - [[Stochastic Gradient Descent]] - [[Mini-batch Gradient Descent]] - [[Optimization algorithms]] - [[cost function]] - [[Sensitivity to learning rate--- Gradient Descent]] - [[Issues during Gradient descent]] - [[Slow Convergence]] - [[Convergence Rate]] - [[GRADIENT VECTOR]] - [[normal equation]] - [[size of the downhill step]]
