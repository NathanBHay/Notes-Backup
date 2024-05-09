Probability filters are a method of recursively updating a prediction using successive measurements of the phenomena. These algorithms have practical applications when dealing with multiple sensors of varying accuracy. This allows all sensors to have a weighted effect on the prediction without discarding any information. This is better than the naive approach of creating an average which doesn't weight values and can't be implemented in an online way.

Filters are based upon control theory which attempts to control dynamic **systems**.  These systems also called *plants* are perceived with a **state observer** where the state is the current value of the system. 
- A **time step** $k$ is the change between discrete time intervals of $\Delta T$.
- The **measurement** $z_k$ is a measured value of the system at a timestep. 
- A **state estimate** $\hat x_k$ is the filter's estimate of the state. A value is *hidden* if it is unable to be measured while it is *observable* if it is able to be measured. 
- A **process model** $v_k$ is a model of the system's change/velocity. It is used to model the system. T
- A process model has **residual error** $r_k$ or process error. If a model has zero error it is considered a **system (plant) model**.

Filtering algorithms operate through first a prediction step called **system propagation** which uses the process model to form a *new state estimate*. The update step called **measurement update** this computes the new estimate between the estimated state and measurement. Both these steps are considered an *epoch*.

# Alpha-Beta Filter
The most basic filter is the $\alpha$-$\beta$ filter which assumes that a system .
This filter is used as the basis of most other filtering algorithms with the varying factor being the alpha and beta values. It 

The *prediction step* has two equations, which first predicts the state and velocity. The estimate of the new state $x_k$ is found through calculating: 
$$\hat x_k\gets \hat x_{k-1}+\Delta T\cdot v_{k-1}$$
The velocity prediction $v_k$ can be calculated through the process model. For a basic model where change is constant (linear) it is calculated as: 
$$v_k\gets v_{k-1}$$
The *state update* refines the state and velocity predictions through the $\alpha$ and $\beta$ terms. This starts with calculation of the residual or **innovation** with: 
$$r_k\gets z_k-\hat x_k$$
To correct the state update find: 
$$\hat x_k\gets\hat x_k+\alpha\cdot r_k$$
The velocity can be corrected by calculating: 
$$v_k\gets v_k+\frac{\beta}{\Delta T}\cdot r_k$$
Choice of an alpha and beta is important for balancing the effectiveness of the algorithm. Larger alpha and beta produces faster responses for new changes, while smaller alpha and beta reduces the level of noise. 

# Kalman Filter
Kalman filters are an expansion upon GH filters that assume measurement error can be represented as a [[Probability Distribution Models#Gaussian (Normal) Distribution|normal distribution]] around the actual value which is the mean. This uses [[Bayesian Statistics|Bayesian]] calculations to predict the variance. The state prediction model is similar to a Alpha-Beta filter with: 
$$\hat x_k\gets \hat x_{k-1}+\Delta T\cdot v_{k-1}$$
Followed by calculation of the velocity: 
$$v_k\gets v_{k-1}$$
In addition to this a **covariance extrapolation** happens to find the predicted joint probability. It is found as: 
$$p^x_{k}=p^x_{k-1}+\Delta T\cdot p^v_{k-1}$$
With the velocities variance found as: 
$$p^v_k=p^v_{k-1}+q_n$$
Where $q_n$ is an optional **process noise variance**. This value is the uncertainty of the dynamic model. The state update phase starts with a calculation of the **Kalman Gain**: 
$$K_k=\frac{p_{k-1}}{p_{k-1}+r_k}$$
This is then followed with the main state update equation which follows: 
$$\hat x_k=\hat x_{k-1}+K_k(z_k-\hat x_{n-1})$$
The **covariance update** changes the covariance between previous measurements. It is calculated as: 
$$p_k=(1-K_k)\cdot p_{k-1}$$

## Non-Linear Kalman Filters
Kalman filters are restricted to linear data of multiple dimensions. For cases where data is non-linear approximation methods need to be used. There are two versions of the filter which achieve this they are:
- **Extended Kalman filters** which use analytic linearization to create a linear rule at the given timestep.
- **Unscented Kalman filters** which uses statistical linearization.
