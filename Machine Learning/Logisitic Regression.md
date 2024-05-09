Logistic Regression is a branch of [[Regression Analysis|regression]] used within [[Machine Learning|machine learning]] to [[Classification|classify]] data. Logistic regression is a model which can be used to estimate a deterministic boundary on whether a value is labeled true or false. This model is defined through the **logistic function** which finds a value which can be regressed in a linear regression. This function follows: 
$$\Pr(Y_i=1|x_{i,1},\dots,x_{i,p})=\frac{1}{1+e^{-\eta_i}}$$
Estimating logistic regression can be done by interpreting a Bernoulli model for each predictor. This finds: 
$$\theta_i(\beta_0,\beta)=\frac{1}{1+\exp(-\beta_0-\sum_{j=1}^p\beta_jx_{i,j})}$$
This finds a likelihood of this is found as: 
$$p(y|\beta_0,\beta)=\prod_{i=1}^n\theta_i(\beta_0,\beta)^{y_i}(1-\theta_i(\beta_0,\beta))^{1-y_i}$$

# Assessing Fit
A basic estimation for how good a logistic regression model is to use the decrease in negative log-likelihood over the intercept of the model, $L(y|\hat\beta_0)-L(y|\hat\beta_0,\beta)$. Another approach is to use an information criterion score of the form $L(y|\hat\beta_0,\beta)+k\alpha_n$, where $k$ is the number of predictors and $\alpha_n$ is the penalty term. Standard choices include $1$ for AIC, $3/2$ for KIC, and $1/2\log n$ for BIC. From this a forward selection procedure can be used. The last approach is to use hypothesis testing to find the null hypothesis that $\beta_j=0$.

# Prediction
Once a given model is found future predictions can be done through using the linear predictor: 
$$\hat\eta=\hat\beta_0+\sum_{j=1}^p\hat\beta_jx_j'$$
This can then be used to find: 
$$\Pr(Y'=1|x_1',\dots,x_p')=\frac{1}{1+\exp(-\hat\eta)}$$

