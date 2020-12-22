---
published: false
---
# Information bottlenecks in a neural network

In a stack of dense layers in a neural net, each layer is dependent on the information from the previous layer. If one layer drops relevant information or has an insufficient number of hidden units and therefore becomes inadequate to learn to separate classes per se. The information thus lost can never be recovered by later layers. The layer can potentially become an “information bottleneck”.

Let’s say, we have a multi-class classification task with a goal to separate 50 different mutually-exclusive topics where each data point should be classified into only one category. Therefore it is a single-label multi-class classification task. The neural network we have built is using 16-dimensional intermediate layers. 

But 16-dimensional space may be too limited to learn to separate 50 different topics. Such small layers may act as information bottlenecks, permanently dropping relevant information.



