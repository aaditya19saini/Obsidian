# Part II: Advanced ML Algorithms

Based on Chapters 5-9 of Geron's book.

## 5. Support Vector Machines (SVMs)
- **Concept:** Finding the widest possible "street" (margin) between classes.
- **Hard Margin vs Soft Margin:** Strict separation vs allowing some margin violations (controlled by hyperparameter $C$).
- **The Kernel Trick:** Implicitly mapping inputs into high-dimensional feature spaces to make non-linearly separable datasets linearly separable.
  - Common kernels: Polynomial, Gaussian RBF.

## 6. Decision Trees
- **Structure:** Root node, interior splitting nodes, leaf (terminal) nodes.
- **CART Algorithm:** Greedily splits the training set into two subsets using a single feature and threshold that minimizes Gini Impurity or Entropy.
- completely non-parametric, requires zero scaling. High variance/overfitting tendency.

## 7. Ensemble Learning and Random Forests
- **Voting Classifiers:** Hard voting (majority) vs Soft voting (highest aggregate probability).
- **Bagging & Pasting:** Training estimators on random subsets of the data (with replacement = bagging, without = pasting).
- **Random Forests:** An ensemble of Decision Trees trained via bagging. Introduces extra randomness by analyzing random subsets of features at each node.
- **Boosting:** Sequential training where the next predictor corrects the predecessor.
  - *AdaBoost:* Tweaks instance weights.
  - *Gradient Boosting:* Fits the new predictor to the *residual errors* of the previous predictor.

## 8. Dimensionality Reduction
- **Curse of Dimensionality:** Data is extremely sparse in high dimensions; distance metrics lose meaning.
- **Principal Component Analysis (PCA):** Identifies the hyperplane that lies closest to the data, and projects the data onto it to preserve maximum variance. Uses SVD under the hood.
- **Manifold Learning:** Techniques like t-SNE and LLE unroll complex 3D (or $N$-D) manifolds into lower dimensions for visualization.

## 9. Unsupervised Learning Techniques
- **K-Means:** Centroid-based clustering. Very fast, but assumes spherical clusters of similar size.
- **DBSCAN:** Density-based clustering. Can find arbitrarily shaped clusters and identify outliers automatically.
- **Gaussian Mixtures:** Probabilistic model assuming data is generated from a mixture of several Gaussian distributions.
