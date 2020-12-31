---
published: true
---
# How does weight regularization prevent overfitting?

The concept of weight regularization is used to prevent overfitting. We have two options: 
L1 regularization adds an L1 penalty equal to the absolute value of the magnitude of coefficients. In other words, it limits the size of the coefficients.

L2 regularization adds an L2 penalty equal to the square of the magnitude of coefficients.
But how does weight regularization help preventing overfitting? Let’s take a deep dive.

As per Occam's Razor principle: given two explanations for something, the explanation most likely to be correct is the "simplest" one, the one that makes the least amount of assumptions. This principle also applies to the models learned by neural networks: given some training data and network architecture, there are multiple sets of weights values, i.e., multiple models, that could explain the data, simpler models are less likely to overfit than complex ones.

Along the lines, we can side with a simple interpretation where the complexity of a function is measured by adjusting its weight vector. For example, let’s consider, without getting too much into the computation, the following linear function:

**f(x) = (w^T) * x**

where w^T represents the transpose version of w
x would be input or features in our context

It’s possible to measure the complexity of the linear function f(x) by some norm of its weight vector, ||w||^2 (||w||^2 represents the squared form of w). Here norm means simply the magnitude, of the weight vector, w. The squared form of the weight vector also referred to as the L2 norm or L2 penalty (as mentioned above). The usual procedure is to add the norm of the weight vector as a penalty term to the loss function, which we try to minimize during model training.

Fitting to our linear context here, the loss function gets an additional term as follows:

**L(w, b) + (𝜆/2 * ||w||^2)**

where 𝜆 is a regularization constant that is a non-negative hyperparameter
(w,b) are the weight and bias parameters respectively
L is the loss function

When 𝜆 equals 0, we recover the original loss function and for 𝜆>0, we start restricting the size of ||w||.

We can also use the L1 norm. But one reason to work with the L2 norm is that it places a penalty on large components of the weight vector. In case of the weight vector growing too large, our learning algorithm might focus on minimizing the weight norm ||w||^2 instead of minimizing the training error. This biases our learning algorithm towards models that distribute weight evenly across a larger number of features. This leads to generating models that are more robust to different features instead of fitting them well to too specific patterns in the training data.

L2 regularization shrinks the size of w towards 0. Thus the learning algorithm decays w at each step of training. That is why the method is sometimes called weight decay. Although the L2 norm shrinks the size of the weight vector, it does not force the weight vector, of features, to 0. By contrast, the L1 norm clears the weights, of some features, to zero, thereby concentrating the weights on a small set of features. This technique is thus helpful in selecting the important features and therefore called feature selection. L2-regularized linear models constitute the classic ridge regression algorithm and L1-regularized linear regression comprises of a similarly fundamental model in statistics, which is popularly known as lasso regression.
 
 
 
 
 

