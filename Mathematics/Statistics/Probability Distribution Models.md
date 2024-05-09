Probability distributions are an idealized frequency of distribution that describes a specific sample. This allows for a description of randomness through the lens of a establish formula for the distribution. With a probability distribution being a mathematical description of the probabilities of all events over a sample space. Certain predefined models allow for the description of this sample space. They use a [[Continuous Probability#Probability Density Function|probability density function]] to give the function for a value at any given point. The addition of parameters allows the definition of the distribution to be defined respective of the sample space. 

Formally a probability distribution is a function $\Pr(x)$ parametrised with by a value $p\in \Theta$ where theta is the parameter space which holds the equality $\text{dim}(\Theta)<|X|$. The notation $\sim$ is read as 'is distributed as per'.

# Parameter Estimation
Parameter estimation is the process of estimating the values of the parameters for a model. The process requires a variety of statical techniques that are able to estimate the models effectiveness in regard to specific metrics.

# Continuous Models
## Continuous Uniform Distribution
The continuous uniform distribution $X\sim U(a,b)$ finds the distribution of consecutive rational values with equal chance of occurring. It has a distribution which follows:
$$\Pr(x)=\begin{cases}0&\text{ for }x<a\\\frac{1}{b-a}&\text{ for }a\leq x\leq b\\0&\text{ for }x>b\end{cases}$$
The parameter values are restricted to $a,b \in \mathbb{R}\;(a \leq b)$ while the values are taken from a range between $X\in\{a,\dots,b\}$. The mean of the function is $E[X]=\frac{a+b}{2}=a+\frac{w}{2}$. The variance of this function is $\text{Var}=\frac{(b-a)^2}{12}=\frac{w^2}{12}$.

## Gaussian (Normal) Distribution
The Gaussian or normal distribution $X\sim N(\mu,\sigma^2)$ is seen as a standard distribution for continuous values. The distribution has two parameters $\mu$ and $\sigma^2$ which control the mean and variance. Its probability density function is given by: 
$$\Pr(x)=\Big(\frac{1}{2\pi\sigma^2}\Big)^\frac{1}{2}\cdot \exp{\Big(-\frac{(x-\mu)^2}{2\sigma^2}\Big)}$$
This formula is fairly straightforward with the first term being a normalising constant which ensures the equation integrates to one of the required values, and the main component is the second term which notes the probability density of $x\in X$ grows smaller at an exponential rate.

All Gaussian distributions are essentially a translated and scaled version of the **unit normal** $X\sim N(0,1)$. This self-similarity property implies that a given random value can be converted to a arbitrary normal distribution through $Y=\sigma Z+\mu$. Conversely you can convert a distributed random variable to a unit normal deviation by reversing this transformation $Z=(X-\mu)/\sigma$. This is called the **z-score** and a higher one means it has a higher number of standard deviations within a specific limit.

Normal random variables have an additivity quality that allows multiple random variables to be added together. This means given two random variables $X_1\sim N(\mu_1,\sigma^2_1)$ and $X_2\sim N(\mu_2,\sigma^2_2)$ they follow a property:
$$Y_1+Y_2\sim N(\mu_1+\mu_2,\sigma^2_1+\sigma^2_2)$$
## Estimators
Estimators are the methods of finding an estimation of the parameters for a given set of data. The estimators using [[Point Estimators|maximum likelihood]] for the $\mu$ is found as the sample mean: 
$$\hat\mu=\frac{1}{n}\sum^n_{i=1}y_i$$
The estimator for $\sigma$ is found as the sample standard deviation which is: 
$$\hat\sigma=\sqrt{\frac{1}{n}\sum^n_{i=1}(y_i-\hat\mu)^2}$$

# Discrete Distributions
## Discrete Uniform Distribution
Discrete uniform distribution $X\sim U(a,b)$ comes from a set of consecutive integers that have equal chance of occurring. This follows the rule:
$$\Pr(X=k) =\begin{cases}\frac {1} {b-a+1}&\text{if }X\in{a,\dots,b}\\0&\text{otherwise}\end{cases}$$
Where the parameters are $a,b \in \mathbb{Z}\;(a \leq b)$ and $k \in \{a,a+1,\dots,b\}$.
It has an expected value $E[X]= \frac {a+b} 2$ and variance $Var[X] = \frac {(b-a+1)^2-1} {12}$.
![[basicDistribution_ManimCE_v0.15.2.png|400]]
## Bernoulli Distribution
A Bernoulli distribution $X\sim\text{Be}(p)$ is a type where the outcome is restricted to two outputs. These trials follow the rule:
$$\Pr(X=k) = p^x(1-p)^{(1-x)}=\begin{cases}p &\text{for } k = 1\\1-p &\text{for } k = 0\end{cases}$$
Where parameter $p \in [0,1]$ .
These trials have an expected value $E[X]=p$ and variance $Var[X]=p(1-p)$.

## Geometric Distribution
A geometric distribution follows the probability that in a sequence of independent Bernoulli trials, the we see exactly $k$ failures before a success. This has the rule:
$$\Pr(X=k) = p(1-p)^k$$
With the parameter $p \in [0,1]$  and for $k \in \mathbb{N}$. 
It has an expected value $E[X] = \frac {1-p} p$ and variance $Var[X] = \frac {1-p} {p^2}$.

## Binomial Distribution
A binomial distribution $X\sim\text{Bin}(p,n)$ is the probability that given a certain number of $n$ independent Bernoulli trials, we see exactly $k$ successes. This follows the rule:
$$\Pr(X=k) = {n \choose k} p^k (1-p)^{n-k}$$
With the parameters $n \in \mathbb{Z}^+$ and $p \in [0,1]$, and for $k \in \mathbb{N}$.
It has an expected value $E[X] = np$ and a variance $Var[X] = np(1-p)$. 

Binomial distributions have an additive property that allows random variables to be additive in particular ways. Thus, given two binomial distributions $M_1\sim\text{Bin}(p,n_1)$ and $M_2\sim\text{Bin}(p,n_2)$ then: 
$$M_1+M_2\sim\text{Bin}(p,n_1+n_2)$$


## Poisson Distribution
Poisson distribution $X\sim\text{Poi}(\lambda)$ is the probability that $k$ events occur over an average time of $k$ occurring being $\lambda$. This has the rule:
$$\Pr(X=k)=\frac{\lambda^k e^{-\lambda}}{k!}$$
With the parameter $\lambda \in \mathbb{R}^+$. It has an expected value $E[X] = \lambda$ and variance $Var[X] = \lambda$. 

Poisson distributions are have an additive property similar to other distributions. Thus, given two distributions $X_1\sim\text{Poi}(\lambda_1)$ and  $X_2\sim\text{Poi}(\lambda_2)$ then: 
$$X_1+X_2\sim\text{Poi}(\lambda_1+\lambda_2)$$
