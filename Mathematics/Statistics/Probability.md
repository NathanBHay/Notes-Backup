Probability is a branch of mathematics based on the chance an event occurs, thus, dealing with randomness mathematically. A **probability space** is defined by two concepts. These being:
- **Sample Space** $S$ which contains all possible outcomes.
- **Probability Function** $\Pr : S \rightarrow [0,1]$ such that the sum of all outcomes is 1.

An **event** a [[Set Theory|subset]] of the **sample space**. This means the probability of an event is the sum of all outcomes of the event. As events are defined on sets all [[Set Theory#Set Operations|set operations]] can be done on them. The sample space is commonly found through the use of [[Counting Methods|counting methods]] to find all possibilities.

Probability can either be over a [[Discrete Probability|discrete]] or continuous function.

The probability of the **unions** between two events has the rule:
$$\Pr(A \cup B) = \Pr(A) + \Pr(B) - \Pr(A \cap B)$$
Some common types of events are:
- **Mutually Exclusive** events are ones that can't occur together. Therefore, the union equals $\Pr(A) + \Pr(B)$.
- **Independent** events are two events such that one doesn't effect the chance of another occurring. This is written as $\Pr(A \cap B) = \Pr(A)\Pr(B)$. This can also be defined as $\Pr(A) = \Pr(A|B)$.

# Conditional Probability
Conditional probability deals with the probability one event happens **given** another occurs. This can be defined as:
$$\Pr(A|B) = \frac {\Pr(A \cap B)} {\Pr(B)}$$
From this we can find the probability of $A$ given $B$. Another way to find the conditional probability is through [[Bayesian Statistics|Bayes' theorem]].

A variable can be **conditionally independent** given $Z$ if for all $x,y,z$:
$$\Pr(x,y|z)=\Pr(x|z)\Pr(y|z)\quad\text{or}\quad\Pr(x|y,z)=\Pr(x|z)$$

# Random Variables
Within probability a random variable (RV) is defined as a function on sample space $\mathbb{R}$. The distribution of a random variable $X$ is described usually as $\Pr(X=x)$, where $x$ is each output within the function. $X$ is sometimes called the **event space**. Random variables are defined as a mapping from the event space $X$ to the sample space $\mathbb{R}$. These distributions satisfy two properties, the first being:
$$\Pr(X=x)\in[0,1]\text{ for all }x\in X$$
In addition to this the distribution of a probability will add up to 1. Formally written as:
$$\sum_{x\in X}\Pr(X=x)=1$$
In addition to this rule, all probabilities selected from two sets can be found as:
$$\Pr(X\in A_1 \cup A_2)=\Pr(X\in A_1)+\Pr(X\in A_1)-\Pr(X\in A_1\cap A_2)$$
## Multiple Random Variables
Multiple random variables can be used to map multiple event spaces onto the sample space. This is called the **joint probability** and can be defined as:
$$\Pr(X=x,Y=y),\quad x\in X,y\in Y$$
The joint probability defines the behaviour of these two random variables. It can be used to find the **marginal probability** which finds the probability of seeing one random variable despite another. It is written as:
$$\Pr(X=x)=\sum_{y\in Y}\Pr(X=x,Y=y)$$

## Independence
For a random variable **independence** can be defined as:
$$\Pr(X=x \land Y = y) = \Pr(X=x)\Pr(Y=y)$$
Random variables can be added together two form new distributions. This process is done working out $\Pr(X=x \land Y = y)$ for independent event and $\Pr(X=x \lor Y = y)$ if the probability is dependent.

Two random variables are **independent and identically distributed** if they are independent and their probability distribution satisfies:
$$\Pr(X_1=x)=\Pr(X_2=x)$$

# Chain Rule
The chain rule, also called the general product rule, within probability allows a joint distribution to be written as an incremental product of conditional distributions. This operates on the simple idea of:
$$\Pr(X\cap Y)=\Pr(Y|X)\Pr(X)$$
This can be scaled up to allow for the writing of many values within a distribution which finds the generalised rule:
$$\Pr(x_1,\dots,x_n)=\prod_{i=1}^n\Pr(x_i|x_1,\dots,x_{i-1})$$

# Quantile Function
The quantile function which is considered the inverse CDF calcualtes the likelihood that a random variable is true in a range from some distribution.

# Expected, Variance & Standard Deviation
The expected value or the mean of the equation is the average value of a probability function. These are calculated differently for [[Continuous Probability#Expected Value|continuous]] and [[Discrete Probability#Expected Value|discrete]] distributions. The variance finds the extent to which values vary. A dataset with a high variance implies a spread of possible values over a larger interval. Similar to mean the variance is calculated in a different way for both distributions, however despite this there still exists a general formula. This is:
$$\sigma^2=\text{Var}[X] = E[(X-\mu)^2]=E[X^2]-E[X]^2$$
This formula is expanded for continuous and discrete variations. The standard deviation calculates the variance in relation to the mean. Standard deviation is the only one to not vary and is calculated as:
$$\text{SD}[X]=\sqrt{\text{Var}[X]}=\sigma=\sqrt{\sigma^2}$$
The **co-variance** of a function is the calculation of the variance between two random variables. This measures the similarity of behaviour between both random variables. Thus, a large covariance indicates that when $X$ deviates positively from $E[X]$ then $Y$ deviates positively from $E[Y]$. This is calculated as:
$$\text{cov}(X,Y)=E[(X-E[Y])\cdot(Y-E[Y])]=E[XY]-E[X]\cdot E[Y]$$
The covariance of a function is between a range of $0\leq |\text{cov}(X,Y)|\leq\max(|Var[X]|,|Var[Y]|)$. Using this metric the **correlation** between multiple variables can be found as:
$$\text{corr}(X,Y)=\frac{\text{cov}(X,Y)}{\text{SD}[X]\text{SD}[Y]}$$
A note on **two independent random variables** is the identify $\text{Var}[X+Y]=\text{Var}[X]+\text{Var}[Y]$ holds. In addition to this the variance between the difference $\text{Var}[X-Y]$ is equal to the above identity. 

## Approximate Expectations
Due to the complexity of calculations for mean and variance approximate estimation functions have been created. For an expected value the approximation assumes that given a probability function $f(x)$ which is twice differentiable and a random variable $X$ that satisfies $E[X]=\mu<\infty$ and $\text{Var}[X]=\sigma^2<\infty$ then the approximation is:
$$E[f(x)]\approx f(\mu)+\Big[\frac{d^2f(x)}{dx^2}\Big|_{x=\mu}\Big]\frac{\sigma^2}{2}$$
For variance the function is similar and can be computed as:
$$\text{Var}[f(x)]\approx\Big[\frac{df(x)}{d}\Big|_{x=\mu}\Big]^2\sigma^2$$
This approximation technique is based upon [[Sequences#Taylor Series|Taylor series expansion]].