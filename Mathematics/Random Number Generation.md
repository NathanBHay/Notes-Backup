Random number generation is the process of creating a number which lacks a pattern outside of its initial constraints. The process of random number generation is important due to it being an effective metaheuristic, that can be used to solve problems. Random numbers are are studied within the [[Probability]] field as to attempt to predict series of random events. The generation of random numbers has become an important problem after the advent of computers due to the need for random numbers but the inability for computers to generate them. This has resulted in a set of **pseudo-random number generation algorithms**. These algorithms take a **seed value** which is then used to generate a set of numbers, in a deterministic fashion. Later algorithms even use seed values from nature as to further simulate randomness. These approaches also have fault due to the possibility of randomness not existing.

Pseudo-random number generators have a many possible flaws due to their deterministic nature. To quantify how good an algorithm is the following properties must be studied:
- The existence of seeds which produce less random, or short sequences of numbers.
- Lack of uniform distributions for large sequences of numbers.
- Correlation between successive values.
- Poor dimensional distribution of output sequence.

In general the generation of random numbers can either be done by basic generation algorithms that rely on basic mathematical techniques, or algorithms based upon [[Cryptography|cryptographic]] techniques that result in increased security. While basic algorithms lack security for many uses they prove less intensive to implement.

# Linear Congruential Generators
Linear congruential generators are one of the oldest and most common pseudo-random number generators. These algorithm are useful as they are one of the fastest generators due to their use of modulo arithmetic. Despite this advantage they are commonly discredited due to their lack of security, especially under constraints. The linear congruential generator follow a mathematical function that can be calculated as a discontinuous [[Functions#Piecewise Functions|piecewise]] linear function. This function can also be represented by the [[Recursion|recurrence relation]]:
$$
X_{n+1}=(aX_n+c) \bmod m
$$
Where $0<m$ is the modulus, $0<a<m$ is the multiplier, $0 \leq c < m$, is the increment, and $0\leq X_0 <m$ is the seed value. It is common for many cases of this equation to have a $c=0$ condition, which is called a **multiplicative congruential generator** or **Lehmer generator**.

The large flaw of generation by this method is that the $a$, $c$, and $m$ values result in a heavy difference in quality of random number generation. To resolve this issue there are three common approaches that are used when picking these numbers:
- **Prime** $m$ and $c=0$, is a common approach and was the original Lehmer generator. This approach suffers from the product being needed to be stored in a [[Datatypes#Float|double]] which results in more steps during calculation. Additionally it also is awkward to convert a starting value into bits.
- **Power of 2** $m$ and $c=0$, is a faster approach than using a prime due to the modulo operation being able to simplify by discarding the second half. This results in faster computation however does suffer from the issue of a small period. This issue becomes more apparent as only the most significant bit increases the period of the generator.

The last approach to picking good numbers is the case when $c\neq 0$. When this is the case the Hull-Dobell theorem can be used to find a set of values that maximise the period. It follows the rule that the period of $m$ can only be achieved if and only if:
1. $m$ and $c$ are relatively prime.
2. $a-1$ is divisible by all prime factors of $m$.
3. $a-1$ is divisible by $4$ if $m$ is divisible by $4$

Linear Congruential Generators are one of the most common random number generators, and are the basis of many future algorithm. Algorithm that are within the same family usually attempt to optimize the algorithm's ability to function on computers.

# Mersenne Twister
The Mersenne Twister is one of the most common pseudo-random number generators within software. Based upon the linear-feedback shift register design the Mersenne Twister has the distinct advantage that it has a period equal to $2^{19937}-1$ and $623$-dimensional equal distribution up to 32-bit accuracy. The Mersenne Twister uses word vectors denoted by $x$ and $a$ which are $w$-dimensional row vectors equal to either 0 or 1. These are then used in the linear recurrence relation:
$$
x_{k+n}=x_{k+n} \oplus (x_k^u | x^l_{k+1})A
$$
Where $k,n,r,n\in\mathbb{Z}$, $k$ is the recurrence step, $n$ is the degree of recurrence, $r$ which is hidden in the definition $x^u_k$ is between $0\leq r \leq w-1$, $m$ is between $1\leq m \leq n$, and a constant $w\times w$ matrix $A$ with entries. The generator uses an initial seed given by $x_0, x_1, \dots ,x_{n-1}$ and then using a set of recurrent numbers $k=0,1,\dots$ to find $x_{n+1},x_{n+2}, \dots$ resulting in a random series. The term $x_k^u | x^l_{k+1}$ can be seen as a concatenation of the upper $w-r$ bits of $x_k$ and the lower $r$ wits of $x_{k+1}$. This is then multiplied by the right from the matrix $A$ generating a new vector that is then added to $x_{k+m}$ ($\oplus$ is bitwise addition modulo two. The whole process is especially useful since many of operations can be calculated with bitwise and shift operations.

A more plain way to discuss this process is that the Mersenne Twister follows a process where an initial state is found from a series of numbers which is then **twisted** by the concatenation operation, before being **tempered** by the matrix. One note is that this process produces a reversable function, rather than a one-way function like most pseudo-random number generators.

# Cryptographic Generators
Cryptographic generators differ themselves with the addition of security due to the use of ciphers or hashes to protect attackers from finding the initial state. Despite this random numbers are commonly required for key generation, cryptographic nonces, and salts. In many ways these algorithm use a hashing algorithm to add a layer of protection on top of the initial randomness generated from another source.

# Inverse Transform Sampling 
Inverse transform sampling is a method of pseudo-random number generation from any probability distribution given its [[Continuous Probability#Cumulative Distribution Function|cumulative distribution function]]. Rather than generating numbers this ensures the results follow a distribution similar to the function. This process is calculated from a [[Probability Distribution Models#Gaussian (Normal) Distribution|normal distribution]] $f(x)$ by finding the CDF $F(x)$, and then computing the inverse $F^{-1}(x)$. This therefore converts the function $f(x)$ into a range between $[0,1]$ before finding the inverse which converts the input $x$ to be between $[0,1]$ and $y$ between $(-\infty,\infty)$. From this we can generate multiple random values between $[0,1]$ and find a result which matches a normal distribution of values.

# External Generators
External generators are a class of random number generator which uses external forces as a seed for a random number algorithm. This can include mouse movements, CPU states, outside data, and commonly time. These values are then use either with a cryptographic generator, or a more basic generator. Some common examples of these generators are **Fortuna** used by Apple, **/dev/random** by Linux, and **Intel Secure Key** by Intel.