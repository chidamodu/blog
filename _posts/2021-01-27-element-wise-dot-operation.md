---
published: false
---
# Element-wise and Dot operations

**Element-wise operation**

It involves applying an operation independently to every entry in a matrix, a vector, or a tensor. It requires all the arrays involved in the operation to be of same shape. Let’s see how element-wise multiplication of two matrices work in math.

<img src="http://chidamodu.github.io/blog/images//element-wise operation pic1.png">

The two matrices in the above example are of same shape (2, 3) and thus the element-wise multiplication is possible comprising each element from the same row or same column in both the matrices.

Let’s see how we can implement the element-wise multiplication using Numpy. Because of the well-optimized built-in functions in Numpy, the above operation can be done in simple ways.

Let’s import the Numpy library and declare the two matrices A and B.

<img src="http://chidamodu.github.io/blog/images//a and b for element-wise numpy.png">


The matrices A and B look like:

<img src="http://chidamodu.github.io/blog/images//a and b for element-wise operation.png">


Then the element-wise product is implemented easily like this:

<img src="http://chidamodu.github.io/blog/images//element-wise product.png">


**Dot operation**

When we have a situation to multiply two matrices that are in different shapes, the dot operation comes in handy. We can apply the dot operation only if the columns of A are same as the rows of B, considering we tend to do A dot B and not B dot A. Point to remember is that which one comes first and which one comes second, play a part in determining the shape of the resulting matrix in the case of differently shaped matrices. The dot operation is also applied on square matrices with equal number of rows and columns. Say, we have matrix A of shape (2,3) and matrix B of shape (3,2).

<img src="http://chidamodu.github.io/blog/images//dot operation pic1.png">

The columns of A is same as the rows of B, thus the dot operation is possible.


In math the notation looks like this:

<img src="http://chidamodu.github.io/blog/images//math notation of dot operation.png">


The dot operation can be implemented in numpy using np.dot command like this:

<img src="http://chidamodu.github.io/blog/images//dot product of a and b using numpy.png">


**Application in deep learning context**

Consider a Keras layer that looks like:

<img src="http://chidamodu.github.io/blog/images//keras dense layer.png">

The layer performs an activation function, 'relu' on an input, which is typically a 2D tensor and returns another 2D tensor as output. Along with the weight matrix and bias term, the layer’s activation function can be interpreted as:

<img src="http://chidamodu.github.io/blog/images//relu output.png">

Here, input is a 2D tensor
W is a 2D tensor
And the bias term, b is a vector

The above function involves the following operations:
1. A dot product between the input and weight matrix. 
2. An element-wise addition between the resulting matrix of step 1 and the vector b.
3. Finally, a relu function performed on the result of step 2. The relu operation can be expressed as max(x, 0), where x represents every independent entry of the result from step 2. Thus, the relu function is also an element-wise operation.




