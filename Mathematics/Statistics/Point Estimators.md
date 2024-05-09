Parameter estimation is the process of estimating the parameters of a [[Probability Distribution Models|probability distribution model]] given some observed data. A **point estimator** in particular predicts a single concrete value which the parameter should be $\hat\theta(y)\equiv \hat\theta$.
# Bias
The bias of an estimator measures the degree to which an estimator under or over-estimates the value. Thus, given a sample from the population $Y=(Y_1,\dots,Y_n)$ and an estimator $\hat\theta(Y)$ which estimates a parameter $\theta$ from the sample $Y$, let the bias be defined as:
$$b_\theta(\hat\theta)=E[\hat\theta(Y)]-\theta$$
Where the expectation is taken with respect to the population distribution of the sample $E[\hat\theta(Y)]=\int_{\hat\theta}\hat\theta\Pr(\hat\theta)\;d\hat\theta$. Where $\Pr(\hat\theta)$ is the sampling distribution of $\hat\theta$ and $\Pr(y_1,\dots,y_n|\theta)$ is the population distribution of the data. If $b_\theta(\hat\theta)<0$ then the estimator tends to underestimate, and vias versa

Another metric is **estimator variance**. This estimates on average how much the expected parameter estimates vary. The greater the variance the more variation  It finds the variance of an estimator $\hat\theta$ is given by:
$$\text{Var}_\theta(\hat\theta)=E\Big[\big(\hat\theta(Y)-E\big[\hat\theta(Y)\big]\big)^2\Big]=V\big[\hat\theta(Y)\big]$$
The **mean-squared error** of an estimator is another metric which measures how close on average the estimator is to a population parameter. This standard measures find the MSE of an estimator $\hat\theta$ of a population parameter $\theta$. This follows: 
$$MSE_\theta(\hat\theta)=E\Bigl[(\hat\theta(Y)-\theta)^2\Bigr]$$
A useful property of MSE is the fact that is can also be calculated through the **bias-variance decomposition** as: 
$$\text{MSE}_\theta(\hat\theta)=b_\theta(\hat\theta)+\text{Var}_\theta(\hat\theta)$$
An estimator is considered **consistent** if $b_\theta(\hat\theta)\to0$ and $\text{Var}_\theta(\hat\theta)\to0$ as $n\to\infty$ for all $\theta$.

# Maximum Likelihood
The main idea behind maximum likelihood is the likelihood function which finds the joint probability of $x_1,\dots,x_n$ if the model's parameters were $\theta$. This means the best model will have the largest likelihood of all data being similar to the model. Formally this means that given a parametric model $p(x|\theta)$ with unknown parameters $\theta=(\theta_1,\dots,\theta_p)$ and observed data $x=(x_1,\dots,x_n)$ the likelihood will be given by:
$$\hat\theta_{\text{ML}}(x)=\arg_\theta\max\{p(y|\theta)\}$$
Often this model is solved in an alternative minimisation context where given a function $L(y|\theta)=-\log(p(y|\theta))$ find the minimum of:
$$\hat\theta_{\text{ML}}(x)=\arg_\theta\min\{L(y|\theta)\}$$
This method of finding a solution is called the **negative log-likelihood** and is often easier to solve. The solving process follows differentiating the negative log-likelihood with respect to the model parameters and then solving for those values of the parameters that set the derivative to zero.

## Independent Data
The process of solving maximum likelihood for independent and identically distributed random variables is more simple than traditional methods. This finds a joint probability function of: 
$$p(y|\theta)=\prod^n_{i=1}p(y_i|\theta)$$
This can then simplify the negative-log likelihood as: 
$$L(y|\theta)=-\sum^n_{i=1}\log(p(y_i|\theta))$$

# Unbiased Estimator of Variance
The unbiased estimator for variance is another estimator technique which estimates the variance of a given model. This is found through the equation:
$$\hat\sigma^2_U=\Big(\frac{1}{n-1}\Big)\sum^n_{i=1}(y_i-\hat\mu)^2$$
