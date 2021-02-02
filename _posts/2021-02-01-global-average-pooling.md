---
published: true
---
# GlobalAveragePooling

GlobalPooling operates on spatial information, i.e., location information like edges and corners in image data. It has two options:
- Finding averaging
- Finding maximum

Let’s talk about the first option, a, finding average. GlobalAveragePooling is an operation that calculates the average of each feature map in the previous layer. It has the following advantages:

1. It has no trainable parameters and therefore using this in a model architecture will help 		reducing the tendency to overfit.

2. Fully connected dense layers have a lot of parameters. Dropouts are typically added to such a network to prevent overfitting. With fewer parameters, through using GlobalAveragePooling, the dropouts layers can be reduced thus contributing to speed up the model training.
