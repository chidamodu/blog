# How is the embedding layer’s internal dictionary different?

Before we dive into explaining, let's establish what we are comparing the embedding layer’s internal dictionary to. For example, let’s consider the popular IMDB Movie Review dataset (can access this dataset from Keras API or on Kaggle). Our task is to predict whether the reviews are positive or negative. 

We cannot send raw text as input into a neural network. One of the ways is to transform the text into integers tokens and then into vectors. The most basic way to convert the integer tokens into vectors is achieved through one-hot encoding. We create a dictionary by assigning unique integers to each unique word in every sentence according to the chosen vocabulary size and the maximum length of each sentence. Then we one-hot encode each sentence, i.e., only the integers, in each sentence, that are present in the dictionary are converted into 1s and the ones that are not present in the dictionary are converted into 0s. Thus the text is converted into vectors during the text vectorization process. 

**What is an Embedding Layer?**

It is essentially a dictionary lookup that maps integer indices, which stand for specific words, to dense vectors. It takes the integers indices of corresponding words as input, looks up these integers in an internal dictionary, and returns their associated vectors.

<img src="http://chidamodu.github.io/blog/images//embedding layer outline.png">

It takes a 2D tensor of integers of shape (samples, sequence_length) as input and returns a 3D floating-point tensor of shape (samples, sequence_ length, embedding_dimensionality). Here samples mean the number of words considered in the vocabulary, i.e., the vocabulary size. 
Let’s refer to the IMDB Movie Review dataset. There are 50000 reviews in total and downloading from Keras we get 25000 reviews for training and the remaining equal half for testing. Let’s restrict the number of words in the datasets to the 10000 most common words chiefly to have a workable vocabulary size that’s not computationally intensive. Now, this 10000 represents the samples in our 2D tensor input for our movie review prediction task. 


**Instantiating an Embedding Layer**

When an embedding layer is instantiated, it starts by assigning random vectors in its internal dictionary. During each backpropagation step, it learns the associations and patterns amongst the vectors and gradually adjusts and structures them. Once trained completely, the embedding space will show a lot of meaningful structures specialized for the specific problem for which the model was trained.

Instantiating the layer in Keras

<img src="http://chidamodu.github.io/blog/images//instantiating embedding layer.png">

Where 10000 represents our samples, i.e., vocabulary size
64 represents the dimensionality of the embeddings


**Meaningful structures learned by embedding spaces**

What we expect while transforming words to vectors is that the geometric relationships between the vectors reflect the semantic relationships between the associated words. Word embeddings are meant to map the human language into geometric space. In real-world word embeddings spaces, common examples of meaningful transformations are gender vectors and plural vectors.
			
A 2D illustration of how two words: King and Queen might get represented. Remember, the words will be represented in their corresponding vector forms. Typically special charcters and punctuations are removed from the text. Initially the embedding layer might assign random vectors to both King and Queen. Therefore no associations are formed.

<img src="http://chidamodu.github.io/blog/images//embedding before learning meaning.png">


Through backpropagation, the embedding layer learns the gender association as shown in the pic below:

<img src="http://chidamodu.github.io/blog/images//embedding_gender association.png">

It has learnt that King + female gender is equivalent to the gender Queen and makes an association shown in the form of arrow in the picture.


Likewise, it learns the plural forms.

<img src="http://chidamodu.github.io/blog/images//plural associations embedding.png">


Thus the embedding layer’s internal dictionary offers powerful associations and exhibits useful properties.






