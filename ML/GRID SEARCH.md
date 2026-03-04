**Grid Search** is a technique used to fine-tune a model by automating the process of hyperparameter tuning. Instead of manually fiddling with hyperparameters, you define a grid of possible values, and the system evaluates every possible combination to find the best one.

Here are the key characteristics of Grid Search based on the sources:

- **Exhaustive Search:** It evaluates all possible combinations of the hyperparameter values you specify. 
    For example, if you provide two hyperparameters with 3 and 4 possible values respectively, it will generate $3 \times 4 = 12$ combinations.
- **Cross-Validation:** To evaluate each combination, Grid Search typically uses **cross-validation** (e.g., K-fold). If you use 5-fold cross-validation on the 12 combinations mentioned above, the system will perform $12 \times 5 = 60$ rounds of training.
- **Refit:** By default (in Scikit-Learn's `GridSearchCV`), once the best combination of hyperparameters is found using cross-validation, the system automatically retrains the model on the **whole training set**. This is generally a good practice as feeding the model more data is likely to improve its performance.
- **Accessing Results:** Once complete, you can access the best parameters found (e.g., via `grid_search.best_params_`) and the best estimator directly.
- **Versatility:** It can be used to tune model hyperparameters (like `n_estimators` in a Random Forest) as well as data preparation steps (such as whether or not to add a specific feature during preprocessing).

**Limitation:** Grid Search is effective when exploring relatively few combinations. However, when the hyperparameter search space is large, **Randomized Search** (`RandomizedSearchCV`) is often preferred, as it evaluates a fixed number of random combinations rather than trying every single one.

### GAMMA VALUE 


**Gamma** is a **hyperparameter** used in **kernel-based models**  
(mainly **RBF SVM**, sometimes **Kernel Ridge**, **Gaussian Processes**).

It controls **how far the influence of a single data point reaches**.



#### Intuition (this is the key)

- **Low gamma** → far influence
    
    - Smooth decision boundary
        
    - Risk: **underfitting**
        
- **High gamma** → short influence
    
    - Very wiggly boundary
        
    - Risk: **overfitting**
        

---

## Visual metaphor

- Low gamma → soft, global curve
    
- High gamma → tight bubbles around points
    

---

## Why Grid Search cares

You **don’t know** the right gamma beforehand.

So you try many values:

```python
param_grid = {
    "gamma": [0.001, 0.01, 0.1, 1, 10, 100]
}
```

GridSearchCV tests them and picks the best.

---

## Gamma interacts with C (important)

- `C` → how much you punish mistakes
    
- `gamma` → how complex the boundary is
    

High `C` + high `gamma` = **overfitting speedrun**  
Low `C` + low `gamma` = **underfitting potato**

They must be tuned **together**.

---

## Rule of thumb

- Start small
- Use log scale
- Never guess one value
