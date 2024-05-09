Discrete Probability is [[Probability|probability]] within a context of values over a discrete set. Discrete Probability has its own set of equations for variance etc.

# Probability Mass Function
A probability mass function can be seen as a function that assigns weights to probabilities. It can be formally defined as any function on discrete event space that satisfies:
$$\Pr(x)\geq 0\text{ for all }x\in X\quad\text{ and }\quad\sum_x\Pr(x)=1$$
The advantage of a PMF over other methods is that it can express probabilities over an infinite event space.

# Expected Value
The expected value, or mean is calculated as the weighted average of possible random variables. For a discrete distribution this generates a rule of:
$$E[X] = \sum_{x\in X}{x\Pr(x)}$$
An alternative interpretation of this finds:
$$E[f(X)]=\sum_{x\in X}f(x)\Pr(x)$$
This expected value is is similar to the average of a series of random tests. This series of random tests approaches the expected value. This is called the **law of large numbers** which is written as:
$$ \lim_{n \to \infty}  \frac {1} {n} (X_1+ \dots + X_n) = \mu$$

**Addition** of expected values is done through an addition of expected terms $E[X+Y]=E[X] + E[Y]$. **Scalar Multiplication** is done in a simply as $E[sX] = sE[X]$. Multiplication of random variables 

The expected values of multiple random variables given a joint probability function $f(x,y)$ can be found as: 
$$E_{X,Y}[f(X,Y)]=\sum_{x\in X}\sum_{y\in Y}f(x,y)\Pr(x,y)$$
The subscript $X,Y$ indicates that this is in relation to multiple values. For cases where this isn't the case the calculation can be modified as to ignore the other value. In the case of calculation in relation to one value this means transformations can be done as to remove the $Y$ out of the function $f(X,Y)$. For example the following is equivalent $E_X[XY]=YE_X[X]$. Addition of these values together can also be transformed by $E_{X,Y}[X+Y]=E_X[X]+E_Y[Y]$.

# Variance & Deviation
Variance measures how spread out the distribution of values are. It is found with the rule:
$$\sigma^2=Var[X] = E[(X-\mu)^2]=E[X^2]-E[X]^2=\sum\Pr(x)(x-E[X])^2$$

# Cumulative Distribution Function
Cumulative distribution function for a continuous sample space is defined as:
$$\Pr(X\leq x)=\sum_{-x^{'}\leq x}p(x^{'}),x\in X$$

