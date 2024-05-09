A function is a series of inputs that return a unique output. These inputs are considered the **domain** and the possible outputs as the **codomain**. All functions are considered a form of [[Relations|relation]]. The common notation is written as:
$$f : \text{domain} \rightarrow \text{codomain}$$
The **image** is the actual outputs of the function given the domain. If the image is the same as the codomain then the function is **onto**. Furthermore, a function can be **one-to-one** if for each input there is only one output. A **sequence** is a form of a function.

A **Characteristic Function** is one which returns a common characteristics between two inputs. Much of the [[Propositional Logic]] symbols can be considered characteristic functions.

# Composition
Functions can build upon other functions to form compositions. These are written as:
$$f \circ g \text{ or } f(g(x))$$
A composition can only exist if the **codomain** of the inside function is the same as the **domain** of the outside function. This could be written as:
$$\begin{align}
h:A \rightarrow B \text{ \& } g:C \rightarrow D \\
\text{then } h \circ g: A \rightarrow D \text{ if } b=c
\end{align}$$
# Basic Functions
## Identity Function
The identity function is a function that does nothing. Its purpose is used for notation within inversion and other functions. It can be written as:
$$\iota_A (x) = x$$
## Kronecker Delta
The Kronecker Delta function is a simple function that returns a [[Datatypes#Boolean|Boolean]] if two values are equal.
$$\delta_{ij}=\begin{cases}0&\text{if }i\neq j\\1&\text{if }i=j\end{cases}$$
# Inversion
An inverse function is one where the **domain** and **codomain** pairs are switched. Formally is can be defined as:
$$f \circ g = g \circ f = \iota_A$$
Inversion requires a function that is **one-to-one** and **onto**. An inverse can be written as:
$$f:A \rightarrow B \;\;\;\; f^{-1} : B \rightarrow A$$
# Piecewise Functions
A piecewise function is one which has multiple rules across different intervals. This is usually written as a single function which has
$$f(x)=\begin{cases}g(x) &\text{for }(\infty,a)\\
\vdots\\
p(x) &\text{for }(b,\infty)\\
\end{cases}$$
These functions can have an infinite number of **cases** that defines rules for different intervals.

## Multi-Variable Functions
A multi-variable function is one which assigns multiple variables within the function definition. These are commonly found in three-dimensional functions. All functions are made up of two types of variables dependent and independent. **Dependent variables** are the ones that depend on the **independent variables**, commonly this is pictures as $z$ depending on the pair of $(x,y)$ for two variable functions.

The **domain** of functions with more than one variables usually excludes inputs that lead to complex numbers or division by zero. The **range** follows the usual conventions, with it being the set of outputs provided by the dependent variables.

**Sketching** multivariable functions can be done by either drawing the surface in three dimensional space, or labeling the curves that have a constant values. The places where a function has constant values is called the **level curve**.

## Parametric Functions
A parametric function defines on a set of multiple independent variables called **parameters**. These parameters are given their own functions as opposed to a single one. From this we see the rule:
$$(x_1,x_2,\dots, x_n)=(f_1(t),f_2(t),\dots, f_n(t))$$
To convert a parametric function to an **implicit function**, these being the latter functions, one does a process of implicitization. **Implicitization** is done through eliminating the $t$ variable in a set of equations generated through an input variable being equated to the function.

A parametric function is differentiable if at all parameters it is differentiable. 

## Vector Functions
Functions can be interpreted as a set of inputs which are modified to produce a range represented by a vector. Functions that explicitly state this are vector-valued functions. This is as opposed to normal functions which are **scalar functions**. A vector function is differentiable if all values within the domain are differentiable. These vector functions also share the same [[Differentiation#Basic Derivative Rules|differentiation rule]]. 
