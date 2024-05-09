Primality is a topic within [[Number Theory]] which handles positive integers that are considered a **prime** number $p$ if its only integer divisors are 1 and itself. Where 1 is not counted as a prime. Adversely numbers that have 3 or more divisors can be considered **composite** as they can be made up of prime factors. All integers are therefore either prime or composite. The **Fundamental Theorem of Arithmetic** states that all integers $>1$ can be represented as a product of primes, called *prime factorisation*. This is written as:
$$n=p_1\cdots p_m=\prod^m_{k=1}p_k, \text{ where }p_1\leq\cdots\leq p_m$$
This ordered form of writing a prime factorisation is unique for all values. Another method of writing the prime factorisation is by assuming there exists a set of infinite primes that can be written in sequence where each prime is to the power of its factorisation value. This can be written as:
$$n=p_1^{n_1}\cdots p_m^{n_m}=\prod^m_{k=1}p^{n_p}, \text{ where each }n_p\geq0$$
This definition depicts primes as a **number system** for positive integers. These numbers have been proved to be infinite.

**Prime number theorem** describes the asymptotic distribution of prime numbers. It formalises the idea that primes become less common as they become larger. The distribution of primes follows:
$$\pi(N)\sim\frac{N}{\ln N}$$
Where $\pi(N)$ is the prime counting function that is number of primes less than or equal to $N$.

# Fermat's Little Theorem
**Fermat's little theorem** states that if $p$ is a prime number, then for any integer $a$, the number $a^p=a$ is an integer multiple of $p$. Mathematically this can be stated as:
$$a^p\equiv a\bmod p$$
A special case of this is if $a$ is not divisible by $p$ then the theorem states $a^{p-1}\%p=1$ or written mathematically is equivalent to:
$$a^{p-1}\equiv 1\bmod p$$

# Square-Free Integers
An integer is considered a square-free integer if its prime factorisation lacks multiple of the same number. This means a number such as $18$ with primes factors $2\cdot3^2$ wouldn't be considered square free. All prime numbers are square free

# Prime Omega Functions
The prime omega [[Functions|functions]] $\omega(m)$ and $\Omega(m)$ count the number of primes factors of a natural number $m$. Little omega $\omega(m)$ counts each **distinct prime factor**, while big omega $\Omega(m)$ counts the **total number** of prime factors. Therefore, for a prime factorisation $m=p_1^{n_1}\cdots p_k^{n_k}$ the little omega can be found as $\omega(m)=k$, and the big omega as $\Omega(m)=\sum n_i$.

# Sequences from Primes
**Mersenne Numbers** are mostly prime numbers found by exponentiation of 2 and a prime, $2^p-1$. Most of these numbers are prime however non-prime instances do exist with the smallest being 11.

**Euclid Numbers** are integers in the form of $E_n=p_n\#+1$ where the $p_n\#$ represents the product of the first $n$ prime numbers. Every Euclid number is congruent to $3\bmod 4$, and $2\bmod 4$ which means no number can be a square. Additionally all numbers have a one as the final number.

**Residue number system** is an application of [[Congruences|congruences]] and primes which states that an integer $x$ is represented by a sequence of residues with respect to moduli that are prime to each other. This means:
$$\text{Res}(X)=(x\bmod m_1,\dots,x\bmod m_r),\text{ if }m_j\perp m_k \text{ for } 1\leq j<k\leq r$$
