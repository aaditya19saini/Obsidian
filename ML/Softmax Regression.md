**Softmax Regression**, also known as **Multinomial Logistic Regression**, is a **generalisation of the Logistic Regression model** that directly supports **multiple classes** without needing to train and combine multiple binary classifiers.
- It is designed for **multiclass classification tasks** where each instance belongs to only **one** out of three or more possible classes. 
- For instance, classifying iris flowers into their three distinct species is a suitable task for Softmax Regression.

Here's how Softmax Regression works:

- **Computing Scores**: For a given instance _x_, the model first calculates a **score** _sk(x)_ for each class _k_. This score is computed as a **weighted sum of the input features** plus a **bias term**, similar to a Linear Regression prediction. Each class _k_ has its own dedicated parameter vector, θ(k), and all these vectors are typically stored together in a parameter matrix Θ.
    
    - The equation for computing the score for class _k_ is: _sk(x) = xTθ(k)_.
- **Estimating Probabilities (Softmax Function)**: After computing scores for all classes, the **softmax function** (also called the normalized exponential function) is applied to these scores to estimate the **probability** _pk_ that the instance belongs to class _k_. This function ensures that all estimated probabilities are between 0 and 1 and that they sum up to 1 across all classes.
    
    - The **Softmax function** is defined as: _pk = σ(s(x))k = exp(sk(x)) / ∑j=1K exp(sj(x))_, where _K_ is the number of classes, _s(x)_ is the vector containing the scores of each class for instance _x_, and _σ(s(x))k_ is the estimated probability that instance _x_ belongs to class _k_.
- **Making Predictions**: The Softmax Regression classifier predicts the class that has the **highest estimated probability**. This is equivalent to choosing the class with the highest score.
    
- **Training and Cost Function**:
    
    - The primary objective during training is to **set the model parameters** (the Θ matrix) such that the model assigns a **high probability to the actual target class** and consequently low probabilities to all other classes.
    - This is achieved by **minimising the cross-entropy cost function**. This cost function penalises the model heavily when it estimates a low probability for the correct target class.
    - The cross-entropy cost function for the whole training set is: _J(Θ) = - (1/m) ∑i=1m ∑k=1K y(i)k log(p(i)k)_, where _y(i)k_ is 1 if the _i_th instance belongs to class _k_, and 0 otherwise.
    - While there is **no known closed-form equation** (like the Normal Equation) to directly compute the parameters that minimise this cost function, the cross-entropy cost function is **convex**. This crucial property guarantees that **Gradient Descent** (or other optimisation algorithms) will find the **global minimum** if given enough time and a suitable learning rate. Gradient Descent uses the partial derivatives of the cost function with respect to each model parameter to iteratively adjust the parameters.
- **Scikit-Learn Implementation**:
    
    - Scikit-Learn's `LogisticRegression` class can be used for Softmax Regression. By default, when training on more than two classes, it employs a **one-versus-all (OvA)** strategy, training multiple binary classifiers.
    - However, you can explicitly enable Softmax Regression by setting the `multi_class` hyperparameter to `"multinomial"`. You also need to specify a solver that supports multinomial logistic regression, such as `"lbfgs"`.
    - The `LogisticRegression` class also applies **ℓ2 regularization** by default, with its strength controlled by the hyperparameter `C` (where a higher `C` value means less regularization).