*Classification* is a type of [[Machine Learning|machine learning]] problem which deals with the determining of a bit of data's label given a previous set of classified data. Statistically this can be defined as the categorization of sub-populations. Classification is done through a **classifier** which is an [[Algorithms|algorithm]] that implements mathematic function to correctly categorize data. These algorithms can either be deterministic or probabilistic, with deterministic algorithms being preferred. Classification is commonly done through [[Logisitic Regression|logistic regression]], [[Bayesian Statistics|Bayesian classifiers]], and more.

Classification can be sub-divided into two separate problems, those being binary and multiclass. **Binary classification** deals with decisions which are restricted to a [[Number Systems#Binary|binary]] range. **Multiclass classification** deals with problems which aren't restricted by two decisions but rather many more. Multiclass classification is usually done through the combination of binary classifier algorithms.

# Assessing Classifiers
Classifiers can be accessed through a variety of different metrics.

## Classification Accuracy
Classification accuracy is a measure of performance which is defined as:
$$\text{CA}=\frac{1}{n'}\sum_{i=1}^{n'}I(y_i'=\hat y'_i)$$Where $I(\cdot)$ is the indicator function that returns a one if the condition inside the parenthesis is meta, and zero otherwise. This metric can be expanded to a confusion matrix. This creates a table of which split true negatives (TN), false negatives (FN), false positives (FP), and true positives (TP). This can then find the **sensitivity**, or the true positive rate as: $$\text{TPR}=\frac{\text{TP}}{\text{TP}+\text{FN}}$$And the **specificity** or true negative rate as: $$\text{TPR}=\frac{\text{TN}}{\text{TN}+\text{FP}}$$
## Area-under-the-curve
The area-under-the-curve is found by constructing a graph of $\Pr(Y_i'=1|\dots)\geq T$ for all $T$. After this the area-under-the-curve can be found between $0$ and $1$. With $0.5$ being the case that the prediction is no better than a coin flip.

# Logarithmic Loss
Logarithmic loss computes for each sample $i$ in the group as: 
$$L(y_i')=\begin{cases}-\log\Pr(Y_i'=1|x_{i,1}',\dots,x_{i,p}'&\text{for }y_i'=1\\-\log\Pr(Y_i'=0|x_{i,1}',\dots,x_{i,p}'&\text{for }y_i'=0\end{cases}$$
With this metric the smaller the score the better the classifier predicts this data. This predicts how well the model predicts the probabilities of an individual being in a class (calibration).