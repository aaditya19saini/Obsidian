The “zooming process” you’re seeing in Géron’s _Hands‑On Machine Learning_ refers to a **progressive refinement strategy for hyperparameter search**.

Here’s the idea in that section of the book:

- When tuning hyperparameters (like learning rate, number of hidden units, regularization strength), you often don’t know the right scale at first.
- Instead of starting with a very narrow grid, you begin with a **broad randomized search** across wide ranges (e.g., learning rate between (10^{-5}) and (10^{-1})).
- Once you identify promising regions, you “zoom in” by running another search with tighter bounds around those good values.
- This iterative narrowing is what Géron calls the **zooming process**: start wide → find promising zones → zoom in → refine further.

📌 **Example:**

1. First randomized search: learning rate sampled from reciprocal(0.0001, 0.1).
2. Best results cluster around 0.003–0.01.
3. Second search: restrict distribution to reciprocal(0.002, 0.02).
4. Possibly zoom in again if needed.

So “zooming” is not about image magnification—it’s about **progressively focusing your search space** for hyperparameters until you converge on optimal values.

![[Copilot_20260329_155235 1.png]]

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
[[Activation functions]] - [[Regression MLP]] - [[AutoDIFF]] - [[Vanishing and Exploding Gradients]] - [[Fine tuning hyperparameters in NN]] - [[Building Models using functional API]] - [[Models with functional API]] - [[MODEL WITH SEQUENTIAL]] - [[Wide and Deep NEAURAL NETWORKS]] - [[Population Based Training of Neural Networks (DeepMind, 2017)]] - [[Tensorflow]] - [[Pytorch]]
