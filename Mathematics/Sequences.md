A sequence is similar to a [[Set Theory|set]] however, is ordered and has duplicates. It is usually over an infinite space where the sequence represents an operation done on infinite terms. This space is usually populated with **partial sums** that produce an element. The notation for sequences usually follows:
$$\{x_1, x_2, x_3, \dots, x_{n-1}, x_n\}$$
Many sequences are defined by a rule which is usually recursive. There are many common types of sequences, those being **arithmetic**, **geometric**, **triangular**, **square**, and **cube**. For example an **arithmetic sequence** follows a rule of:
$$a,a+d,a+2d,a+3d\dots =t_{k+1} = t_k + d$$
With an initial value of $t_1=a$. This provides a sequence of numbers which increase by a defined amount. A **geometric sequence** follows a similar rule where the value is multiplied. This rule is expressed as:
$$a,ar,ar^2,ar^3,\dots=t_{k+1} = rt_k$$
The **order** of a recurrence relation is given by the difference between highest and lowest subscripts. Thus the order is dependent on how far back you call a function.

# Summations
Summations are a notation of sequences used to represent the addition of multiple terms. This follows a syntax where the sigma symbol is used with a upper limit $n$, and a initial value $i=m$.
$$\sum^n_{i=m}a_i=a_i+a_{i+1}+\cdots+a_n$$
Summations can be manipulated through a variety of mathematical laws that relate. These laws include:
- **Distributivity** where constants can be moved out of the sum, $\sum ca_k= c\sum a_k$.
- **Associativity** where grouping can be changed $\sum(a_k+b_k)= \sum a_k+\sum b_k$.
- **Commutative** where terms can be reordered, $\sum_{k \in K} a_k=\sum_{p(k) \in K} a_{p(k)}$.

# Convergence & Divergence
A sequence can converge at a value to produce a result. This happens when for every positive integer there is a value such that the convergence point is bigger.
$$\lim_{n\to \infty}a_n=L$$
Where $a_n$ is the sequence which converges on a value $L$. The opposite of this process is a **divergence** where the limit becomes infinity as time goes on. This can be represented as:
$$\lim_{n \to \infty}a_n=\infty$$
Some common convergences include:
- $\lim_\frac {\ln n} n=0$
- $\lim x^{1/n}=1$ for $x>0$
- $\lim (1+\frac x n)^n=e^x$
- $\lim \sqrt[n]{n}=1$
- $\lim x^n = 0$ for $|x| < 1$
- $\lim \frac {x^n} {n!}=0$

If a series $\sum a_n$ converges then $a_n \to 0$. If two series are convergent they can be combined as to produce a new result. These can be added or subtracted to produce a convergence equal to the addition. Similarly they can be multiplied by a constant.

The **integral test** can be used to test if a sequence converges or diverges. This is done through integrating the partial sum given the series is of positive terms and the sum is decreasing and continuous.

If for sequences $a_n \leq b_n$ where $b_n$ converges then $a_n$ converges. If for sequences $b_n \leq a_n$ where $b_n$ diverges then $a_n$ diverges.

**Limit Comparison Test** uses the limits of sequences to find convergence. This follows three rules:
- If $\lim \frac {a_n} {b_n} > 0$ then both converge of diverge.
- If $\lim \frac {a_n} {b_n} = 0$ then $b_n$ converges and $a_n$ diverges.
- If $\lim \frac {a_n} {b_n} < 0$ then $a_n$ converges and $b_n$ diverges.

# Bounded Monotonic Sequences
A sequence is **bounded from above** if there exists a value such that all values in the sequence are less than or equal to. This number is the **upper bound** and can be considered a least upper bound if no value is less than the upper bound. A sequence is **bounded from below** if there exists a value such that all values in the sequence are greater than or equal to it. This number is the **lower bound** and has a greatest lower bound if no value is greater than it. If neither of these facts are true it is **unbounded**.

A sequence is **non-decreasing** if for every value $a_n \leq a_{n+1}$. Adversely the sequence is **non-increasing** if $a_n \geq a_{n+1}$. The sequence is **monotonic** it is neither decreasing or increasing. If a sequence is bounded and monotonic then the sequence converges. A series of non-negative terms also converge if the partial sums are bounded from above.

# Absolute Convergence
A series converges absolutely if the absolute partial sum converges, which also means that the non-absolute partial sum converges. These series can be rearranged and still produce the same result. To find absolute convergence the rule is:
$$\lim_{n\to\infty}|\frac {a_{n+1}} {a_n}| = \rho$$
This series converges absolutely if $\rho < 1$, it diverges if $\rho > 1$ or is infinite, and the test is inconclusive if $\rho = 1$. Another test is the root test which follows:
$$\lim_{n\to\infty} \sqrt[n]{|a_n|} = \rho$$
This series allows the same rules as the one above. The **alternating series test** also finds absolute convergence given it follows:
$$\sum_{n=1}^n (-1)^{n+1}u_n=u_1-u_2+u_3-u_4+\dots$$
This series converges if all $u$'s are positive, if the values are non-increasing, and if $u_n=0$.

# Power Series
A power series is a series which centers around a value $n$ which takes the form:
$$\sum_{n=0}^\infty c_nx^n = c_0 + c_1(x-a) + c_2(x-a)^2 + \dots + c_n(x-a)^n$$
If a power series converges at a value then it will converge absolutely if the term is less than the convergence value. If a series diverges then it diverges for all terms that are greater than the divergence value. Two power series can be multiplied to create a series that converges absolutely. Similarly for any function to the power of $n$ they converge absolutely. Power series can be [[Differentiation|differentiated]] and [[Integration|integrated]] at every term independently.

# Taylor Series
A Taylor series is a series which centers around a value $a$ which takes the form:
$$\sum_{n=0}^\infty \frac {f^{(n)}(a)} {n!} (x-a)^n = f(a) +f'(a)(x-a) + \frac {f''(a)} {2!} (x-a)^2 + \dots + \frac {f^{(n)}(a)} {n!} (x-a)^n$$
A **Maclaurin Series** is a Taylor series where $a=0$. A Taylor series can be linearized as to produce an approximation for higher order polynomials. These polynomial approximations are called **Taylor Polynomials**. This can be generated by the rule:
$$P_n(x) = f(a) +f'(a)(x-a) + \dots + \frac {f^{(n)}(a)} {n!} (x-a)^n + \frac {f^{(n+1)}(a)} {(n+1)!} (x-a)^{n+1}$$
These polynomials are generated until point $n$ with the final $n+1$ term being the remainder term. A remainder term can be estimated if there is a constant term $M$ that is greater than the function differentiated $n+1$ times. This can be written as:
$$|R_n(x)| \leq M \frac {|x-a|^{n+1}} {(n+1)!}$$
If this inequality holds for all $n$ then the series converges to $f(x)$. Some frequently used Taylor series include:
- $\frac 1 {1-x} = \sum x^n$
- $\frac 1 {1+x} = \sum (-1)^nx^n$
- $e^x= \sum \frac {x^n} {n!}$
- $\sin x = \sum \frac {(-1)^nx^{2n+1}} {(2n+1)!}$
- $\cos x = \sum \frac {(-1)^nx^{2n}} {(2n)!}$
- $\ln x = \sum \frac {(-1)^{n-1}x^n} n$
- $\tan^{-1} x = \sum \frac {(-1)^nx^{2n+1}} {2n+1}$

As seen [[Trigonometry|trigonometric]] functions, as well as exponential functions are commonly simplified through the use of Taylor polynomials.
