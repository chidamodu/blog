---
published: false
---
# What is an epoch?

One epoch can be considered as a complete pass through the entire data where our neural network gets to work on, i.e., learn from, the entire training dataset

Let’s consider a situation where we are tasked to solve a computer vision problem with 60000 images in our training data. We have decided on 5 epochs to train our data. We can think of the epochs in the following way:

<img src="http://chidamodu.github.io/blog/images//entire dataset_epoch.png">

Typically, we cannot fit all 60000 images in the computer memory. So we divide the dataset into mini-batches of images. In this context, we have decided to go with 500 images per batch (i.e., our batch_size=500), so dividing 60000 images by 500 (per batch) gives us 120 batches.

If we zoom in on the above for-loop with batch_size=500, we get the following:

<img src="http://chidamodu.github.io/blog/images//epochs with batches.png">

The entire training set is split into 120 batches of images and the network passes through all 120 batches for every epoch. 




