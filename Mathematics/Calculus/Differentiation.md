The process of derivation is a method concerned with rate of change, particularly over an instantaneous scenario.

# Rates of Change
A rate of change within mathematics is considered the average rate that a function's value changes over a value. Its is found through the change in one value over the change in another. This is represented as:
$$\frac {\Delta y} {\Delta x} = \frac {y_2 - y_1} {x_2 - x_1}$$
This equations is similar to a basic $\frac {rise} {run}$ equation done to find **gradient** as a gradient is a form of a rate of change. Writing this functionally where $y=f(X)$ can be done as to provide a further rule for rate of change:
$$\frac {\Delta y} {\Delta x} = \frac {f(x_1) - f(x_2)} {x_2 - x_1} = \frac {f(x_1+h) - f(x_1)} {h}$$
Where $h$ is the shift from the original $x_1$ value thus $h \neq 0$. This equation is used practically to find the gradient of the **secant line**. Which is a line that goes through multiple points in another function.

# Derivatives
A derivative is considered an instantaneous rate of change, where the change is measured from a single point. This means that a derivative can be used as the gradient of a **tangent line** to the curve. Where a tangent line is one that only touches the graph once. The derivative can be defined with the use of [[Limits|limits]] as:
$$f'(x)= \lim_{h\to 0} \frac {f(x+h)-f(x)} h$$
**Leibniz** notation is an alternate way of writing a derivative. This notation is defined as the derivative of $y$ with respect to $x$ and is written as:
$$f'(x)= y' = \frac {dy} {dx}$$
The last two types of notation are **Euler** notation which uses $(Dy)(x)$ for a basic derivative. **Newton** notation uses dots above the $y$ term to show a derivative $\dot y$.

A **n-order derivative** is a derivative where you have differentiated it $n$ times. This is written with the notation:
$$f^{(n)}(x) = \frac {d^nf} {d^nx}$$
**Implicit Differentiation** is the process of differentiating an implicit function. An implicit function is one for which the $y$ or $f(x)$ isn't in a form where it's by itself. To solve this you differentiate all variables within the equation, and collect like terms until you find the derivative $y$ with respect to $x$.

**Inverse Differentiation** is done through the rule where $a=f^{-1}(b)$:
$$f^{-1}(x)'(b) = \frac 1 {f'(f^{-1}(b))}$$
**Increasing** and **decreasing** function intervals. If a function is differentiable over an interval, then if $f'(x)>0$ at each point $x \in (a,b)$ then the function is increasing over the interval. Similarly if $f'(x) < 0$ then the function is decreasing. This interval can be found as the critical points within the graph.

**Concavity** is used to find the bend of the graph. If a function is increasing or if $f''(x) > 0$ then it is **concave up**. Adversely if a function is decreasing or if $f''(x)<0$ then it is **concave down**. The point where concavity changes is a **stationary point of inflection**.

# Basic Derivative Rules
Derivatives have a series of rules which enable you to find them easily. In cases where $u$ and $v$ are the differentiable function of $x$ these rules are:

| Rule         | Note                                                                               |
| ------------ | ---------------------------------------------------------------------------------- |
| Constant     | $\frac {d} {dx} (c)$                                                               |
| Power        | $\frac {d} {dx} x^n = nx^{n-1}$                                                    |
| Scalar       | $\frac {d} {dx} (cu) = c \frac {du} {dx}$c                                         |
| Sum          | $\frac {d} {dx} (u+v) = \frac {du} {dx} + \frac {du} {dx}$                         |
| Natural Expo | $\frac {d} {dx} (e^x) = e^x$                                                       |
| Natural Log $u>0$  | $\frac {d} {dx} \ln u = \frac 1 u \frac {du} {dx}$                                                                                   |
| Product      | $\frac {d} {dx} (uv) = v \frac {du} {dx} + u \frac {dv} {dx}$                      |
| Quotient     | $\frac {d} {dx} (\frac u v) = \frac {v \frac {du} {dx} - u \frac {dv} {dx}} {v^2}$ |
| Sine         | $\frac {d} {dx} (\sin x) = \cos x$                                                 |
| Cosine       | $\frac {d} {dx} (\cos x) = -\sin x$                                                |
| Tangent      | $\frac {d} {dx} (\tan x) = \sec^2x$                                                |
| Secant       | $\frac {d} {dx} (\sec x) = \sec x \tan x$                                          |
| Cotangent    | $\frac {d} {dx} (\cot x) =-\csc^2 x$                                               |
| Cosecant     | $\frac {d} {dx} (\csc x) = -\csc x \cot x$                                         |

All other basic functions such as trigonometric inverses can be found through the use of the chain rule.

# Chain Rule
The chain rule finds the derivative of a [[Functions#Composition|composite function]]. It can be written with Lagrange notation as:
$$(f \circ g)'(x) = f'(g(x)) \times g'(x)$$
Or with Leibniz notation as:
$$\frac {dy} {dx} = \frac {dy} {du} \times \frac {du} {dx}$$

# Linearization
Is a process of approximating a function through the use of derivatives. This can be found as the rule:
$$f(x) \approx f(a) + f'(a)(x-a)$$
Where $a$ is any point on the graph of $f(x)$.

# Critical Points
The **extrema** are the **maxima** and **minima**. These are found at points where the $f'(c)=0$. A **critical points** either a extrema or a **point of inflection**. A point of inflection keeps the same positive or negative gradient,. The **absolute extrema** are the local maxima and minima for which the maximum value is given.

The **second derivative test** can be used to find local extrema. It follows the basic rules for all $f'(c)=0$ then:
- It has a **maximum** at $x=c$ if $f''(c) < 0$.
- It has a **minimum** at $x=c$ if $f''(c) > 0$.
- It is unclear what's at $x=c$ if $f''(c) = 0$.

# Mean Value Theorem
**Rolle's Theorem** is a form of the mean value theorem. It states that over an interval $[a,b]$ where $f(a) = f(b)$ there is at least one value where $f'(c) = 0$. This is used to prove the mean value theorem and can be shown graphically as:
![[Pasted image 20220508024042.png|#invert|400]]
The mean value theorem is a sloped version of Rolle's theorem which is used to find the point where the gradient of the secant is the same as the tangent. This can be written with the rule:
$$\frac {f(b)-f(a)} {b-a} = f'(c)$$
The equation can be shown as the equating of the rate of change with the derivative of a point. This can be show graphically as:
![[Pasted image 20220508024217.png|#invert]]
From this theorem we can find that if all the values over the interior of the interval are equal to 0, then the function is a constant. It is also finds that if two functions have equal derivatives over the same interval then there exists a value $C$ that the function is modified by.

**Cauchy's mean value theorem** is a general form of the mean value theorem used on multiple function. It has the rule:
$$\frac {f'(c)} {g'(c)} = \frac {f(b) - f(a)} {g(b) - g(a)}$$

# Newton's Method
Newton's method is an approximation technique to find an intercept point. It is done by first approximating the solution of $f(x) = 0$. Use the first approximation's intercept as the value of the function. This can be continuously done until until the intercept is found.
