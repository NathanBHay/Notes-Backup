Integration is the process of finding the area underneath a curve through the use of a function's antiderivative. This is used all throughout mathematics and physics.

# Antiderivative
An antiderivative of a function is the opposite of a [[Differentiation|derivative]]. Where a derivative finds the gradient of a function, an antiderivative would turn that gradient into the original equation. If the antiderivative is considered **indefinite** then a constant is added at the end, denoted with the term $C$. If the derivative is **definite** then $C$ has a value.

# Basic Antiderivative Rules
Anti-Derivatives much like derivatives have a series of rules which enable basic operations to be solved. In cases where $u$ and $v$ are anti-differentiable functions of $x$ these rules are:

| Rule         | Note                                                                               |
| ------------ | ---------------------------------------------------------------------------------- |
| Constant     | $\int ax = ax+C$                                                               |
| Power        | $\int x^n \;dx = \frac{x^{n+1}}{n+1}+C$ |
| Scalar        | $\int ax \;dx = a\int x \;dx$ |
| Sum          | $\int (u+v) \;dx = \int u \;dx + \int v\;dx+C$|
| Natural Expo | $\int (e^x) \;dx = e^x+C$|
| Expo | $\int (a^x) \;dx = \frac{a^x}{\ln (a)}+C$|
| Natural Log | $\int \ln x \;dx = x \ln (x) -x + C$|          |

## Integration by Substitution
If an integral looks difficult one method is to substitute a new function $u=u(x)$ within the function and invert it, as to find $\int f(x)=f(x(u))\frac {dx} {du}\;dx$. If chosen well this new integral will be much easier.

## Integration by Parts
Another method if the integral is difficult is to integrate by parts. To find this rule first choose two functions $u(x)$ and $v(x)$ in your equation, and then follow the rule:
$$\int u(x)v(x)\;dx=u(x) \int v(x)\;dx-\int u'(x)(\int (x)\;dx)\;dx$$
# Integration Approximation
**End Point Approximation** is a method of predicting an integral through the use of rectangles. This follows the basic rule of:
$$\int_a^b f(x)\;dx \approx \frac{b-a}{n}\sum_{x=a}^{n}f(x)$$
Where $a$ is the starting interval, and $b$ is the final interval, with $n$ being the subintervals (distance between squares). This equation has two variants with the **left endpoint** making $n=n-1$ and $x=a-1$, as to make the curve touch the right side of the rectangle. While the **right endpoint** keeps the values the same, with the curve touching the left side of the rectangle. This leads to a difference in either being greater or less than the actual integral.

While this first method offers a useful approximation, the **trapezoidal rule** offers a better approximation due to its use of a shape that contorts better to the curve. It follows the rule:
$$\int_a^b f(x)\;dx \approx \frac{b-a}{2n}\left(  f(a)+f(b)+2\sum_{i=1}^{n-1}f(x_i)\right)$$
