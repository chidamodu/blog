---
published: false
---
# How does Tokenizer of Keras Preprocessing work?

We cannot feed a machine learning model or a neural net input data in the form of text. We, therefore, have to convert the text into numbers of some sort for the models to understand. This is where a tokenizer helps and it is one of the ways that TensorFlow's Keras API provides to deal with text data. It generates a dictionary with words as keys and, in simplest terms, it associates each word with a number and that’s stored as the dictionary values. We shall then use some methods of the tokenizer to create number sequences out of sentences. A tokenizer is initialized by calling **Tokenizer()**.

It has the following options:

-num_words: We can choose the number of unique words in the input text to be considered for encoding. What does this mean? Say, we have quite a large input data with a plentitude of unique words. Instead of creating a dictionary with all the unique words in the input data, we can select the top 100 words. In situations where top words (tops words mean: most frequently occurring words) would suffice to train a model and infer from the trained model using the word encodings (in simple terms encodings mean: numbers that are used to represent words), the num_words option would come in handy.

Example:**tokenizer=Tokenizer(num_words=100)**. The tokenizer selects the first 100 words by frequency of their occurrence volume. 

-fit_on_texts: It takes the data and tokenizes it. We cannot check the outcome of **tokenizer.fit_on_texts**, because we are able to access the outcome in the form of a dictionary using **word_index**, which is explained in the next bullet point.

Example:**tokenizer.fit_on_texts(sentences)**
Here sentences represent the input text data.

-word_index: This property returns a dictionary with key value pairs where key is a word and value is a token (token here means: a numerical value of some sort) for that word. Every unique word is assigned a distinct number.

Example: **word_index=tokenizer.word_index**
Let’s check out a simple example that demonstrates word_index of the tokenizer fitted on the given input sentences here: 
sentences=['I love swimming', 'I learnt to speak french when I visited France a couple of years ago']


<img src="http://chidamodu.github.io/blog/images/tokenizer_1.pdf">


P.S.: Tokenizer strips punctuation out. It can be seen in the above image that **'I'** is represented as **'i'** and so is **'F'** as **'f'** in France in the second sentence.

-texts_to_sequences: When this method is accessed using the tokenizer, it converts each word into a list of numbers and therefore transforms the entire sentence into a sequence of numbers. 

Example: 
Let’s assume the following input data with four sentences.
sentences=['I love swimming', 'I learnt to speak french when I visited France a couple of years ago', 'The coronavirus outbreak is terrible', 'Financial independence is a must have for a woman']

To drive the point home, we first initialize the tokenizer, fit it on sentences (the input data), and finally convert the given sentences into a sequence of numbers using the fit_on_texts method of the tokenizer. Let’s check the concept just explained in the below illustration:

https://github.com/chidamodu/blog/blob/gh-pages/_posts/tokenizer_pic2.png

OOV_token: What happens when we have words in test data that are not seen by the trained model? Well, the unseen words are omitted by the trained model while making inference. In case of numerous unseen words present in the test data, omitting those words result in a huge loss of information. Let’s check the simple illustration below:


https://github.com/chidamodu/blog/blob/gh-pages/_posts/tokenizer_pic%203.png


Part of the word_index dictionary that was used to fit the trained model for reference:

https://github.com/chidamodu/blog/blob/gh-pages/_posts/tokenizer_pic%204.png


In the first sentence, the unseen words: **'really'**, **'my'**, and **'turtle'** are omitted because these words weren’t present in the word_index of the trained model. 
Likewise in the second sentence, the unseen words: **'stay', 'in', 'shelter', 'in', 'place',** and **'due'** are omitted.

Luckily, the tokenizer has a property, oov_token to deal with it. OOV means “Out of Vocabulary”. Like before we first initialize the tokenizer, but here we assign a distinct value that’s not easily confused with other words in the input data to oov_token to give the unseen words a better coverage. You can assign any distinct values to oov_token. I have assigned it "<OOV>". The rest of the steps follow as mentioned under texts_to_sequences bullet point.  Let’s check the option in action in the following illustrations with the same examples used before for easy understanding:

Here the tokenizer is initiated with oov_token.
  
https://github.com/chidamodu/blog/blob/gh-pages/_posts/tokenizer_5.png

The oov_token gets a numerical value ('<OOV>' : 1) assigned as other words in the dictionary.
  
https://github.com/chidamodu/blog/blob/gh-pages/_posts/tokenizer_6.png

The unseen words in the first sentence: **'really'**, **'my'**, and **'turtle'** are assigned a value of 1 as they are considered as oov_token. 
Similarly the unseen words in the second sentence: **'stay'**, **'in'**, **'shelter'**, **'in'**, **'place'**, and **'due'** are assigned a value of 1.

The test_sequence now comprises values for all the data present. Thanks to oov_token!

https://github.com/chidamodu/blog/blob/gh-pages/_posts/tokenizer_7.png
