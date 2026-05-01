
### Hyperbolic tangent function
- S shaped, continuous  and differentiable? \
- output value ranges from **-1 to 1** (0/1 in log regression
- which tends to make each layer’s output more or less centered around 0 at the beginning of training. This often helps speed up convergence.

  $tanh(z) = 2σ(2z) – 1$
### Rectified Linear Unit function (RELU)
- continuous + not differentiable at z=0
- derivative is 0 for z < 0
- fast to compute 
- doesnt have a maximum output value 
- Helps to resolve [[Issues during Gradient descent]]

                  
                  $ReLU(z) = max(0, z)$


### Need for activation functions 
The primary need for an activation function is to introduce **non-linearity** into a neural network.
for example:
- If you do not use an activation function (or use a purely linear one), chaining multiple linear transformations together simply results in another linear transformation. 
- For example, if $f(x) = 2x + 3$ and $g(x) = 5x - 1$, chaining them gives $f(g(x)) = 10x + 1$. 
- Without non-linearity, a deep stack of layers behaves exactly like a single linear layer, making the network incapable of solving highly complex problems.

- Additionally, the _choice_ of activation function is crucial for the training process itself. 
- Early neural networks used step functions, but because step functions only have flat segments (where the derivative is zero), Gradient Descent cannot make any progress. 
- Using continuous, differentiable activation functions (like the logistic function, ReLU, or ELU) provides the non-zero gradients necessary for the backpropagation algorithm to effectively tweak the model's weights and learn.

---
![[Pasted image 20260304135256.png]]

## Geron Deep Dive: Code & Advanced Math
Activation functions are what allow Neural Networks to learn non-linear decision boundaries. Without them, an MLP is just a giant linear model.

### 1. ReLU (Rectified Linear Unit)
$$ \text{ReLU}(z) = \max(0, z) $$
Continuous but not differentiable at $z=0$ (derivative is 0 or 1). Very fast to compute.
- **Problem:** "Dying ReLUs". If a neuron's weights are updated such that $W^T x + b < 0$ for all instances, the gradient becomes 0, and the neuron dies forever.

### 2. Leaky ReLU
$$ \text{LeakyReLU}_\alpha(z) = \max(\alpha z, z) $$
$\alpha$ is usually set to 0.01. This ensures the neuron never fully "dies".

### 3. ELU (Exponential Linear Unit)
$$ \text{ELU}_\alpha(z) = \begin{cases} \alpha (\exp(z) - 1) & \text{if } z < 0 \\ z & \text{if } z \ge 0 \end{cases} $$
Smoother than ReLU (differentiable everywhere), faster convergence, but slower to compute.

### Implementation
```python
from tensorflow import keras

# Setting an activation in a Dense layer
keras.layers.Dense(50, activation="elu")

# Setting Leaky ReLU requires a separate layer
keras.layers.Dense(50, kernel_initializer="he_normal")
keras.layers.LeakyReLU(alpha=0.2)
```

### Related Links
[[Regression MLP]] - [[AutoDIFF]] - [[Vanishing and Exploding Gradients]] - [[Fine tuning hyperparameters in NN]] - [[Zooming in hyper-params tuning]] - [[Building Models using functional API]] - [[Models with functional API]] - [[MODEL WITH SEQUENTIAL]] - [[Wide and Deep NEAURAL NETWORKS]] - [[Population Based Training of Neural Networks (DeepMind, 2017)]] - [[Tensorflow]] - [[Pytorch]]
