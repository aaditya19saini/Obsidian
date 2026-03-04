
### hyperbolic tangent function
- S shaped, continuous  and differentiable? \
- output value ranges from **-1 to 1** (0/1 in log regression)
- which tends to make each layer’s output more or less centered around 0 at the beginning of training. This often helps speed up convergence.

  $tanh(z) = 2σ(2z) – 1$
### Rectified Linear Unit function (RELU)
- continuous + not differentiable at z=0
- 