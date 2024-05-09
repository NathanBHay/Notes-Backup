Number theory is a branch of mathematics that deals with integers and arithmetic functions. Its primarily concerned with concepts such as divisibility and primality. Number theory has applications within mathematics but also [[Cryptography|cryptography]].

# Divisibility
A **divisor**, and its associated notation follows the basic rule that:
$$a|b\Longleftrightarrow\text{}b = qa$$
Where $a$ divides into $b$ for some [[Datatypes#Integer|integers]] $q$. With the use of a bar to denote that the values divide to produce an integer. Thus its said:
- $a$ is a **divisor** and a **factor** of $b$.
- $b$ is **divisible** and a **multiple** of $a$.

The **division theorem** expands this idea of division and illustrates that a divisor can be made up of the quotient and the remainder $r$. More formally this states that for any integer $a$ and positive integer $b$ there exists unique integers $q$ and $r$ such that $0 \leq r <n$ and $a=qb+r$.

Divisors come in pairs of two numbers. This means that $n=ab$ for $a \leq \sqrt {n}$ or $b \leq \sqrt {n}$ . Thus, to find primes you can iterate through all integers until one of these limits.

# Primes & Relative Primes
[[Primality]] and [[Relative Primality]] are key to much of the study of number theory due to their unique properties in comparison to other numbers. Prime numbers are simply numbers with their only [[Common Divisors|common divisors]] being themselves and one. Relative primality is a related concept where to numbers are considered relatively prime if their only common multiples are one.
