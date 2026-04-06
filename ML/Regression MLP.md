

## Geron Deep Dive: Code & Advanced Math
Building a Regression MLP is almost identical to a classification MLP, except:
1. The output layer has **no activation function** (or `relu`/`softplus` if output must be strictly positive).
2. The output layer usually has exactly **1 neuron** (predicting a single continuous value).
3. The loss function is **MSE** (Mean Squared Error), or **Huber loss** if there are noisy outliers.

### Keras Sequential Implementation
```python
from tensorflow import keras

model = keras.models.Sequential([
    keras.layers.Dense(30, activation="relu", input_shape=[8]), # e.g. 8 features
    keras.layers.Dense(30, activation="relu"),
    keras.layers.Dense(1) # No activation for regression
])

model.compile(loss="mean_squared_error", optimizer=keras.optimizers.SGD(learning_rate=1e-3))
# history = model.fit(X_train, y_train, epochs=20, validation_data=(X_valid, y_valid))
```

### Related Links
[[Activation functions]] - [[AutoDIFF]] - [[Vanishing and Exploding Gradients]] - [[Fine tuning hyperparameters in NN]] - [[Zooming in hyper-params tuning]] - [[Building Models using functional API]] - [[Models with functional API]] - [[MODEL WITH SEQUENTIAL]] - [[Wide and Deep NEAURAL NETWORKS]] - [[Population Based Training of Neural Networks (DeepMind, 2017)]] - [[Tensorflow]] - [[Pytorch]]
