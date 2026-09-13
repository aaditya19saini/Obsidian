**Automatic differentiation**, often shortened to **autodiff**, is a set of techniques used to automatically and precisely compute the gradients of a function.

Instead of requiring you to manually solve complex calculus equations or rely on imprecise numerical approximations, autodiff calculates the exact gradient (up to machine precision) by tracking the operations your code performs. It does this by breaking down the function into a computation graph made of intermediate variables and basic elementary operations (like addition, multiplication, or exponentials). It then systematically applies the **chain rule** of calculus across this graph to evaluate the derivatives.

Autodiff generally operates in two main modes:

- **Forward mode:** Gradients flow sequentially from the inputs to the outputs, left to right alongside the data.
- **Reverse mode:** Gradients are propagated backward through the graph, from the output back to the inputs.

In deep learning, the famous **backpropagation algorithm** is simply a specific application of **reverse-mode autodiff**. Reverse mode is highly efficient for neural networks because it is perfectly suited for scenarios where a function has many variables (like thousands of connection weights) but very few outputs (like a single loss value). It can compute the gradients of the error with regard to every single model parameter in just two passes: one forward pass to make a prediction, and one backward pass to compute the gradients.

related:
[[Tensorflow]]


### Related Links
[[Activation functions]] - [[Regression MLP]] - [[Vanishing and Exploding Gradients]] - [[Fine tuning hyperparameters in NN]] - [[Zooming in hyper-params tuning]] - [[Building Models using functional API]] - [[Models with functional API]] - [[MODEL WITH SEQUENTIAL]] - [[Wide and Deep NEAURAL NETWORKS]] - [[Population Based Training of Neural Networks (DeepMind, 2017)]] - [[Tensorflow]] - [[Pytorch]]
