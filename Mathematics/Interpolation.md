Interpolation is an estimation method used on a discrete set of points. This creates an approximation of the solution that can be used to predict points across the graph. There are a variety of interpolation methods that can be used as an approximation, these are:
- **Piecewise Constant** interpolation, which assigns a [[Functions#Piecewise Functions|piecewise]] [[Functions|function]] that has a constant value for every function.
- **Linear** interpolation uses a line to connect every point, through piecewise function.
- **Polynomial** interpolation uses a single polynomial to go through all points. In general for $n$ points there exists a polynomial of degree $n-1$ that goes through all data points.
- **Spline** interpolation uses a piece-wise function with low degree polynomials to fit between the points. This makes it easier to find than a polynomial interpolation, but can lead to a decrease in accuracy.

Interpolations while possible to predict a value, suffer from computational complexity issues, due to their difficulty to calculate.

# Cubic Spline Calculations
A cubic spline is similar to a spline however each function within the piece-wise function is a cubic. It has $n-1$ functions within the piece-wise functions, where $n$ is the number of points. This means:
$$\tilde y(x)=\begin{cases}\tilde y_0(x),&x_0\leq x\leq x_1 \\ \tilde y_1(x),&x_1\leq x\leq x_2 \\ \vdots \\ \tilde y_{n-1}(x),&x_{n-1}\leq x\leq x_n\end{cases}$$
Where $\tilde y_n(x)$ is equal to the cubic equation:
$$\tilde y(x)=d_i+a_i(x-x_i)+b_i(x-x_i)^2+c_i(x-x_i)^3$$
Therefore, the goal is to find these coefficients for every equation. Furthermore, some rules have been applied to each equation as to ensure they connect correctly, these are:
- **Interpolation Condition**, where the segment is over the correct interval, $y_i=\tilde y_i(x_i)$.
- **Continuity**, where the data connects on all axis, $\tilde y_{i-1}(x_i)=y_i$.
- **Continuity of first derivative**, where segments have equal rate of change, $\tilde y'_{i-1}=\tilde y'_{i}$.
- **Continuity of second derivative**, where segments are equal in derivative, $\tilde y''_{i-1}=\tilde y''_{i}$.

These conditions also allow easy solutions to the cubic spline. From these conditions we find:
- $d_i=y_i$
- $a_i=\frac{y_{i+1}-y_i}{h_i}-\frac{1}{6} h_i (y''_{i+1}+2y''_i)$
- $b_i=\frac{1}{2}y''_i$
- $c_i=\frac{1}{6h_i}(y''_{i+1}-y''_i)$

Where $h_i$ can be found as $h_i=x_{i+1}-x_i$. All these equations follow a linear system found as:
$$6 \left( \frac{y_{i+1}-y_i}{h_i} - \frac{y_i-y_{i-1}}{h_{i-1}} \right)=h_iy''_{i+1}+2(h_i+h_{i-1})y''_i+h_{i-1}y''_{i-1}$$
For $i=0,\dots,n-1$ where $y''_n=y''_0=0$. From this we have a method of solving a cubic spline through the steps:
1. Solve Linear System
2. Plug into values of $x_i,y_i,y''_i$ to compute the coefficients $a_i,b_i,c_i,d_i$.
3. Use cubic equation to get rules.
4. Assemble cubic spline equation to get the final rule.
