Machine learning is a sub-field of computer science which is concerned with the design of [[Algorithms|algorithms]] that can be used to find rules within life. This usually follows the process of gathering data, building a statistical model on the dataset, and using these assumptions colour understanding. This can be considered the learning procedure. A learning procedure being the method in which it learns how to function. (Explainable AI is the idea of AI that isn't just black boxed, but explains how it found a result)

# Types of Machine Learning
Machine learning can be subdivided into multiple different types depending on the type of data that is used. This leads to three main approaches, those being supervised, unsupervised, and [[Reinforcement Learning|reinforcement]].
## Supervised Learning
Supervised learning deals with a dataset of labelled examples. Each of these examples includes **features** or **predictors** which are values that quantify traits. These dependent variables are usually stored within a vector. These **labels** can be a [[Discrete Probability|discrete]] class or a continuous value. **Supervised algorithms** use this data to create a model that if given new data it would be able to label it. If the data is **quantitative** [[Regression Analysis|regression]] techniques are used, while if the data is **qualitative** [[Classification|classification]] techniques are used.

There are multiple techniques for machine learning which include:
- **Linear classifiers**, for representing numerical functions.
- **Parametric**, for representing probabilistic functions. Some examples include [[Bayesian Statistics|Bayes classifiers]].
- **Non-parametric**, for instance-based functions. Models include kernel regression and [[Clustering#K-means|K-nearest]].
- **Non-metric**, for symbolic functions. Tree models such as [[Decision Trees|decision trees]].
- **Aggregation**, which includes models like bagging, Adaboost, random forest.


## Unsupervised Learning
Unsupervised learning deals with a dataset that lacks labels to differentiate the features and traits of the data. As a result the algorithm is designed to find patterns within the data. This can lead to classifications or reduction of unused data to produce better results.

# Overfitting & Underfitting
The most common issue to deal with in machine learning is fitting of the model. Fitting of a model is how accurate a model is in comparison to training data. **Overfitting** happens when the data adheres to the training data too much. Representing features in the training data that aren't present in the real population. This leads to the data not being able to be used practically. This means the data has a high bias. **Underfitting** happens when the data lacks training and has low bias.