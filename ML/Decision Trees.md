# Decision Trees
Decision Trees are versatile Machine Learning algorithms that can perform both classification and regression tasks. They work by splitting the training dataset into subsets based on feature values, recursively building a tree structure.

## Training (CART Algorithm)
The Classification and Regression Tree (CART) algorithm builds the tree top-down by choosing the best feature $k$ and threshold $t_k$ to split the data. The objective is to produce the purest child nodes possible. 
For classification, purity is measured by **Gini Impurity** or **Entropy**:
$$ G_i = 1 - \sum_{k=1}^{n} p_{i,k}^2 $$

## Advantages & Disadvantages
- **Advantages:** Highly interpretable (white-box model), requires very little data preparation (no feature scaling needed), handles both numerical and categorical data.
- **Disadvantages:** Highly prone to **overfitting** (creating overly complex trees that don't generalize well). This is generally mitigated by pruning or using ensemble methods like Random Forests.

### Related Links
[[Ensemble Learning]] - [[Random Forests]] - [[Bagging and Pasting]] - [[Out of bag Evaluation]]
