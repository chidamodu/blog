---
published: false
---
# Decorrelated Trees - Random Forest

Random Forest, an ensemble learning method helps to build decorrelated trees using the concept of **feature subsetting**, also called as **subspace sampling**. According to the technique, for any node in any tree, instead of finding the best split among all features, we randomly select a few features, and find the best split among those ones. The number of features (denoted as max_features in sklearn library) to consider at each split is a hyperparameter and therefore can be tuned. Sklearn provides options to find the max_features and the typical one is:

**max_features = sqrt(n_features)**

where n_features is the total number of features in the training dataset
sqrt indicates that we are taking square root of n_features

This technique provides the nodes farther down a decision tree, in Random Forest, an opportunity to pick the significant features. Without the concept of feature subsetting, the significant features might be used only for the first few splits leaving the lower nodes to select only from the insignificant ones.



