---
published: false
---
# Encoding Text Data - a high level

Let’s consider the task of classifying the movie reviews into positive and negative ones using the popular IMDB dataset. We have to convert the text data into either integer or float tensors in order to feed into a neural network. The two options we have are as follows:

-We could start by randomly assigning some numbers to the words in a movie review and then gradually learn the appropriate word vectors through back propagation.

-We could use pre-computed vectors that were computed using word occurrence statistics in a well structured word embedding space.  
