**Vanishing and exploding gradients** are problems that occur during the training of deep neural networks, causing different layers to learn at widely different speeds.

Because the backpropagation algorithm works by going from the output layer to the input layer to propagate the error gradient, the gradients can become highly unstable:

- **The Vanishing Gradients Problem:** Gradients often get smaller and smaller as the algorithm progresses down to the lower layers. Consequently, the Gradient Descent updates leave the lower layer connection weights virtually unchanged, meaning **the network never converges to a good solution**.
- **The Exploding Gradients Problem:** The opposite occurs when gradients grow bigger and bigger. This causes the layers to receive insanely large weight updates, and **the algorithm diverges** (this is mostly encountered in recurrent neural networks).
## History 

**Why does this happen?**
- In 2010, researchers Xavier Glorot and Yoshua Bengio discovered that the root of the problem was the combination of the **logistic sigmoid activation function** and the standard weight initialization technique of the time (random initialization with a mean of 0 and a standard deviation of 1).
- This combination causes the variance of the outputs of each layer to be much greater than the variance of its inputs. As the signal goes forward, the variance keeps increasing until the logistic function saturates at 0 or 1.
- When this happens, the derivative is extremely close to 0, leaving virtually no gradient to propagate back down through the network.

### How to Solve These Problems


**1. Better Weight Initialization** To keep the signal flowing properly, the variance of the outputs of each layer needs to be equal to the variance of its inputs, and the gradients must have equal variance before and after flowing through a layer. This can be achieved using specific initialization strategies depending on your chosen activation function:

- **Glorot (or Xavier) initialization:** Used for None, Tanh, Logistic, and Softmax activation functions.
- **He initialization:** Used for the ReLU activation function and its variants.
- **LeCun initialization:** Used for the SELU activation function.

**2. Nonsaturating Activation Functions** Because the logistic function saturates for large positive or negative values, switching to activation functions that do not saturate as easily helps tremendously.

- **ReLU** is a popular choice, but it can suffer from "dying ReLUs" where neurons stop outputting anything other than 0.
- Variants like **Leaky ReLU**, **ELU** (Exponential Linear Unit), and **SELU** (Scaled ELU) generally perform better and prevent neurons from dying. SELU, when used under specific conditions, even allows a dense network to "self-normalize" and solve the gradient problems entirely.

**3. Batch Normalization (BN)** Proposed in 2015, this technique adds an operation just before or after the activation function of each hidden layer. It zero-centers and normalizes each input, then scales and shifts the result using two new parameter vectors per layer. This technique strongly reduces the vanishing/exploding gradients problem, allowing you to use saturating activation functions (like the logistic function) and much larger learning rates.

**4. Gradient Clipping** To specifically lessen the **exploding** gradients problem, you can simply clip the gradients during backpropagation so that they never exceed a certain threshold. This technique is most commonly used in recurrent neural networks, where Batch Normalization is trickier to implement.


### Related Links
[[Activation functions]] - [[Regression MLP]] - [[AutoDIFF]] - [[Fine tuning hyperparameters in NN]] - [[Zooming in hyper-params tuning]] - [[Building Models using functional API]] - [[Models with functional API]] - [[MODEL WITH SEQUENTIAL]] - [[Wide and Deep NEAURAL NETWORKS]] - [[Population Based Training of Neural Networks (DeepMind, 2017)]] - [[Tensorflow]] - [[Pytorch]]
