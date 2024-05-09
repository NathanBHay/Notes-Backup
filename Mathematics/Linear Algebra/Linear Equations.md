Linear equations is the focus on mathematics with regards to equations which produce lines. It is commonly related with [[Linear Algebra|linear algebra]] due to it being used to solve linear equations. Linear equations follow a common rule of:
$$y=mx+c$$
Where $c$ is the constant, and $m$ is the gradient, which is equal to $\frac {rise} {run}$, found usually with the change in distance from the $y$ position on the $x$ position.

# Simultaneous Linear Equations
Simultaneous equations can be used to find the intersection of linear equations. The common methods of doing this are:
- **Elimination** which substitutes an equation's term that has an equation coefficient.
- **Determinants** which uses gaussian elimination.

The result of the intersection of linear equations can be one of three possibilities. These are:
- **Parallel** which means that there is no solution to the intersection.
- **Multiple Solutions** which means that the rules are found to be equal.
- **One Solution** which means that there is a single intersection.

# Distance Formula
The distance formula is used to measure the length of a line on a Euclidian plane. This formula follows the rule:
$$dist = \sqrt{(x_2-x_1)^2+(y_2-y_1)^2}$$

# Midpoint
The midpoint formula finds the middle point of a line. It has the rule:
$$(\frac {x_1+x_2} 2,\frac {y_1+y_2} 2)$$

# Gaussian Elimination
As the amount of variables increase when solving linear equations [[Linear Algebra|linear algebra]] can be used to modify the form of these equations. This is done through either making vectors or matrices. This follows the idea:$$\begin{align}
a_1x+b_1y=c_1\\
a_2x+b_2y=c_2\\
\vdots\;\;\;\;\;\;\;\;\vdots\;\;\;\;\;\;\;\;\;\vdots\\
a_n+b_ny=c_n
\end{align} \Rightarrow x\begin{bmatrix}a_1\\ a_2\\ \vdots\\ a_n\end{bmatrix} + y\begin{bmatrix}b_1\\ b_2\\ \vdots\\ b_n\end{bmatrix} = \begin{bmatrix}c_1\\ c_2\\ \vdots\\ c_n\end{bmatrix} \Rightarrow \begin{bmatrix}a_1 & b_1\\ a_2& b_2\\ \vdots & \vdots\\ a_n& b_n\end{bmatrix} \begin{bmatrix}x\\ y\end{bmatrix}= \begin{bmatrix}c_1\\ c_2\\ \vdots\\ c_n\end{bmatrix}$$Above are three forms of showing linear equations. The first is through equations, the next is through vectors, and the final is through matrices.

The most common way to solve these equations is through **gaussian elimination**. This is a process which attempts to turn the equations, or matrices into a triangular form. From this you are able to easily derive the solution. For example on normal equations we see:$$\begin{align}
a_1x+b_1y+d_1z=c_1 && a_1x+b_1y+d_1z=c_1\\
a_2x+b_2y+d_2z=c_2 && b_2y+d_2z=c_2\\
a_3x+b_3y+d_3z=c_3 && d_3z=c_3
\end{align}
$$This form allows use back-substitution to build up the variables from bottom to top. This process is similarly done on matrices:$$
\begin{bmatrix}
a_1x&b_1y&d_1z\\ a_2x&b_2y&d_2z\\ a_3x&b_3y&d_3z \end{bmatrix} 
= \begin{bmatrix}c_1\\c_2\\c_3\end{bmatrix} \Rightarrow 
\begin{bmatrix} a_1x&b_1y&d_1z\\ 0 & b_2y&d_2z\\ 0&0&d_3z
\end{bmatrix} = \begin{bmatrix}c_1\\c_2\\c_3\end{bmatrix}$$This equation can be seen as trying to find the original vector of $\langle x,y,z \rangle$ that after transformation by the matrices produces a result of $\langle c_1,c_2,c_3 \rangle$. The form of the above matrices is commonly called the **row echelon form**. The variables in the matrices adjacent to the zeroes are commonly called the **pivots**.

## 3-Dimensional Linear Equations
When a line is found within three dimensional space, there are a few basic equations which can be used. To find a rule you either need 2 points on the line, or an [[Linear Algebra|orientation vector]] These are:
$$x(t)=a+pt, \;\;\;y(t)=b+qt,\;\;\;z(t)=c+rt$$
This rule follows the idea of two vectors $(a,b,c)$ and $p,q,r$. Where $t$ is a parameter, that should produce a correct result for all numbers. The rule can also be written as:
$$x(t)=\begin{bmatrix}a\\b\\c\end{bmatrix} +t\begin{bmatrix}p\\q\\r\end{bmatrix}$$
Another equation which can be used follows the rule:
$$\frac{a_1-a_0}{p}=\frac{b_1-b_0}{q}=\frac{c_1-c_0}{r}$$

