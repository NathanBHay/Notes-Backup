The central limit theorem states that for [[Probability#Independence|independent]] and identically distributed random variables the sampling distribution tends towards the normal. Informally for a large sample of observations that don't depend on each other it follows a normal distribution. Formally given a set of randomly distributed variables $Y_1,\dots,Y_n$ with $E[Y_i]=\mu$ and $\text{Var}[Y_i]=\sigma^2$ then: 
$$\sum_{i=1}^nY_i\xrightarrow{d}N(n\mu,n\sigma^2)$$
Where $a\xrightarrow{b}c$ means $a$ converges in distribution to the quantity $b$ in the limit. In other words this means that the sum of many RVs each with a finite mean and variance are approximately normally distributed. 

An implication of the central limit theorem is that for parametric models of a large sample size or with parameters of 1 or greater an approximation using the normal will be accurate. Another implication is that given a sample mean we can find a distribution which approaches $N(\mu,o^2/n)$.
