---
published: false
---
# Batch Learning

Incremental learning that happens over a group of data points at once is called batch learning. It’s in the middle ground between the online and offline learning. Online Learning involves training the existing model typically on every new observation. Offline comprises of adding the new set of observations to the existing dataset that we used to train the already existing model and retraining the model again on this newly formed dataset.

The size of a batch involved in batch learning really depends on a business application, the amount of data received, and the frequency, of the learning from the new data points, that is necessary to the business context.

In sklearn the estimators (algorithms) with the method partial_fit are eligible for batch learning.


