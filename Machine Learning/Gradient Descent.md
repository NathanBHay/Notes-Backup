Gradient Descent is an optimisation [[Algorithms|algorithm]] used to find the minimum or maximum of a [[Differentiation|differentiable]] function. It is commonly used within [[Machine Learning|machine learning]] and [[Neural Networks|neural networks]] as to optimise function parameters. Gradient descent works on convex differentiable functions by finding the derivative at any point, and travelling in the opposite direction of the steepest gradient. The amount of travel dependent on the **learning rate**. The fully optimised function is found when the derivative is equal to 0, as it is at a extrema. The gradient descent algorithm follows the iterative definition:
$$a_{n+1}=a_n - \eta \nabla f(a_n)$$
Where $f(a_n)$ is the function to be optimised, $a_n$ is a vector of the parameters, and $\eta$ is the learning rate.

# Gradient Descent Variants
The basic form of gradient descent is commonly called **batch gradient descent** as it operates using a full batch of data. However, as the dataset gets larger it struggles to find a minimum due to the computational complexity. There are two common variants of gradient descent which solves this.
- **Stochastic gradient descent** solves the computational issues by only finding the error over one training example rather than the average of the whole set. This single example is found by using a random heuristic, which decreases computation by a factor of the dataset's size.
- **Mini-batch gradient descent** solves the computational issues by operating on a small batch of random data. This makes it have a larger computational complexity than stochastic however is more accurate.

While these two forms of gradient descent determine the amount of data gradient descent is done on issues still persist in relation to the learning rate. As the learning rate is constant, its value can determine what extrema it finds. As a result a low learning rate can take too long to find an extrema, while a one two big will jump into higher extrema. To fix this further algorithms have been proposed.

# Momentum
Gradient descent with momentum attempts to solve the issues that arise from going down ravines through the use of momentum. Momentum dampens the jumping around gradient descent does when going down ravines. This allows it to get further in fewer iterations. Momentum is done by looking at a previous result as to modify the current outcome. It follows the equation:
$$a_{n+1}= a_n-(\gamma a_{n-1} + \eta \nabla f(a_n))$$
Where $\gamma$ is the momentum value which is restricted by $\gamma \in [0,1]$. This momentum value determines how much the previous iteration will change the outcome of the current iteration.

# Nesterov Momentum
Nesterov Momentum is a variant of momentum which increases the speed of gradient descent momentum by calculating an approximation of the next position of the parameters and finding its gradient. This results in a faster algorithm that requires less iterations to find a minimum. It follows the equation:
$$a_{n+1}= a_n-(\gamma a_{n-1} + \eta \nabla f(a_n-\gamma a_{n-1}))$$
# Adagrad
Adagrad is an algorithm which uses an **adaptive learning rate**. This adaption is based upon the idea that high gradients mean they are closer to an extrema, while lower ones means it is further away.
$$a_{n+1}= a_n - \frac{\eta \nabla f(x)}{\sqrt{F_n+\epsilon}}$$
Where $F_n$ is a diagonalized vector that contains the sum of squares at each iteration. The learning rate $\eta$ is commonly set to $0.01$ as the learning rate is manually tuned anyway. Adagrad's weakness comes from its slowdown which leads to the learning rate being so small it can't find find a higher extrema

# Adadelta
Adadelta is an extension of Adagrad that reduces the decreasing learning rate issue. This is done through a momentum like parameter as well as an adaptive learning rate. It follows the rule:
$$a_{n+1}=a_n - \frac{\nabla f(x) \sqrt{?+\epsilon}}{\sqrt{?+\epsilon}}$$
Equation unfinished.
