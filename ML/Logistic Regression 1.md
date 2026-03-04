### Definition and Purpose

Links: [[Linear Regression]]

**Logistic Regression** (also known as **Logit Regression**) is a common machine learning algorithm used primarily for **classification tasks**.
- It is listed among the most important supervised learning algorithms.

The main goal of Logistic Regression is to **estimate the probability that an instance belongs to a particular class**. For example, it might estimate the probability that an email is spam.

It functions as a **binary classifier**:

- If the estimated probability ($p$) is greater than 50%, the model predicts the instance belongs to the positive class (labeled "1").
- Otherwise, it predicts the instance belongs to the negative class (labeled "0").

### Model Structure and Probability Estimation

Like a Linear Regression model, a Logistic Regression model calculates a **weighted sum of the input features** plus a bias term. However, instead of outputting this sum directly, it applies the **logistic function** to the result.

1. **The Logistic Function ($\sigma(\cdot)$):** The logistic function is a **sigmoid function**—meaning it is S-shaped—that constrains the output to a value between 0 and 1. This output is the estimated probability.
    - The logistic function is defined by Equation 4-14: $$\sigma(t) = \frac{1}{1 + \exp(-t)}$$
2. **The Logit (Score):** The weighted sum of the input features ($t = x^T \theta$) is often called the **logit**. This name derives from the fact that the logit function is the inverse of the logistic function. The logit is also referred to as the **log-odds**.
3. **Model Prediction:** The Logistic Regression model's estimated probability ($p$) is calculated using the vectorized form shown in Equation 4-13: $$p = h_{\theta}(x) = \sigma(x^T \theta)$$

The model makes its final prediction ($\hat{y}$) easily based on this probability (Equation 4-15):

- **$\hat{y} = 1$ if $p \geq 0.5$**.
- **$\hat{y} = 0$ if $p < 0.5$**.

Crucially, since $\sigma(t) \geq 0.5$ when $t \geq 0$, and $\sigma(t) < 0.5$ when $t < 0$, the model essentially predicts class 1 if $x^T \theta$ is positive, and class 0 if it is negative.

### Decision Boundaries and Training

The classification decision relies on the value of $x^T \theta$. Because this is a linear combination of inputs, the resulting separation between classes is a **linear boundary**.

#### Training and Cost Function (Log Loss)

The training objective is to determine the optimal parameter vector $\theta$ such that the model predicts high probabilities for positive instances ($y=1$) and low probabilities for negative instances ($y=0$).

The cost function capturing this objective over the entire training set is called the **log loss** (Equation 4-17). The cost function severely penalizes the model when it incorrectly estimates a probability close to 0 for a positive instance, or a probability close to 1 for a negative instance.

The cost function for a single training instance $x$ is defined as: $$c(\theta) = \begin{cases} -\log p & \text{if } y = 1 \ -\log (1 - p) & \text{if } y = 0 \end{cases}$$

#### Optimization

A significant distinction from some linear models (like Linear Regression solved via the Normal Equation) is that **there is no known closed-form equation** to directly compute the value of $\theta$ that minimizes the log loss.

However, the good news is that the Logistic Regression cost function is **convex**. This convexity guarantees that iterative optimization algorithms, such as **Gradient Descent**, are certain to find the **global minimum** (provided the learning rate is appropriate and training runs long enough). Training involves minimizing the cost function by calculating its partial derivatives (Equation 4-18).

#### Regularization

Logistic Regression models can be regularized using $\ell_1$ or $\ell_2$ penalties, just like other linear models. Scikit-Learn applies an $\ell_2$ penalty by default.

The regularization strength in the Scikit-Learn `LogisticRegression` class is controlled by the hyperparameter **C**. This parameter is the _inverse_ of the regularization factor ($\alpha$) used in other linear models. Consequently, **a higher value of C means the model is less regularized**.

### Related Concepts

**Softmax Regression:** Logistic Regression can be extended directly to handle tasks involving **multiple exclusive classes** (three or more) without resorting to training and combining multiple binary classifiers (like OvA or OvO strategies). This generalization is known as **Softmax Regression** (or Multinomial Logistic Regression). Softmax Regression computes scores for each class and then estimates the probability of each class using the softmax function.