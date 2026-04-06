# Part III: ANNs and Deep Learning

Based on Chapters 10-13 of Geron's book.

## 10. Introduction to Keras & TensorFlow
- **The Perceptron:** Simplest ANN architecture based on a single TLU (Threshold Logic Unit).
- **Multi-Layer Perceptron (MLP):** The foundation of Deep Learning. Must use non-linear activation functions (ReLU, sigmoid, tanh) to learn non-linear patterns.
- **Keras APIs:**
  - *Sequential API:* Simple stack of layers.
  - *Functional API:* Allows complex topologies (multiple inputs/outputs, skip connections).
  - *Subclassing API:* Maximum flexibility in custom forward passes.

## 11. Training Deep Neural Networks
Training deep networks is difficult due to the **Vanishing/Exploding Gradients** problem during backpropagation.
- **Initialization:** Use Glorot (Xavier) for Tanh/Sigmoid, He Initialization for ReLU.
- **Activation Functions:** ELU, SELU, Leaky ReLU outperform standard ReLU by preventing "dying ReLUs".
- **Batch Normalization:** Normalizes the inputs to layers across the batch, substantially decreasing training time and dampening the vanishing gradient issue.
- **Optimizers:** Faster alternatives to basic SGD:
  - Momentum, Nesterov Accelerated Gradient (NAG)
  - RMSProp, Adam, Nadam. (Adam is typically the default recommendation).

## 12. Custom Models & Training
TensorFlow operates using efficient C++ computational graphs under the hood. 
- You can write custom loss functions, regularizers, metrics, and layers by subclassing `keras.losses.Loss` or `keras.layers.Layer`.
- You can write fully custom training loops using `tf.GradientTape` to compute gradients automatically via AutoDiff.

## 13. The tf.data API
Deep learning models are data-hungry. The `tf.data` API provides highly efficient loading and preprocessing pipelines.
- Prevents GPU starvation via `.prefetch()`.
- Supports multithreaded data transformations via `.map(num_parallel_calls)`.
- Handles interleaving multiple files on disk into a single smooth training stream.
