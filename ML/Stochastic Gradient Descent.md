tags: [[Linear Regression]], [[Gradient descent]]
- picks a random instance in the training set at every step and computes the gradients based only on that single instance.
- much faster
- makes it possible to train on huge training sets


##### Much less regular than Batch Gradient Descent( due to stochastic nature):
1. instead of gently decreasing until it reaches the minimum, the cost function will bounce up and down, decreasing only on average.
2. Over time it will end up very close to the minimum, but once it gets there it will continue to bounce around, never settling down
3. once the algo stops final parameter values are good, but not optimal.
---
## randomness is good to escape from local optima, but bad because it means that the algorithm can never settle at the minimum.
- When the cost function is very irregular, this can actually help the algorithm jump out of **local minima**, so ==Stochastic Gradient Descent has a better chance of finding the global minimum than Batch Gradient Descent does.

- Solution is to gradually reduce the learning rate
- The steps start out large (which helps make quick progress and escape local minima), then get smaller and smaller, allowing the algorithm to settle at the global minimum.


#### learning schedule
- The function that determines the learning rate at each iteration is called the learning schedule.
- if learning rate is reduced too quickly--> may get stuck at the local minima / frozen halfway to the minimum 
- if learning rate is reduced to slow--> End up with a suboptimal solution( jumping around the minimum), if training is halted too early?


