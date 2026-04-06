# Part IV: Specialized Architectures

Based on Chapters 14-18 of Geron's book.

## 14. Deep Computer Vision (CNNs)
Convolutional Neural Networks are designed to process grid-like topology (images).
- **Convolutional Layers:** Slide filters over the image to extract feature maps. Learns hierarchical features (edges -> textures -> objects).
- **Pooling Layers:** Reduce spatial dimensions (Downsampling via MaxPooling).
- **Famous Architectures:** LeNet-5, AlexNet, VGGNet, ResNet (Introduced skip connections to train ultra-deep 100+ layer nets).

## 15. Processing Sequences using RNNs
Recurrent Neural Networks have connections pointing backward, holding "state" over time.
- Standard RNNs easily suffer from memory loss on long sequences.
- **LSTM (Long Short-Term Memory):** Uses internal gates (Forget, Input, Output) to control what information is kept or erased in the long-term memory cell.
- **GRU:** Simplified, highly efficient version of the LSTM with similar performance.

## 16. NLP with Attention
Processing raw text sequences effectively.
- Word embeddings represent text densely in vector space.
- **Encoder-Decoder Architecture:** Translates languages by encoding a sequence into a vector context, and decoding it.
- **Attention Mechanisms & Transformers:** Allow the network to "attend" or focus on specific relevant words in the input phrase, rather than stuffing the entire phrase into a single fixed vector. (The basis of modern LLMs like GPT/BERT).

## 17. Autoencoders and GANs
- **Autoencoders:** Unsupervised learning models trained to reconstruct their inputs. Used for dimensionality reduction, feature extraction, and anomaly detection.
- **GANs (Generative Adversarial Networks):** A Generator network tries to create realistic fake data, while a Discriminator network tries to distinguish real vs fake data. They train each other competitively.

## 18. Reinforcement Learning
An **agent** observes an **environment**, takes an **action**, and receives a **reward**. Deep RL uses neural networks to map observations to actions to maximize long-term rewards (e.g. Deep Q-Networks).
