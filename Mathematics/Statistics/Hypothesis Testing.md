Hypothesis testing is a part of the research process where an assumption about a topic is attempted to be proven. Hypothesis testing can be found within [[Scientific Papers|academic research]], or [[Data Science]] for testing of models.

A **null hypothesis** is the method of creating a hypothesis that is proven by a contradiction. It will usually state an idea that is incorrect and attempt to validate its incorrectness through experimentation. Below demonstrates a null hypothesis where both causes are equally likely to cause an event.
$$
\Pr(\text{Effect}|\text{Cause}_0)=\Pr(\text{Effect}|\text{Cause}_1)
$$
The **alternative hypothesis** is the statement that is being validated by the tester who is trying to validate this claim as to prove the null hypothesis incorrect. The alternative hypothesis can be the inverse of the null hypothesis however it could also be a variety of differing hypothesis which answer the question.

# Statistical Tests
Within [[Probability|statistics]] disproving of a hypothesis usually relates to finding the chance a given conclusion is only true by chance. For example to disprove a hypothesis of a model parameter.

## Two Sided Tests
Testing normal distributions with known variance attempts to find the mean of a distribution given a known variance. Thus, the hypothesis follows $H_0:\;\mu=\mu_0$ and $H_A:\;\mu\neq\mu_0$. To answer this we ask is $\mu=\mu_0$ at the population level, and how unlikely would it be to see your estimate of $\hat\mu$ by chance. Therefore, to find the solution one must make use of the sampling distribution $\hat\mu\sim N\Big(\mu_0,\frac{\sigma^2}{n}\Big)$ under the null hypothesis. This is then used 

## One Sided Tests
One sided tests find whether a mean is below a certain value given an unknown and mean. The hypothesis follows a structure of $H_0:\;\mu\leq\mu_0$ and $H_A:\;\mu>\mu_0$.

# P-Values
A p-value is a value that quantifies evidence against a null-hypothesis by testing the chance the data would randomly happen this way. If a p-value is below $0.1$ then it is considered significant, if below $0.05$ even more, and if below $0.01$ it is really significant.
