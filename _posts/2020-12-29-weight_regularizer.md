---
published: false
---
# Adding weight regularization

We associate a cost to the loss function of a neural network in case of having large weights. In other words, we punish the network for having large weights. This, in turn, forces the weights to take only small values. This is called weight regularization. This is one of the useful techniques implemented to prevent overfitting. In Keras, weight regularization is added by passing **kernel_regularizer** as a keyword argument to the layers.

The cost, associated with large weights, comes in two flavors:
1. L1 regularization, where the cost added is proportional to the absolute value of the weights coefficients. 
2. L2 regularization, where the cost added is proportional to the square of the value of the weights coefficients.

