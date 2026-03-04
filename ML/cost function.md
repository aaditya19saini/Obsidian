- A **cost function** (like Mean Squared Error for regression or Cross-Entropy for classification) measures how far off a model’s predictions are from the actual outcomes. It’s essentially a **quantitative measure of “wrongness".**
- It quantifies the **distance between the model's predictions and the actual target values** in the training data

NEED:
- **To find optimal model parameters**
- to ensure quality of predictions.

Examples:
1. [[Linear Regression]] : MSE(mean sqaured error)---finds parameters that result in the ==smallest average squared difference== between **predicted and actual values.**
2. [[ML/Logistic Regression]] : **log loss** (or cross-entropy)---==penalises the model heavily== when it estimates a probability close to 0 for a positive instance, or close to 1 for a negative instance.
3. [[ML/Softmax Regression]] : **cross-entropy cost function** is used to penalise the model when it estimates a low probability for the correct target class
