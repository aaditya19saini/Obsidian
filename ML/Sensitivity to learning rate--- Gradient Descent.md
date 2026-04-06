The **learning rate** is a crucial hyperparameter in Gradient Descent that determines the size of the steps the algorithm takes toward the minimum of a cost function. Gradient Descent is highly sensitive to this exact value, and getting it wrong can derail your model's training.

Here is how the learning rate directly impacts Gradient Descent:

- **If the learning rate is too small:** The algorithm will take tiny baby steps, requiring many iterations and a very long time to eventually converge,.
- **If the learning rate is too large:** The algorithm can diverge, jumping entirely across the valley of the cost function and ending up even higher than it started, completely failing to find a good solution,.
- **If the learning rate is slightly too high:** It might make very quick progress initially, but it will end up bouncing around the optimum without ever truly settling down at the minimum.

**Relationship with Feature Scaling** Gradient Descent's sensitivity to the learning rate is heavily amplified if your input features have very different scales. Unscaled features cause the cost function to look like an elongated bowl. As a result, the algorithm might bounce down the steep sides and take a frustratingly slow path down the flat valley, making it difficult to find a learning rate that works well,.

**How to overcome learning rate sensitivity:**

- **A simple tuning trick:** Start with a large learning rate that makes the algorithm diverge, then divide it by 3 repeatedly until the divergence stops. You will usually end up very close to the optimal learning rate.

- **Learning Rate Scheduling:** Instead of forcing a single constant rate, you can systematically reduce it over time (using power, exponential, or performance scheduling),. This allows the algorithm to take large steps initially to escape local minima, and small steps later to settle exactly at the global minimum.

- **Adaptive Optimizers:** Algorithms like **RMSProp**, **AdaGrad**, and **Adam** automatically adapt the learning rate for steep versus gentle dimensions during training,. This drastically reduces the need to manually tune the learning rate hyperparameter,.


### Related Links
[[Gradient descent]] - [[Batch Gradient Descent]] - [[Stochastic Gradient Descent]] - [[Mini-batch Gradient Descent]] - [[Optimization algorithms]] - [[cost function]] - [[Learning Rate]] - [[Issues during Gradient descent]] - [[Slow Convergence]] - [[Convergence Rate]] - [[GRADIENT VECTOR]] - [[normal equation]] - [[size of the downhill step]]
