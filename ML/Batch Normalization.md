# Batch Normalization
## Geron Deep Dive: Code & Advanced Math
Introduced by Ioffe and Szegedy (2015), Batch Normalization heavily mitigates vanishing/exploding gradients. It adds an operation right before (or after) the activation function that **zero-centers and normalizes each input, then scales and shifts it**.

### The Math (Per mini-batch)
1. **Empirical Mean:** $ \mu_B = \frac{1}{m_B} \sum_{i=1}^{m_B} \mathbf{x}^{(i)} $
2. **Empirical Variance:** $ \sigma_B^2 = \frac{1}{m_B} \sum_{i=1}^{m_B} (\mathbf{x}^{(i)} - \mu_B)^2 $
3. **Normalize:** $ \hat{\mathbf{x}}^{(i)} = \frac{\mathbf{x}^{(i)} - \mu_B}{\sqrt{\sigma_B^2 + \epsilon}} $
4. **Scale and Shift:** $ \mathbf{z}^{(i)} = \gamma \otimes \hat{\mathbf{x}}^{(i)} + \beta $

Where $\gamma$ and $\beta$ are trainable parameter vectors (learned via backprop), scaling and deciding the mean of the distribution for that layer.

### Keras Implementation
```python
from tensorflow import keras

model = keras.models.Sequential([
    keras.layers.Flatten(input_shape=[28, 28]),
    keras.layers.BatchNormalization(), # Applied before Activation explicitly:
    keras.layers.Dense(300, use_bias=False), # Bias mathematically absorbed by BN beta
    keras.layers.BatchNormalization(),
    keras.layers.Activation("relu"),
    keras.layers.Dense(10, activation="softmax")
])
```
