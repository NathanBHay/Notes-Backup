Relative primality is a topic within [[Number Theory]] that deals with two integers are **relatively prime**/**coprime** if their only [[Number Theory#Common Divisors|common divisors]] is $1$ which is equivalent to $\text{gcd}(m,n)=1$. A syntax occasionally used for this is that $m\perp n$. A fraction $\frac m n$ is at is lowest terms if and only if $m\perp n$. Therefore, in general a fraction at its lowest terms follows:
$$\frac{m}{\gcd(m,n)}\perp\frac{n}{\gcd(m,n)}$$
Furthermore, a set of integers $n_1, n_2, \dots, n_k$ are **pairwise relatively prime** if when $i \neq j$ then the greatest common divisor is $1$. The relation of relative primes ahs a simple foundation when used with prime exponents because:
$$m\perp n\Longleftrightarrow\min(m_p,n_p)=0\Longleftrightarrow m_p n_p=0 \text{ for all }p$$
Additionally since $\gcd$ is distributive so is relative primality with $k\perp m$ and $k\perp n$ being equivalent to $k\perp mn$.

# Totient
The amount of integers $\{0,1,\dots,m-1\}$ that are relatively prime to $m$ is called the **totient** of $m$ or $\varphi(m)$. The function $\varphi$ is called the **Euler's totient function**. Simply it is the number of integers $k$ in the range $1\leq k\leq m$ for which the GCD $\gcd(m,k)=1$. The integers $k$ are sometimes referred to as being totatives of $m$.

Basic calculation of the function follows the rule that in the case first case $\varphi(1)=1$. For the case where $m$ is a prime power $p^k$ the solution can be found as the multiples of $p$ in $\{0,1,\dots,p^k-1\}$ which are $\{0,p,2p,\dots,p^k-p\}$ hence there are $p^{k-1}$ of them, and $\varphi(p^k)$ counts what is left. Thus:
$$\varphi(p^k)=p^k-p^{k-1}$$
If $m$ is not a prime power then it can be represented with $m=m_1m_2$, where $m_1\perp m_2$. Then the numbers $0\leq n<m$ can be written in a residue number system as $(n\bmod m_1, n\bmod m_2)$. This means:
$$n\perp m \Longleftrightarrow n\bmod m_1\perp m_1 \text{ and }n\bmod m_2\perp m_2$$
Thus, $n$ is only relatively prime to $m$ if both residuals mod $n$ is relatively prime.

Another approach to calculation of the Totient is Euler's product formula. It states:
$$\varphi(n)=n\prod_{p|n}\Big(1-\frac{1}{p}\Big)$$
The last approach is to use a Discrete Fourier Transform to calculate the value. This uses the formula:
$$\varphi(n)=\sum^n_{k=1}\gcd(k,n)\cos\frac{2\pi k}{n}$$

# Euler's Theorem
Euler's theorem is a generalisation of [[Primality#Fermat's Little Theorem|Fermat's little theorem]]. It states that for all integers $m$ through the use of the Euler's Totient function:
$$n^{\varphi(m)}\equiv1\bmod m$$

# Multiplicative Functions
A [[Functions|function]] $f(m)$ is said to be multiplicative if for any positive integer $f(1)=1$ and:
$$f(m_1m_2)=f(m_1)\cdot f(m_2)\quad\text{when }m_1\perp m_2$$
Euler's totient is an example of a multiplicative function. A function is considered completely multiplicative if the condition holds for all integers $m_1$ and $m_2$ even when they aren't coprime.

# Möbius Function
The Möbius function $\mu(n)$ returns values $\{-1,0,1\}$ depending on its prime factorization. Where:
- $\mu(n)=1$ if $n$ is a square-free positive integer with an **even** number of prime factors.
- $\mu(n)=-1$ if $n$ is a square-free positive integer with an **odd** number of prime factors.
- $\mu(n)=0$ if $n$ is a squared prime factor.

A version of this functions which maintains the previous following traits are:
$$\mu(n)=\begin{cases}1&\text{if }n=1\\0&\text{if }a^2|n\text{ for some }a>1\\(-1)^k&\text{if }n\text{ is the product of }k\text{ distinct primes}\end{cases}$$
Alternatively through the use of the [[Functions#Kronecker Delta|Kronecker Delta]] $\delta$, Liouville function $\lambda(n)$, and the product of the [[Primality#Prime Omega Functions|omega functions]] it can be found that: 
$$\mu(n)=\delta_{\omega(n)\Omega(n)}\lambda(n)$$

## Mobius Inversion
The Mobius Inversion principle is a relation between pairs of functions. It finds:
$$g(n)=\sum_{d|n}f(d)\quad\Longleftrightarrow\quad f(n)=\sum_{d|n}\mu(d)\cdot g(\frac{n}{d})$$
