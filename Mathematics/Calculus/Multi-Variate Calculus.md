Multi-Variate Calculus is the subtype of calculus which deals with functions of multiple variables. Thus, due to this use of [[Functions#Multi-Variable Functions|multi-variable functions]] many of the calculus rules bend to fit the new context.

# Multi-Variate Limits
Due to the added complexity of multiple variables the limit definition is changed to be:
$$\lim_{(x,y) \to (x_0,y_0)} f(x,y) = L$$
Where $|f(x,y) - L| < \epsilon$ whenever $0 < \sqrt{(x-x_0)^2+(y-y_0)^2} < \delta$ . The [[Limits#Limit Theorems|limit theorems]] remain the same for all operations with the change of each function being multi-variable.

**Continuity** is redefined as to be continuous at a point if it fulfills the conditions:
- Defined at a given point.
- The limit at the given point exists.
- The limit is equal to the function at that point.

**Composites** have continuity if the interior function is considered continuous and the outer function has a continuous value as the result of the interior function.

The **two path test** states that if a function has two different paths in the domain as the function approaches a certain point, then the limit at that given point doesn't exist.

# Partial Derivatives
A partial derivative is the derivative with respect to one variable, while considering the rest of the values as constants. This is written as:
$$\frac {\partial f} {\partial x} = f_x' = \lim_{h \to 0} \frac {f(x_0 + h, y_0) - f(x_0, y_0)} h$$
To solve a partial derivative you find the derivative of the given variable, you then set all other variables as constants which enables you to find the partial derivative. A second order derivative follows the same process as normal calculus and is written as:
$$\frac {\partial^n f} {\partial x^n} = f_{(n)x}$$
The **mixed derivative theorem** or Clairaut's theorem states that for a function with partial derivatives $f_x,f_y,f_{xy},f_{yx}$ defined throughout an open region $(a,b)$ that is continuous then $f_{xy}=(a,b)= f_{yx}(a,b)$.

A function is **differentiable** at a given point if the derivative with respect to each variable at that given point exists.

# Chain Rule
The chain rule has multiple variants depending on how many variables it has. For **one independent** and **two dependent** we find the rule:
$$\frac {dw} {dt} = \frac {\partial f} {\partial x} \frac {dx} {dt} + \frac {\partial f} {\partial y} \frac {dy} {dt}$$
Where function $w = f(x,y)$ is differentiable at $t$. Commonly the notation for $f$ is replaced with $w$. A general form for **one independent** can be found as:
$$\frac {dw} {dt} = \frac {\partial w} {\partial x_1} \frac {dx_1} {dt} + \frac {\partial w} {\partial x_2} \frac {dx_2} {dt} + \dots + \frac {\partial x_n} {\partial x_n} \frac {dz} {dt}$$
Where $w = f(x_1,x_2,\dots,x_n)$ are differentiable at $t$. For a function with **two independent** and **three intermediate** we find the rules:
$$\begin{align} \frac {\partial w} {\partial t} = \frac {\partial w} {\partial x} \frac {\partial x} {dt} + \frac {\partial w} {\partial y} \frac {\partial y} {\partial t} + \frac {\partial w} {\partial z} \frac {\partial z} {\partial t}\\
\frac {\partial w} {\partial s} = \frac {\partial w} {\partial x} \frac {\partial x} {\partial s} + \frac {\partial w} {\partial y} \frac {\partial y} {\partial s} + \frac {\partial w} {\partial z} \frac {\partial z} {\partial s}
\end{align}$$
Where $w=f(x,y,z), x=g(t,s), y=(t,s) \text{ and, } z=k(t,s)$ 

## Implicit Differentiation
Implicit differentiation is the process of differentiating a multi-variable function without treating any variables as constants. A basic formula for differentiating a function with two independent and one dependent is found as:
$$\frac {dy} {dx} = -\frac {F_x} {F_y}$$
Where $F(x,y)$ is differentiable and equal to 0.

## Vector Gradient
The gradient of a multi-variable function is stored within a vector. This vector is defined though the notation:
$$\nabla f= \begin{bmatrix}\frac {\partial f} {\partial x}\\ \frac {\partial f} {\partial y}\end{bmatrix} = \frac {\partial f} {\partial x} \hat i + \frac {\partial f} {\partial y} \hat j$$
The **directional derivative** is used to measure a functions change you move along a vector. This is defined as:
$$\nabla_{\hat v} f(x) = \lim_{h \to 0}\frac {f(x+h \hat v) - f(x)} h$$
Where $\hat v$ is a unit vector that defines the plane, if 3-dimensional, or the area where the derivative is defined. Another wat to find the directional derivative is through the dot product of the gradient. This can be shown as:
$$\nabla_{\hat v} f(x) = \nabla f \cdot \hat u$$

## Linearization
Linearization is a process used to create a linear function which approximates a function at a point. This process can be defined with the rule:
$$f(x) \approx f(x_0)+ (\nabla f)(x_0)(x-x_0)$$

## Critical Points
Much like the [[Differentiation#Critical Points|critical points]] within standard differentiation multi-variable functions have extrema located at the places where $f_x(a,b)=0,\; f_y(a,b)=0$. Stationary points of inflection have only one derivative with respect to a variable equal to 0. With the addition of more variables we see the creation of **saddle points** which are extrema but only on one plane.

The second derivative test can be used to find all critical points of a multi-variable function. This follows the cases where:
- It has a **local maximum** at $(a,b)$ if $f_{xx} < 0$ and $f_{xx}f_{yy}-f_{xy}^2>0$.
- It has a **local minimum** at $(a,b)$ if $f_{xx} > 0$ and $f_{xx}f_{yy}-f_{xy}^2>0$.
- It has a **saddle point** at $(a,b)$ if $f_{xx}f_{yy}-f_{xy}^2<0$.
- The test is **inconclusive** at $(a,b)$ if $f_{xx}f_{yy}-f_{xy}^2=0$.

## Lagrange Multipliers
Lagrange multipliers are used to find extrema on constrained functions. This constraint is defined as $g(x_1,x_2,\dots,x_n)=c$. Lagrange multipliers therefore create a series of simultaneous equations which are written as:
$$\begin{align}f_{x_1}=\lambda g_{x_1}\\
f_{x_2}=\lambda g_{x_2}\\
\vdots \;\;\;\;\;\;\;\;\;\;\;\;\;\;\vdots\\
f_{x_n}=\lambda g_{x_n}
\end{align}$$
Where $\lambda$ is a scalar multiplier.

## Vector Fields
A vector field is a way of visualizing the instantaneous rate of change of a function. This is done through drawing vectors periodically on a graph at to demonstrate a change in gradient that is seen throughout the graph.

## Jacobian Matrix
A Jacobian matrix is all of the first order derivatives of a [[Functions#Vector Functions|vector-valued multivariable function]]. This can be written as:
$$J= \begin{bmatrix} \frac {\partial f} {\partial x_1} & \dots & \frac {\partial f} {\partial x_1}\end{bmatrix} = \begin{bmatrix} \nabla f_1 \\ \vdots \\ \nabla f_n\end{bmatrix}= \begin{bmatrix} \frac {\partial f_1} {\partial x_1} & \dots & \frac {\partial f} {\partial x_n} \\ \vdots & \ddots & \vdots \\   \frac {\partial f_n} {\partial x_1} & \dots & \frac {\partial f_n} {\partial x_n}\end{bmatrix}$$
When this matrix is square, where the inputs are equal to the amount of outputs the determinant is called the **Jacobian Determinant**.
