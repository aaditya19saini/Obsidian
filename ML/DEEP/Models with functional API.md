Based on the sources, the **Keras Functional API** is a flexible method for building neural networks that allows for complex topologies—such as directed acyclic graphs, models with multiple inputs, models with multiple outputs, and shared layers—which are impossible to build using the simpler Sequential API.

Here is the step-by-step process of how to use the Functional API to create a model:

**1. Define the Input(s)** Instead of passing an `input_shape` to the first layer like in the Sequential API, you must explicitly create an `Input` object (e.g., `keras.layers.Input(shape=...)`). This object serves as the starting tensor for your model. If your model requires multiple inputs, you create multiple `Input` objects.

**2. Apply Layers as Functions** The API gets its name because you manipulate tensors directly by treating layers as functions. You create a layer (like `Dense` or `Conv2D`) and immediately call it, passing a tensor to it as an argument.

- _Example:_ `x = layers.Dense(32, activation='relu')(input_tensor)`. This returns a new output tensor. You can then pass this new tensor to the next layer, explicitly drawing the path the data will take through the network. No actual data is processed at this stage; you are simply telling Keras how to connect the layers together.

**3. Branch or Merge (Optional)** Because you are explicitly passing tensors around, you can split the flow of data or merge multiple branches together. For instance, you can take outputs from two completely different layers and combine them using Keras merge operations like `concatenate` or `add`. This is how architectures like Wide & Deep networks or Inception modules are built.

**4. Define the Output(s)** You pass your final tensor(s) into your output layer(s) to generate the final prediction(s). Just like inputs, a functional model can have multiple independent outputs (e.g., one output predicting a person's age and another predicting their income).

**5. Instantiate the Model** Once your input and output tensors are fully connected, you build the actual model using the `Model` class, specifying what the inputs and outputs are.

- _Example:_ `model = keras.models.Model(inputs=[input_tensor], outputs=[output_tensor])`. Behind the scenes, Keras magically traces the path from the `output_tensor` back to the `input_tensor`, retrieving every layer involved in the process and bringing them together into a graph-like data structure.

**6. Compile, Train, and Evaluate** Once the `Model` is instantiated, the rest of the workflow is identical to the Sequential API. You call `model.compile()` to set your optimizer and loss functions, `model.fit()` to train it, and `model.evaluate()` or `model.predict()` to test and use it.

---

**Concise Answer:** To use the Functional API, you start by creating an **`Input` tensor**. You then build the network by instantiating layers and immediately **calling them like functions** on tensors (e.g., passing the input tensor into the first layer, and the output of that layer into the next). This explicit linking allows you to easily merge, branch, or create multiple inputs and outputs. Finally, you construct the model by calling `keras.models.Model(inputs=..., outputs=...)`, after which you compile and train it exactly as you would a Sequential model.


[[MODEL WITH SEQUENTIAL]]

### Related Links
[[Activation functions]] - [[Regression MLP]] - [[AutoDIFF]] - [[Vanishing and Exploding Gradients]] - [[Fine tuning hyperparameters in NN]] - [[Zooming in hyper-params tuning]] - [[Building Models using functional API]] - [[MODEL WITH SEQUENTIAL]] - [[Wide and Deep NEAURAL NETWORKS]] - [[Population Based Training of Neural Networks (DeepMind, 2017)]] - [[Tensorflow]] - [[Pytorch]]
