---
published: true
---
# Cross-Validation

It’s a rotation estimation technique and it is the gold standard in the machine learning realm.

**How does it work?**

It splits the training data into folds and for every fold, it picks a data point that’s not in the fold. The data point thus picked is used as the test data for that particular fold. So it trains a model using the training fold and tests the model’s performance on the picked test data point. The cool thing is that this test data point gets reused when it gets shuffled as one of the training data points in the other training folds (typically 10-folds is chosen for cross-validation). Thus the technique leverages the use of training data, at the same time provides a legit way to build up an estimate of the performance of the machine learning model on unseen data. 

Benefits of the technique include:

**Testing**

To test how well a predictive model would perform on test data (unseen data) by using a part of the training set and therefore not touching the precious test set. 


**Comparing**

To compare and contrast a bunch of predictive models based on their performance in order to pick the best model that’s most fitting to the given data. 


**Tuning (hyperparameter)**

Also, the technique is used to find the optimum value of parameters (also called hyperparameters) for a model. Grid Search (in sklearn library) uses cross-validation to find the best value for a parameter.

