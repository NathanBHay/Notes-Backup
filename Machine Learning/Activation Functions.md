Activation functions within [[Neural Networks|neural networks]] function to squish or limit the sum of all inputs as to produce a useable output. The definition of this function is important as the computational complexity, and the ability to [[Differentiation|differentiate]] this function are important in producing results that can be easily optimised. Furthermore, activation functions are valuable in combating the vanishing gradient problem. There are many common functions, some of which avoid vanishing gradient.

# Step-Function
The step-function is an outdated activation function which was used throughout early neural network development. The function is also called **Heaviside Step-Function** and follows the rule:
$$H(x)=\begin{cases}1 &\text{for } x>0\\0 &\text{for } x\leq 0 \end{cases}$$
This functions main issue is it isn't differentiable. This makes it unable to be optimised through the use of gradient descent.

# Linear
The linear activation function is a simple line whose domain and codomain aren't restricted. These linear activation functions follow the rule:
$$s(x)=x$$
Where $x \in \mathbb{R}$, and the derivative can be found as $s'(x)=1$. This function has many issues, with the gradient having no relation to the input which results in [[Gradient Descent|gradient descent]] only moving in one direction constantly. Furthermore, error within the function effects the output much more than other functions.

# Rectified-Linear
Rectified-Linear function (ReLu) is one of the most used activation functions. Its simplicity allows it to be computationally efficient. Its definition can be written as $R(x)=\max(0,x)$ or as:
$$R(x)=\begin{cases} x &\text{for } x>0\\ 0 &\text{for } x \leq 0\end{cases}$$
The function has a derivative equal to the [[Activation Functions#Step-Function|Heaviside step-function]] which allows it to avoid the vanishing gradient problem at an efficient rate. This function can only be used within the input layer and can lead to dead neurons. These dead neurons can lead to inaccurate outputs as there gradient can't be modified. Due to its range being $[0,\infty]$ it can also explode outputs.

# Leaky Rectified-Linear
Leaky Rectified Linear functions attempt to decrease the amount of dead neurons by adding a parameter $\alpha$ which is commonly defined as $\alpha=0.01$. The activation function follows the rule:
$$R(x)=\begin{cases} x &\text{for } x>0\\ \alpha x &\text{for } x \leq 0\end{cases}$$
This function has a derivative that is defined by the rule:
$$R'(x)=\begin{cases} 1 &\text{for } x>0\\ \alpha &\text{for } x<0\end{cases}$$
This function is considered less computationally efficient than normal ReLu, it still is much better compared to other functions. Similar to ReLu it also isn't as efficient in non-linear functions in classification problems.

# Exponential Linear Unit
Exponential linear unit (ELU) is a function that is similar to ReLu that has a non-linear function below 0. This function follows the rule:
$$E(x)=\begin{cases} x &\text{for } x>0\\ \alpha(e^x -1) &\text{for } x\leq 0\end{cases}$$
This function has the derivative with the definition:
$$E'(x)=\begin{cases} 1 &\text{for } x>0\\ \alpha e^x &\text{for } x<0\end{cases}$$
Since this function is smooth rather than linear it offers accurate results when the input is negative. However, it still lacks the accuracy of other activation functions and is also more computationally expensive.

# Sigmoid
The sigmoid function is common within classification and neural network problems. It produces a value between one and zero. The function is also non-linear, monotonic and has a fixed output range. This function can be written as:
$$S(x)=\frac{1}{1+e^{-x}}$$
This function has a derivative $S'(x)=S(x)\cdot(1-S(x))$. While this function provides accurate results that aren't exploded due to its restricted range it isn't computationally efficient in cases with large amount of inputs. Furthermore, it suffers from the vanishing gradient problem for large inputs.

# Hyperbolic Tangent
The hyperbolic tangent function is a [[Trigonometry#Hyperbolic Function|hyperbolic function]] that has a restricted range between $[-1,1]$. Its similar to sigmoid with the same advantages and disadvantages. This function has the rule:
$$\tanh (x)=\frac{e^x-e^{-x}}{e^x+e^{-x}}$$
This function has a derivative $\tanh' (x) = 1-\tanh(x)^2$. This function has a steeper gradient that the sigmoid function which results in it jumping further during the gradient descent process.

# Softmax
Softmax activation is a function based on probability. It follows the rule:
$$S(x)=\frac{e^{x_i}}{\sum_{j=1}^K e^{x_j}}$$
Where $K$ is the probability of proportional to the exponentials of real numbers. This function is commonly used as the final output function of a neural network.
