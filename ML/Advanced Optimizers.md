# Advanced Optimizers
## Geron Deep Dive: Code & Advanced Math
Plain Stochastic Gradient Descent updates weights completely linearly $\mathbf{\theta} \leftarrow \mathbf{\theta} - \eta \nabla_{\mathbf{\theta}} J(\mathbf{\theta})$.
Deep neural networks easily get stuck in local plateaus using plain SGD. Modern optimizers track historical momentum.

### 1. Momentum Optimization
Imagine a bowling ball rolling down a hill. It gains speed over time. Momentum $m$ retains a fraction $\beta$ (usually 0.9) of the previous gradient.
$$ m \leftarrow \beta m - \eta \nabla_{\mathbf{\theta}} J(\mathbf{\theta}) $$
$$ \mathbf{\theta} \leftarrow \mathbf{\theta} + m $$
```python
optimizer = keras.optimizers.SGD(learning_rate=0.001, momentum=0.9)
```

### 2. Adam (Adaptive Moment Estimation)
Combines the features of Momentum and RMSProp. It keeps track of an exponentially decaying average of past gradients (like Momentum) **and** past squared gradients (like RMSProp).
$$ m \leftarrow \beta_1 m - (1 - \beta_1) \nabla_{\mathbf{\theta}} J(\mathbf{\theta}) $$
$$ s \leftarrow \beta_2 s + (1 - \beta_2) \nabla_{\mathbf{\theta}} J(\mathbf{\theta}) \otimes \nabla_{\mathbf{\theta}} J(\mathbf{\theta}) $$
$$ \mathbf{\theta} \leftarrow \mathbf{\theta} + \eta m / \sqrt{s + \epsilon} $$
```python
# The industry standard default optimizer
optimizer = keras.optimizers.Adam(learning_rate=0.001, beta_1=0.9, beta_2=0.999)
```
