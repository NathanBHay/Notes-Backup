Automatic Differentiation (AutoDiff) is an algorithmic way of calculating the [[Differentiation|derivative]] of a function on a computer. Historically computers have had issues with computing derivatives, with the common **symbolic method** requiring large lookup tables with derivative rules as to solve problems. To solve this automatic differentiation was proposed. Automatic differentiation works through the division of functions into core components and the use of the chain rule to tie them together. For example:
$$\begin{align}
y&=f(g(h(x)))\\
w_0&=x\\
w_1&=h(w_0)\\
w_2&=g(w_1)\\
w_3&=f(w_2)=y\\
\end{align}$$
These functions are called primitives and can include simple arithmetic operations to complex exponential ones. They can be put into a [[Graph Theory|directed graph]] as to represent the flow of functions. Thus, the chain rule can be applied as:
$$
\frac {dy} {dx} = \frac {dy} {dw_2} \frac {dw_2} {dw_1} \frac {dw_1} {dwx}$$
From this basic concept there are two modes of automatic differentiation **forward-mode** and **reverse-mode**. Where forward is used when there are more outputs than inputs, and reverse used when there are more inputs. Forward mode operates by traversing the chain rule from the inside to the outside. This has the [[Recursion|recursive relation]]:
$$\frac {dw_i} {dx} = \frac {dw_i} {dw_{i-1}} \frac {dw_{i-1}} {dx}$$
This relation solves until the highest $w_n$ resulting in a derivative at any point given as the independent variables. When computing [[Multi-Variate Calculus#Partial Derivatives|partial derivatives]] with respect to a variable multiple operations are required, and can be used to produce a [[Multi-Variate Calculus#Jacobian Matrix|Jacobian matrix]]. **Reverse-mode** works by going outside to inside. It follows the recursive relation:
$$\frac {dy} {dw_i} = \frac {dy} {dw_{i+1}} \frac {dw_{i+1}} {dw_i}$$
With the lowest $w_0$ being the input variables. This works by computing how the previous operation effects the gradient of the output leading to a result of a group of derivatives with respect to each input that form a gradient.
