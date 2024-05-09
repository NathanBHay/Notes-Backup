 **Linear equations** are the focus on mathematics with regards to equations which produce lines. It is commonly related with [[Linear Algebra|linear algebra]] due to it being used to solve linear equations. Linear equations follow a common rule of:
$$y=mx+c$$
Where $c$ is the constant, and $m$ is the gradient, which is equal to $\frac {rise} {run}$, found usually with the change in distance from the $y$ position on the $x$ position. These equations can also be represented within vector form for equations of higher dimensions.
$$\begin{align}
a_{1,1}x_1+\cdots+a_{1,n}x_n=b_1\\
\vdots\mspace{50mu}\vdots\mspace{50mu}\vdots\mspace{50mu}\\
a_{n,1}x_1+\cdots+a_{n,n}x_n=b_n\\
\end{align} \Rightarrow \begin{bmatrix}a_{1,1} & \cdots & a_{1,n}\\ \vdots & \ddots & \vdots\\ a_{n,1} & \cdots & b_{n,n}\end{bmatrix} \begin{bmatrix}x_1\\\vdots\\ x_n \end{bmatrix}= \begin{bmatrix}b_1\\ \vdots\\ b_n\end{bmatrix}$$
**Linear systems** (also called simultaneous equations) are a series of linear equations usually used to [[Modelling|model]] a system where linear operations occur. When modelling these systems we can use these multiple rules in vector form to find: 
$$A\vec{x}=\vec{b}$$
Where $A$ is the matrix representing the set of linear equations, and $\vec{b}$ represents a possible solution. A *solution* to a linear equation is the intersection between all the vectors within the equation. A solution can take three possible forms:
- **Parallel** which means that there is *no solution* to the intersection, and $A$ singular and $b\in span(A)$.
- **Infinite Solutions** which means that the rules are found to be equal, and $A$ is singular and $b\notin span(A)$.
- **One Solution** which means that there is a *solution* and the system is non-singular.

Where a square matrix $A$ is considered non-singular if either $A^{-1}$ exists or $\text{det}(A)\neq0$. Finding solutions to linear systems can be done through two types of approaches:
- **Exact methods**, such as [[Linear Systems#Gaussian Elimination|Gaussian elimination]], find the exact solution usually through extensive calculations.
- **Iterative solutions** find solutions by generating candidate solutions multiple times until a good result is found. This is good in cases where finding a solution is too complicated.

# Gaussian Elimination
The most common way to solving linear equations is through Gaussian elimination. This is a process which attempts to turn the equations, or matrices into a triangular form. From this you are able to easily derive the solution. For example on normal equations we see:
$$\begin{align}
a_1x+b_1y+d_1z=c_1 && a_1x+b_1y+d_1z=c_1\\
a_2x+b_2y+d_2z=c_2 && b_2y+d_2z=c_2\\
a_3x+b_3y+d_3z=c_3 && d_3z=c_3
\end{align}$$
This form allows use back-substitution to build up the variables from bottom to top. This process is similarly done on matrices:
$$\begin{bmatrix}
a_1x&b_1y&d_1z\\ a_2x&b_2y&d_2z\\ a_3x&b_3y&d_3z \end{bmatrix} 
= \begin{bmatrix}c_1\\c_2\\c_3\end{bmatrix} \Rightarrow 
\begin{bmatrix} a_1x&b_1y&d_1z\\ 0 & b_2y&d_2z\\ 0&0&d_3z
\end{bmatrix} = \begin{bmatrix}c_1\\c_2\\c_3\end{bmatrix}$$
This equation can be seen as trying to find the original vector of $\langle x,y,z \rangle$ that after transformation by the matrices produces a result of $\langle c_1,c_2,c_3 \rangle$. The form of the above matrices is commonly called the **row echelon form**. The variables in the matrices adjacent to the zeroes are commonly called the **pivots**.  

Algorithmically to use back substitution can be computed for a matrix $U$ of dimensions $n\times n$ as: 
$$x_n=\frac{z_n}{u_{n,n}}\mspace{50mu}x_i=\frac{1}{u_{i,i}}\Big(z_i-\sum_{j=i+1}^nu_{i,j}x_j\Big)$$
Where $i\in[n-1,1]$, $z$ is the result vector, and $u$ is an upper vector. 

## 3-Dimensional Linear Equations
When a line is found within three dimensional space, there are a few basic equations which can be used. To find a rule you either need 2 points on the line, or an [[Linear Algebra|orientation vector]] These are:
$$x(t)=a+pt, \;\;\;y(t)=b+qt,\;\;\;z(t)=c+rt$$
This rule follows the idea of two vectors $(a,b,c)$ and $p,q,r$. Where $t$ is a parameter, that should produce a correct result for all numbers. The rule can also be written as:
$$x(t)=\begin{bmatrix}a\\b\\c\end{bmatrix} +t\begin{bmatrix}p\\q\\r\end{bmatrix}$$
Another equation which can be used follows the rule:
$$\frac{a_1-a_0}{p}=\frac{b_1-b_0}{q}=\frac{c_1-c_0}{r}$$
