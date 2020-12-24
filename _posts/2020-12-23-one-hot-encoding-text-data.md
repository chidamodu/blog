---
published: true
---
# One Hot Encoding of text data

The goal of this post is to introduce the steps involved in transforming text data into tensors, which are then ready to be fed into a neural network, using one-hot-encoding technique. Let’s consider a binary classification task of classifying movie reviews into either positive or negative ones just based on the text content of the reviews. 

For this task, let’s consider the "IMDB dataset", a set of 50,000 highly-polarized reviews from the Internet Movie Database. They are split into 25,000 reviews for training and 25,000 reviews for testing, each set consisting in 50% negative and 50% positive reviews. 

<img src="http://chidamodu.github.io/blog/images//download.png">


Here we are downloading the train and test dataset from the Keras package where the train and test data were already converted into integers. 

<img src="http://chidamodu.github.io/blog/images//train data into integers.png">


We can also convert the text into integers ourselves by following:

1. Split the words in a sentence.
2. Assign a unique number, which acts as a unique index, to each word.
3. Form a dictionary with the words as keys and their unique indexes as values.


Here’s the code to implement the three steps above:

<img src="http://chidamodu.github.io/blog/images//creating a dictionary with word tokens ourselves.png">


<img src="http://chidamodu.github.io/blog/images//dictionary with word tokens.png">


Sentences of words to sequences of numbers:

<img src="http://chidamodu.github.io/blog/images//use the dict with word tokens to transform sentences.png">


After the transformation we get:

<img src="http://chidamodu.github.io/blog/images//sentence of words into sequence of numbers.png">


We have transformed our text data into numbers. Now what? We cannot feed lists of integers into a neural network. We have to turn our lists into tensors. One way to do that is to one-hot-encode our lists to turn them into float type vectors of 0s and 1s. 

<img src="http://chidamodu.github.io/blog/images//function to vectorize x_data.png">


The x_train after the transformation above:

<img src="http://chidamodu.github.io/blog/images//x_train after vectorization.png">


We have to vectorize y_train and y_test too:

<img src="http://chidamodu.github.io/blog/images//Vectorize y-labels too.png">


Here's an outline of a sequential model with three hidden layers, input, and output. Because it is a classification task the output is in the form of probability:

<img src="http://chidamodu.github.io/blog/images//look at the network.png">


Here we are considering only the 10,000 most frequently occurring words in the training data. So rare words will be discarded. This further allows us to work with vector data of manageable size.

<img src="http://chidamodu.github.io/blog/images//the 10000 most frequent words.png">


Concretely, this would mean for instance turning a sequence [8, 100, 567] into a 10,000 dimensional vector (the 10,000 dimensional vector is because we are considering the 10,000 most frequent words in the training data) that would be all-zeros except for indices 8,100, and 567 which would be ones. Then we could use a Dense layer as the first layer, i.e., input layer, in our network, that’s capable of handling floating-point vector data.

<img src="http://chidamodu.github.io/blog/images//sample sequential model.png">
