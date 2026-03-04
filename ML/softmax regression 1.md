### Overview and Purpose

Links: [[Logistic Regression 1]],[[Linear Regression]]

Softmax Regression, also known as **Multinomial Logistic Regression**, is a generalization of the Logistic Regression model.

While [[Logistic Regression 1]] is strictly a **binary classifier** , Softmax Regression is used to directly support **multiple classes** (three or more).
- It is important to note that the Softmax Regression classifier predicts only one class at a time (it is a **multiclass**, not a multioutput, classifier).
- Therefore, it should only be used with classes that are **mutually exclusive** (e.g., classifying different types of iris plants).

### Model Mechanism and Probability Estimation

The core idea of Softmax Regression involves calculating a score for each class and then converting these scores into estimated probabilities.

1. **Computing the Score (Logit):** When given an instance $x$, the model first computes a **score** ($s_k(x)$) for each class $k$. This score calculation is linear and looks just like the prediction equation for Linear Regression, where $\theta^{(k)}$ is the parameter vector dedicated to class $k$: $$s_k(x) = x^T \theta^{(k)}$$ All these class-specific parameter vectors ($\theta^{(k)}$) are typically stored as rows in a parameter matrix $\Theta$.
    
2. **Applying the Softmax Function:** To estimate the probability ($p_k$) that the instance belongs to class $k$, the scores are run through the **softmax function** (also called the normalized exponential). This function ensures that all estimated probabilities are between 0 and 1, and that they sum up to 1. The softmax function is defined as: $$p_k = \sigma(\mathbf{s}(\mathbf{x}))_k = \frac{\exp(s_k(\mathbf{x}))}{\sum_{j=1}^K \exp(s_j(\mathbf{x}))}$$ where $K$ is the number of classes, and $\mathbf{s}(\mathbf{x})$ is the vector containing the scores for all classes. These scores are often referred to as **logits** or **log-odds** (though they are actually unnormalized log-odds).
    
3. **Final Prediction:** The Softmax Regression classifier predicts the class with the **highest estimated probability**, which is equivalent to selecting the class with the **highest score**. $$\hat{y} = \underset{k}{\operatorname{argmax}} , \sigma(\mathbf{s}(\mathbf{x}))_k = \underset{k}{\operatorname{argmax}} , s_k(\mathbf{x})$$
    

### Training and Cost Function (Cross Entropy)

The goal of training is to find the optimal parameter matrix $\Theta$ that makes the model estimate a **high probability for the target class** and low probabilities for the others.

The function used to measure this objective is the **cross entropy** cost function (Equation 4-22): $$J(\Theta) = - \frac{1}{m} \sum_{i=1}^m \sum_{k=1}^K y_k^{(i)} \log(p_k^{(i)})$$ This cost function severely penalizes the model when it estimates a low probability for the actual target class.

- **Relationship to Log Loss:** When there are only two classes ($K=2$), the cross entropy cost function is mathematically equivalent to the Logistic Regression's cost function, known as the **log loss**.
- **Optimization:** Similar to Logistic Regression, there is no known closed-form solution to minimize this cost function. However, since the cost function is convex, iterative optimization algorithms like **Gradient Descent** are guaranteed to find the global minimum (provided the learning rate is not too large and training runs long enough). The gradient vector needed for optimization is defined by Equation 4-23.

### Implementation in Scikit-Learn

While Scikit-Learn's `LogisticRegression` class is primarily a binary classifier, it can be configured to use Softmax Regression when trained on more than two classes.

To enable Softmax Regression in Scikit-Learn, you must set the `multi_class` hyperparameter to **"multinomial"**. You must also choose a solver that supports Softmax Regression, such as the **"lbfgs"** solver. By default, the `LogisticRegression` class also applies $\ell_2$ regularization, which is controlled by the hyperparameter **C**.