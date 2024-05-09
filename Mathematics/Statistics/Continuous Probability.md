Continuous probability is a branch of [[Probability]] which focuses on a range of values between two numbers. These distributions can be defined as:
$$\Pr(X=x,Y=y)\in[0,1]\text{ for all }x\in X, y\in Y$$
This is called the **joint probability**

# Probability Density Function
A probability density function defines the probability associated over a certain range. This is defined over a continuous range as: 
$$p(x)\geq 0\text{ for all }x\in X\quad\text{ and }\quad\int_xp(x)dx=1$$
# Expected Value
The expected value or mean for a continuous distribution is found given a probability density function. This function is used to find:
$$E[X]=\int_Xxp(x)\;dx$$
# Variance
Variance is calculated as the measure of spread of the values. Its found as:
$$\sigma^2=\int(x-\mu)^2f(x)\;dx$$
# Cumulative Distribution Function
Cumulative distribution function for a continuous sample space is defined as:
$$\Pr(X\leq x)=\int^x_{-\infty}p(x^{'})dx^{'}$$
