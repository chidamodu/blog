---
published: true
---
## Why RNN?

Well, we could use a standard neural network with a few hidden layers, maybe even dense ones to represent the input text. But this network does not seem to work very well because of the following reasons:
- The input sentences could be of different lengths and so are the outputs for the corresponding sentences. Even if we solve the issue by padding with zeros, it does not seem to be a good representation.
- In order to make complete sense it rather becomes necessary to share information across texts (i.e., words) at different positions. So, for example, we will know a person’s name, say, Harry appearing in the first part of the sentence refers to the same Harry appearing in the later part of the sentence.


## How’s RNN better?

RNN represents each word at each time step and predicts the outcome at each time step. What’s different with RNN is that it passes the information from a previous layer to a next layer in the form of activations. Before time step 1, the activation, a0 is set as a zero vector. So the following happens at time step 1:

	a0 is passed
	input word, say, x1 (this is the first word represented at time step 1) is passed
	y_pred1 is predicted 
	a1 is calculated

Let’s do one more time step to get a deeper understanding:
At time step 2, the following happens:

	a1 is passed 
	input word, say, x2 (this is the second word represented at time step 2) is passed
	y_pred2 is predicted 
	a2 is calculated, which is then passed as input to time step 3


## Passing information across layers ##

RNN uses the same set of parameters across all the time steps:

![]({{site.baseurl}}/https://github.com/chidamodu/blog/gh-pages/images/RNN.png)

Weight matrices and bias at input level:
	-Weight matrix relating an activation to an input x (it’s represented as Wax in the figure)
	-Bias related to activation at the input level (it’s represented as ba in the figure)

Weight matrices and bias at output level:
	-Weight matrix relating an activation to an output y (it’s represented as Wya in the figure)
	-Bias relating an activation to an output y (it’s represented as by in the figure)

Weight matrix at the outcome of each time step:
	-Weight matrix relating an input activation to an output activation at each time step 
	(it’s represented as Waa in the figure)
	
