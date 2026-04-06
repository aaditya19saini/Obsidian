**RMSProp**

- **What it solves:** RMSProp was created to fix a major flaw in the AdaGrad algorithm, which scales down the learning rate so aggressively that it often stops entirely before finding the global optimum.
- **How it works:** Instead of accumulating _all_ past squared gradients from the beginning of training, RMSProp uses exponential decay to keep track of only the most _recent_ squared gradients.
- **Usage:** It introduces a decay rate hyperparameter (typically set to 0.9) and generally performs much better than AdaGrad, making it a highly preferred optimizer before Adam was introduced.

**Nadam**

- **What it is:** Nadam is simply the **Adam** optimization algorithm combined with the **Nesterov Accelerated Gradient** trick.
- **Advantage:** By incorporating the Nesterov trick, Nadam typically converges slightly faster than standard Adam.
- **Performance:** While it generally outperforms standard Adam across various tasks, it is still sometimes outperformed by RMSProp depending on the dataset.

**FTRL (Follow The Regularized Leader)**

- **What it is:** Also known as Dual Averaging, FTRL is an optimization technique proposed by Yurii Nesterov.
- **What it solves:** It is specifically used for creating **highly sparse models** (models where most parameter weights are exactly zero). This is highly useful when you need a model that takes up less memory and is blazingly fast at runtime.
- **Usage:** When FTRL is used alongside $\ell_1$ regularization, it pushes the optimizer to zero-out weights much more effectively than standard $\ell_1$ regularization alone. Keras implements a specific variant of this called FTRL-Proximal.

### Related Links
[[Gradient descent]] - [[Batch Gradient Descent]] - [[Stochastic Gradient Descent]] - [[Mini-batch Gradient Descent]] - [[cost function]] - [[Learning Rate]] - [[Sensitivity to learning rate--- Gradient Descent]] - [[Issues during Gradient descent]] - [[Slow Convergence]] - [[Convergence Rate]] - [[GRADIENT VECTOR]] - [[normal equation]] - [[size of the downhill step]]
