The Keras Sequential API is used to build neural networks that are composed of a single, linear stack of layers connected sequentially. Here is the complete step-by-step process for creating, training, and using a model with this API:

**1. Building the Model Architecture**

- **Initialization:** You start by creating an instance of the model using `keras.models.Sequential()`.
- **Adding Layers:** You can build the network by passing a list of layers directly to the `Sequential` constructor, or by adding them one by one using the `model.add()` method.
- **Input Shape:** It is highly recommended to specify the `input_shape` argument in the very first layer so the model knows the dimensions of the data it will receive. Subsequent layers will automatically infer their input shape based on the output of the previous layer.
- **Inspection:** Once the layers are assembled, you can call `model.summary()` to display the model's architecture, the shape of each layer's output, and the total number of trainable parameters.

**2. Compiling the Model** After building the architecture, you must configure the learning process by calling the `model.compile()` method. You need to specify three main components:

- **Loss function:** The objective that the model will try to minimize (e.g., `"mse"` for regression, or `"categorical_crossentropy"` for multiclass classification).
- **Optimizer:** The gradient descent algorithm used to update the network's weights (e.g., `"sgd"` or `"rmsprop"`).
- **Metrics:** Optional metrics (like `["accuracy"]`) to evaluate the model's performance during training and testing.

**3. Training the Model** You train the model by calling the `model.fit()` method and passing it your training input features and target labels.

- You must specify the number of **epochs** (how many times the network will iterate over the entire training set) and the **batch size**.
- You can optionally pass a validation set using the `validation_data` argument. Keras will evaluate the loss and metrics on this unseen data at the end of each epoch to help you monitor for overfitting.
- The `fit()` method returns a `History` object containing a dictionary of the training and validation metrics recorded at each epoch, which you can use to plot learning curves.

**4. Evaluating the Model** Once you are satisfied with the model's performance during validation, you evaluate it on a completely unseen test set to estimate the generalization error. This is done by calling `model.evaluate()`, passing in the test data and labels.

**5. Making Predictions** Finally, you can use the trained model to make predictions on new, unseen instances by calling the `model.predict()` method. For classification tasks, this outputs the estimated probabilities for each class; alternatively, you can use `model.predict_classes()` to directly output the class index with the highest probability.