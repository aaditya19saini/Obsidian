

## Geron Deep Dive: Code & Advanced Math
Grid-searching neural networks takes astronomically long because training deep networks is notoriously slow. Keras Tuner simplifies this dramatically using highly optimized algorithmic searches.

### Keras Tuner (Hyperband) Implementation
Hyperband algorithmically trains a huge number of models for highly truncated epochs, instantly discarding the poorly performing halves, and expanding epochs only for the competitive models.

```python
import keras_tuner as kt

def build_model(hp):
    n_hidden = hp.Int("n_hidden", min_value=0, max_value=8, default=2)
    n_neurons = hp.Int("n_neurons", min_value=16, max_value=256)
    learning_rate = hp.Float("learning_rate", min_value=1e-4, max_value=1e-2, sampling="log")
    
    model = keras.models.Sequential()
    model.add(keras.layers.Flatten())
    for _ in range(n_hidden):
        model.add(keras.layers.Dense(n_neurons, activation="relu"))
    model.add(keras.layers.Dense(10, activation="softmax"))
    
    optimizer = keras.optimizers.SGD(learning_rate=learning_rate)
    model.compile(loss="sparse_categorical_crossentropy", optimizer=optimizer, metrics=["accuracy"])
    return model

tuner = kt.Hyperband(
    build_model, objective="val_accuracy", 
    max_epochs=10, factor=3, directory="my_mnist", project_name="hyperband_run"
)
# tuner.search(X_train, y_train, epochs=10, validation_data=(X_valid, y_valid))
```

### Related Links
[[Activation functions]] - [[Regression MLP]] - [[AutoDIFF]] - [[Vanishing and Exploding Gradients]] - [[Zooming in hyper-params tuning]] - [[Building Models using functional API]] - [[Models with functional API]] - [[MODEL WITH SEQUENTIAL]] - [[Wide and Deep NEAURAL NETWORKS]] - [[Population Based Training of Neural Networks (DeepMind, 2017)]] - [[Tensorflow]] - [[Pytorch]]
