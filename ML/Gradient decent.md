tags: [[Linear Regression]]

- very generic optimization algorithm
- ==General Idea==: tweak parameters iteratively in order to minimize the [[cost function]]

***Gradient Descent*** = taking steps downhill (steepest slope) on the error curve until you reach the lowest point (minimum error)



GUIDE TO UNDERSTANDING:
**1. Starting Point**

- Begin with random values for parameters (θ) → _random initialization_.

- Update θ step by step to reduce the cost function (like MSE).

- Keep going until you’re near the minimum → _convergence_.

**2. [[Learning Rate]] (step size)**

- Too **small** → progress is very slow (takes forever to reach bottom).
    
- Too **big** → you overshoot, jump around, maybe never settle (diverges).
    
- Just right → smooth, steady convergence.
    

**3. Real-life Cost Functions Aren’t Always Simple**

- Some terrains = messy (holes, ridges, flat areas).
    
- **Local minimum** → you might get stuck in a small dip instead of the deepest valley.
    
- **Plateaus** → very flat, so updates are tiny, making training slow.
    

**4. The Good News (for [[Linear Regression]] + MSE)**

- The cost function is **convex** → shaped like a single bowl.
    ![[Pasted image 20250819211014.png]]
- Convex = no local traps → only one **global minimum**.
    
- So Gradient Descent _will_ find the best solution (if learning rate isn’t too high).
    

**5. [[Feature Scaling]]**

- If features (inputs) are on different scales → the bowl looks stretched/elongated.
    
- Gradient Descent then zig-zags a lot and takes longer.
    
- **Fix**: scale features (e.g., StandardScaler in Scikit-Learn).
    

**6. Big Picture**

- Training a model = searching parameter space for the point that gives the lowest cost.
    
- More parameters = higher-dimensional space (like searching in 300D instead of 3D).
    
- But for Linear Regression, since the function is convex, the "needle" is always at the bottom of the bowl.





TYPES OF GRADIENT DESCENT:
1. [[Batch Gradient Descent]]
2. [[Stochastic Gradient Descent]]
3. [[Mini-batch Gradient Descent]]

![[Pasted image 20250826152021.png]]
