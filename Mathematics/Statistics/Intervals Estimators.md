Parameter estimation is the process of estimating the parameters of a [[Probability Distribution Models|probability distribution model]] given some observed data. As opposed to a point estimator which predicts one value $\hat\theta(y)\equiv \hat\theta$ an **interval estimators** gives a range of plausible values in the form $T(Y)=(\hat\theta^-(y),\hat\theta^+(y))$.

# Prediction Intervals
Prediction intervals estimate an interval in which a future observation will fall within a certain probability. 

# Confidence Intervals
Confidence intervals measure the uncertainty of an estimate of a parameter's value based upon samples. 
Formally an interval $T(y)$ is a $100(1-\alpha)\%$ confidence interval for population parameter $\theta$ if and only if:
$$\Pr(\theta\in T(y))=1-\alpha$$
Where $\alpha\in(0,1)$ and the probability is with respect to the population distribution $\Pr(y|\theta)$ over all possible data samples of size $n$.

# Prediction vs Confidence
The main differences between the two are what they focus on with prediction focusing on future events while confidence focuses on past. This means prediction finds an individual number rather than the mean of the confidence. The wider range of prediction intervals make them less certain.
