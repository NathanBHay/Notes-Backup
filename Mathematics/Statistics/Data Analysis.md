Data analysis is a process within [[Data Science]] that attempts to make accurate predictions from a given dataset. To this end [[Probability|probability]] metrics are used as to create an accurate model that allows for the description of data. A large part of this is **statistical inference** where generated data is used to build a model. This model is based upon three main considerations:
- **Point Estimation** where learning from a model is done through finding parameters that best fit the data.
- **Interval Estimation** where the accuracy of the model is quantified.
- **Hypothesis Testing** where a specific hypothesis is tested to be plausible within a model.

# Types of Data
**Sampling** is the process of getting a subset of the population that is possible to make accurate inferences from. Sampling has many possible errors such as sampling bias and as a result is a delicate process. Sampled data is then subclassified into **quantitative** and **qualitative** data. Four more possible classifications of data which are found within data science are:
- **Categorical-Nominal** data is discrete variables without ordering.
- **Categorical-Ordinal** data is discrete variables with an ordering.
- **Numeric-Discrete** data is numeric data with enumerable amounts.
- **Numeric-Continuous** data is numeric data with real numbers.

# Statistical Inference
# Data Distribution
Data [[Probability Distribution Models|distribution]] is the way data is put across discrete bins. A data set is symmetrically skewed if the mean is the same as the median. It is positively skewed if the mean is greater, and negatively if the median is greater.

**Percentiles** are a value such that all values below that in the sample are lower. The median is considered the 50th-percentile.

# Measures
## Measures of Centrality
Some of these metrics are measures of centrality. The most common of these are:
- **Mean** which is the most common value given an average.
- **Mode** which is the most frequently occurring value.
- **Median** which is the middle value.

## Measures of Spread
Measures of spread note how much the samples differ on average from the typical value. These metrics include:
- **Range** checks the minimum compared to the maximum.
- **Standard Deviation** is the arithmetic mean of the squared deviations from the sample mean.
- **Variance** measures how values vary.

## Variance
**Bias** measures how much a prediction differs from the desired function, sometimes called accuracy. **Variance** measures how much predictions differ from average, this is also called precision.

**Correlation** is a way to measure association between two variables. Correlation can also be found through plotting variables on a scatter plot. The higher the R-value, or the more it looks like a mathematic function, the more correlated the variables. Boxplots can also be used for categorical and numeric data.

## Confusion Matrix
Confusion matrix is used to classify the accuracy of a classification algorithm. It measures the metrics of **True Positives** (TP), **False Negatives** (FN), **False Positives** (FP), **True Negatives** (TN). These can be used to find:
- **Sensitivity** which is $\frac {TP}{TP+FN}$, and measures how often the prediction is correct.
- **Specificity** which is $\frac {TN}{TN+FP}$, and measures when it is actually negative.
- **Precision** which is $\frac {TP}{TP+FP}$, and measures when a positive value is correct.
- **Negative Predictive Value** which is $\frac {TN}{TN+FN}$, and measures negative prediction.
- **Accuracy** which is $\frac {TP+TN}{TP+TN+FP+FN}$, and measures overall correctness.
