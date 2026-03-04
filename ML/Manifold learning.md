**Manifold Learning** is a specific approach to **Dimensionality Reduction** that works by modelling the geometric manifold on which the training instances lie, rather than simply projecting data onto a lower-dimensional plane


##### The Core Concept: The Manifold

A d-dimensional manifold is defined as a part of an n-dimensional space (where d<n) that locally resembles a d-dimensional hyperplane 

High-dimensional data that actually lives on a lower-dimensional surface.
- looks complicated globally but is much simpler locally 


##### The Implicit Assumption

Manifold learning is often accompanied by an implicit assumption: that the machine learning task (such as classification or regression) will become **simpler** if the problem is expressed in the lower-dimensional space of the manifold

- **Caveat:** This assumption does not always hold. In some cases, a decision boundary might be a simple plane in 3D space (cutting through the Swiss roll) but become a complex collection of disjoint segments when the manifold is unrolled into 2D
![[Pasted image 20260120215516.png]]figure:
For example, in the bottom row of Figure 8-6, the decision boundary is located at x1 = 5. This decision boundary looks very simple in the original 3D space (a vertical plane), but it looks more complex in the unrolled manifold (a collection of four independent line segments).