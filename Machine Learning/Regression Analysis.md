Regression is a statistical and [[Machine Learning|machine learning]] used to estimate in [[Machine Learning#Supervised Learning|supervised learning]] to find the relationships between dependent and independent variables. There are many differing techniques which can be used to find these statistical rules. Regression operates under the classical assumptions:
- The Sample is representative of the population.
- Variables are measured with no error
- Deviations from the model have a expected value of zero.
- Variance is constant across all observations.
- Residuals are uncorrelated.

Regression models involve unknown components, independent variables, dependent variables, and error terms. These **error terms** are used to find the error of a function which is then optimised as to minimise the functions error. Thus, finding the parameters which are best used within the model leading to it being able to predict values.

The most common branches of regression are [[Linear Regression|linear regression]] and [[Logisitic Regression|logistic regression]], and non-linear regression which all are regression problems which solve different issues.

# Mean-Squared Prediction Error
The mean squared prediction error is a measure of the averaged squared prediction error. It can be written as: 
$$\text{MSPE}(\mathcal{\hat M}(y))=\frac{1}{n'}\sum_{i=1}^{n'}(y_i'-\hat y_i(\mathcal{\hat M}(y)))^2$$
 Where $\hat y_i(\mathcal{\hat M}(y))=\hat y(x_{i,1}',\dots,x_{i,p}',\mathcal{\hat M}(y))$, which is a vector of the model's values and the new values. This therefore, tests how much new data modifies the model. A smaller MSPE means the more accurate the predictions are. The expected MSPE is a metric which can be used to find the bias and variance. This is written as: 
$$\text{EMSPE}=E[\text{MSPE}(\mathcal{\hat M}(y))]=\text{bias}^2+\text{variance}$$

From this we are able to in general say that for simpler models the bias is higher and the variance is lower as the model has less flexibility. For more complex models the opposite is normal as flexibility is required to compute many predictors. Variance will always decrease with increasing training sample size. Variance increases with the number of predictors that are included. Thus model selection is about balancing bias and variance.

# Hypothesis Testing on Regressions
The **multiple testing problem** is a problem associated with hypothesis testing individual regression predictors. This happens due to the p-value being a poor measure as more predictors are added to a model. Commonly called **data dredging** or **p-hacking**. To resolve this the **Bonferroni procedure** can be done. This finds that given a significance level $\alpha$ and $p$ different tests then the Bonferroni procedure should only reject the null hypothesis for each test if: 
$$p\text{-value}<\frac{\alpha}{p}$$
This finds that given a significance level equal over a certain amount of tests if the p-value is less significant. This means that inclusion into the model requires for the p-value to be below the ratio of threshold to tests. The Bonferroni procedure guarantees the probability of including at least one unassociated predictor is $\alpha$.

# Information Criteria
When selecting the appropriate values for a model a common approach would be to use hypothesis testing to find variables with a low  p-value. Maximum likelihood can't be used for selecting a model due to it finding models with more predictors as better. An information criterion finds given a model $\mathcal{M}$, with a minimised negative log-likelihood $L(y|\mathcal{M})$ or equivalently $L(y|\hat\beta_0,\hat\beta,\hat\sigma_{ML}^2,\mathcal{M}
$$ for that model. This is used to find the information criterion for the model as:  $$
L(y|\mathcal{\hat M})+\alpha(n,k_\mathcal{M})$$Where $\alpha(\cdot)$ is the model's complexity penalty, $k_\mathcal{M}$ is the number of predictors and $n$ is the size of the data sample. The complexity penalty can be chosen as:
- **AIC**, Akaike information criterion, which is $\alpha(n,k_\mathcal{M})=k_\mathcal{M}$.
- **BIC**, Bayesian information criterion , which is $\alpha(n,k_\mathcal{M})=k_\mathcal{M}/2\log n$. 
- **KIC**, Kullback-Leibler information criterion, which is $3/2k_\mathcal{M}$.
- **RIC**, risk inflation information criterion, which is $k_\mathcal{M}\log p$.

Where $p$ is the amount of predictors. In general AIC is more prone to overfitting while BIC is less prone to underfitting. RIC can be conservative for large datasets. KIC usually functions the best.

Using the information criterion the [[Algorithmic Paradigms#Greedy|greedy]] **forward selection algorithm** is able to be ran. This algorithm finds the best model by starting with the empty model $\mathcal{M}=\emptyset$, and then iterating through each predictor 1 to $p$ tries to include each remaining predictor in the model, choosing the one that reduces the information criterion score by the largest amount. Therefore, finding the best predictors for any given model $\mathcal{\hat M}^{(i)}$, where $i=1,\dots,p$. Backwards selection is a related algorithm which removes predictors rather than adding.

# Cross-Validation
Cross-validation is a method for controlling model complexity. The basic algorithm for cross validation works by splitting data into training and test sets, fitting a model to the train, computing the MSPE of the model with the test data, and repeating the procedure $m>1$ times. This gives an estimate to how well future data will be predicted. In practice the $m$ value should be as large as possible. CV has two variants these are:
- **K-fold CV** which partitions $K$ into equal sized non-overlapping random partitions and then trains the model on $K-1$ partitions.
- **Leave-one-out CV** works by training on $n-1$ data points and uses remaining data for testing.

# Penalized Regression
Penalized regression is an alternative to using information criteria. Penalized regression functions by adding a penalty function $g(\cdot)$ which finds a $\hat\beta_\lambda$. For linear regression this can be seen as:
$$(\hat\beta_0,\hat\beta_\lambda)=\arg_{\hat\beta_0,\hat\beta}\min\Bigl(\text{RSS}(\hat\beta_0,\hat\beta)+\lambda\sum_{j=1}^pg(\hat\beta_j)\Bigr)$$


Where $\lambda$ is a hyperparameter which defines how strong the penalty is. By varying this value to start off high and go low it allows the model to learn more as the model becomes better. Penalized regression is better than traditional stepwise selection methods as it promotes statistical stability. Which means small changes in the training data don't greatly change the model.

Some common penalized regression methods are:
- Ridge regression which uses $g(\beta_j)=\beta^2_j$. This method is quick to run and produces a very stable estimate. It suffers from one the inability to compute coefficients equal to zero..
- Lasso regression which uses $g(\beta_j)=|\beta_j|$. This method is very stable and efficient.

