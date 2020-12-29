---
published: false
---
# Regularization

The foundational issue we deal with in machine learning is the tension between optimization and generalization. Optimization refers to the process of getting the best possible performance of a model on the training data, while generalization refers to how well the trained model would perform on data it has never seen before. Our goal is to get good generalization.  

But generalization stops improving when a model starts overfitting the training data, i.e. when it starts to learn patterns that are specific to the training data but that are not relevant to perform on the new data.

In order to prevent a model from learning misleading or irrelevant patterns found in the training data, one of the best solutions is to add constraints on what information the model is allowed to store. If a neural network is only allowed to memorize a small number of patterns, the optimization process will force it to focus on the most prominent patterns, resulting in a better chance of generalizing well.

The processing of fighting overfitting in this way is called regularization.

