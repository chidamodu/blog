---
published: true
---
# Build a Decision Tree Classifier using Spark ML Package

The Spark ML package provides an API for pipelining data transformers, estimators, and model selectors. In this post, I would like to give a high level view of building a decision tree model, setting a pipeline, and required formats to transform the data. 

First import the necessary packages and after that the below steps follow: 

- The ML package needs the data in a dataframe with labels in double-precision floating point numbers type and features in vector format. This can be achieved through:

	data.map(lambda r: [r[-1],Vectors.dense(r[:-1])]).toDF(['label','features'])

We are converting the features into vectors using Vectors.dense method (which is imported from **pyspark.mllib.linalg**) and storing both the labels and transformed features in a dataframe by calling **.toDF** method.

- Next we use the following transformers:

**StringIndexer() on label:** to add the metadata to the label column.

	labelIndexer = StringIndexer(inputCol='label', outputCol='indexedLabel').fit(transformed 		training data from step 1)

outputCol represents the result of labelIndexer and that’s named here as ‘indexedLabel’.

**VectorIndexer() on features:** to find the categorical features and index them.

	featureIndexer = VectorIndexer(inputCol='features', outputCol='indexedFeatures', 				maxCategories=2).fit(transformed training data from step 1)

In the example used here there are only 2 categorical features. outputCol represents the result of featureIndexer and that’s named here as 'indexedFeatures'.

- We can initialize the decision tree model as follows:

	dTree=DecisionTreeClassifier(labelCol='indexedLabel', featuresCol='indexedFeatures')

indexedLabel is the output column of labelIndexer and indexed Features is the output column of featureIndexer.

- We shall now chain the indexers and tree in a pipeline as follows:

	pipeline=Pipeline(stages=[labelIndexer, featureIndexer, dTree])

We have set labelIndexer and featureIndexer above and also have initialized the decision tree classifier as the estimator.

- It’s possible to cross-validate by setting a parameter grid by using the **ParamGridBuilder()** and adding parameters to the builder by using the **addGrid()** method. Then we shall put the builder into functioning by calling **build()** on it.
Example:
Let set the grid with just one parameter, maxDepth and a list of values to choose the optimum value for the parameter.

	paramGrid = ParamGridBuilder().addGrid(dTree.maxDepth, [2,3,4,5,6,7]).build()

- We can define the evaluation metric by using MulticlassClassificationEvaluator as follows:

	evaluator = MulticlassClassificationEvaluator
	(labelCol='indexedLabel',predictionCol='prediction', metricName='f1')

We are setting the F-1 score as an evaluation metric with predicted labels stored in the column name 'prediction'. The 'indexedLabel' is the result of labelIndexer described above.

- We can set up a 5-fold cross validation as follows:

	crossval = CrossValidator(estimator=pipeline, estimatorParamMaps=paramGrid, 					evaluator=evaluator, numFolds=5)

We set the cross validator with the already defined estimator, parameter grid, and evaluator with the metric.

- It’s time to fit the CrossValidator on the input data:

	CV_model = crossval.fit(transformed training data from step 1)

The CV_model here has the optimum parameter value after cross validation, so we can use that to transform the test data and predict the outcome from it.

- Recall the transformation that we used on the training data in step 1. We use the same transformation on the test data.

	def transformfunc(data):
		return data.map(lambda r [r[-1],Vectors.dense(r[:-1])]).toDF(['label','features']) 

Let's now transform the test data by using the function transformfunc on the test data and save it as transformed_testdata:**transformed_testdata=transformfunc(test data)**

- We can use the cross validator stored in CV_model above to predict the test data:

	predicted_outcome=CV_model.transform(transformed_testdata)

- We can evaluate the predictions by using the **evaluator** method on the **predicted_outcome**:

	evaluator.evaluate(predicted_outcome)
