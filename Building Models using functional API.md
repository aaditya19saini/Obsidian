![[Pasted image 20260328194858.png]]

- It connects all or part of the inputs directly to the output layer, as shown in Figure.
- This architecture makes it possible for the neural network to learn both deep patterns (using the deep path) and simple rules (through the short path). 
- In contrast, a regular MLP forces all the data to flow through the full stack of layers, thus simple patterns in the data may end up being distorted by this sequence of transformations.

`input = keras.layers.Input(shape=X_train.shape[1:])` 
`hidden1 = keras.layers.Dense(30, activation="relu")(input)`
`hidden2 = keras.layers.Dense(30, activation="relu")(hidden1)` 
`concat = keras.layers.Concatenate()[input, hidden2])` 
`output = keras.layers.Dense(1)(concat) model = keras.models.Model(inputs=[input]`
`, outputs=[output])`

Let’s go through each line of this code: •
1. First, we need to create an Input object. This is needed because we may have multiple inputs
2. Next, we create a Dense layer with 30 neurons and using the ReLU activation function. As soon as it is created, notice that we call it like a function, passing it the input. This is why this is called the Functional API. Note that we are just telling Keras how it should connect the layers together, no actual data is being pro cessed yet. 
3. We then create a second hidden layer, and again we use it as a function. Note however that we pass it the output of the first hidden layer. 
4. Next, we create a Concatenate() layer, and once again we immediately use it like a function, to concatenate the input and the output of the second hidden layer (you may prefer the keras.layers.concatenate() function, which creates a Con catenate layer and immediately calls it with the given inputs). 
5. Then we create the output layer, with a single neuron and no activation function, and we call it like a function, passing it the result of the concatenation. 
6. Lastly, we create a Keras Model, specifying which inputs and outputs to use.


[[Models with functional API]]
