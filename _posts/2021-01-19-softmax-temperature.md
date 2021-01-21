---
published: true
---
# Softmax Temperature

It’s a hyperparameter that can be used to change the output probability distribution computed by a neural net. It is added to the logit vectors of class probabilities output by a softmax function like this:

<img src="http://chidamodu.github.io/blog/images//softmax temp formula.png">

where z is the class probabilities expressed as logit vectors produced by a neural network. And z=(z1, z2, z3....zn) and i ranges from 1 to n.
by performing the softmax function on z, we get the probability vector q
T is the temperature parameter 
	 	 	 		
In order to generate interesting looking sentences with realistically sounding words, it is rather vital to introduce the concept of randomness while generating text by predicting the next words/characters. One of the ways to do that is by reweighting the softmax probability output of the language model. We achieve the reweighting by converting the original probability distribution of the softmax output into a new probability distribution. 


**Use of softmax temperature**

Let’s consider a situation where we are building a language model to generate the next character. A high-level view of where softmax temperature is used in the language model context.

1. We train the model.

2. We sample a seed text from the corpus.

3. Get the model to predict the next character and to output the probability scores for each unique character in the target. The probability scores sum to 1. The point to note is that the target, i.e., y is an array containing the corresponding targets for every sentence in the training data and it has a shape of (sequences, unique_characters), where sequences are the number of sentences in the training data and unique_characters are the number of unique characters in the training corpus. 

4. We take the probability scores, i.e., predictions output by the model and reweight them by introducing the softmax temperature. Typically we choose various values for the softmax temperature and try to narrow it down to one best value where the text with predicted characters takes a more cohesive shape and therefore not very repetitive, but interesting.

5. After reweighting, we get the character with the highest probability value and add it to the seed text.

6. Repeat the process until the required number of characters is generated.


**Reweighting a probability distribution**

Let’s dive deeper into the reweighting procedure at a softmax temperature of 0.5. The typical reweighting procedure, fitting to the context, looks like this:

<img src="http://chidamodu.github.io/blog/images//reweighting procedure.png">

Let’s try to get an intuitive understanding of the function above. From the formula at the very beginning of this post, we can see that softmax temperature is added to the logit vectors of the output class probabilities. That’s why we take np.log of the probability scores (that are output by the softmax of the language model). 

Consider a scenario where we multiplied, instead of dividing, the softmax temperature in the softmax temperature formula. It would have made the bigger values even bigger, given that exponential is an increasing function. It becomes likely to pick the few characters with bigger probability scores repeatedly, because of the confidence of the network. Such a situation leads to predicting repetitive characters thereby resulting in boring and incohesive text. Luckily, by dividing the softmax temperature the bigger values get smaller, and therefore the characters with smaller values get a chance to be predicted as well. This introduces the randomness that excites the network to predict non-repetitive characters.  


**Implementation of the reweighting procedure - a sample**

Assume we have the following number of unique characters in our training corpus.

<img src="http://chidamodu.github.io/blog/images//unique_chracters.png">


The softmax function of the language model outputs the following probability scores predicting the highest score of 0.6 for the character ‘n’.

<img src="http://chidamodu.github.io/blog/images//original_prob.png">  


It’s very much likely we have 0s in our probability scores. We get a warning if we take the log of 0s. A workaround is to transform the first two steps in the function, reweight_distribution, i.e., taking the log of probability scores and finding the exponential of the result into the following:

<img src="http://chidamodu.github.io/blog/images//softmax_temperature_1.png"> 


Because we can get rid of the log by doing:
	e^(log(a)/T) = a^(1/T)


We can see how the probability scores are getting transformed.

<img src="http://chidamodu.github.io/blog/images//softmax_temperature_2.png">


Because the exponential result doesn't sum to 1, we divide it by its sum.

<img src="http://chidamodu.github.io/blog/images//softmax_temperature_3.png">


Finally, we transform the probability values back to represent binomial outcomes and pick the character with the highest value.
 
<img src="http://chidamodu.github.io/blog/images//reweighted_probability.png"> 


Thus the reweighting using the softmax temperature has predicted the character ' ' as opposed to the character 'n' that was originally predicted.

