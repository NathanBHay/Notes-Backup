Primality tests are algorithms which find whether a number $n$ is a [[Primality|prime number]]. This is an important algorithm within [[Number Theory|number theory]] with practical applications within [[Cryptography|cryptography]].

# Trial Division
The naive approach to testing primality is trial division which tests the divisibility of $n$ with all numbers from $2$ to $\sqrt n$. The pseudocode for this algorithm follows:
```pseudo
	\begin{algorithm}
	\caption{TrialDivision($n$)}
	\begin{algorithmic}
		\For{$k \gets 2$ \To $\sqrt n$}
			\If{$n\bmod k = 0$}
				\Return \False
            \EndIf
        \EndFor
		\Return \True
	\end{algorithmic}
	\end{algorithm}
```
The algorithm has a time complexity of $O(\sqrt n)$ or using a binary system $O(2^{d_n/2}d_n^2)$ where $d_n$ is the amount of binary digits of $n$.

# Fermat
Fermat's randomised primality test relies upon [[Primality#Fermat's Little Theorem|Fermat's little theorem]] which states a prime number must satisfy $a^{n-1}\equiv 1\bmod n$ where $a$ is the witness of the integer $n$. This algorithm doesn't guarantee the number is prime however does guarantee a number will be composite.
```pseudo
	\begin{algorithm}
	\caption{FermatRandomisedTest($n$)}
	\begin{algorithmic}
		\State $a \gets $ random number between $1<a<n-1$
		\If{$a^{n-2}\bmod n \neq 1$}
			\Return \False
        \EndIf
		\Return \True
	\end{algorithmic}
	\end{algorithm}
```
This algorithm is an example of a randomised algorithm and is the basis for the Miller-Rabin algorithm.

# Miller-Rabin
The Miller-Rabin primality test expands upon the methodology of the Fermat's randomised testing by finding strong probable primes. It relies upon the observation that if $n$ is an odd number then $n-1$ is even and can be represented as:
$$n-1=2^s\cdot t$$
Where $t$ is some odd integer. This means that we can factor the number as a series of powers of $2$ which allows us to compute the sequence given an odd natural number $n>3$ and a witness $a\in[2,n-2]$:
$$\forall x\in [0,s]: x_i=a^{2^i\cdot t}\bmod n=x_{i-1}^2$$
Where $s$ is the sequences length and $t$ is an integer. From this we are able to test $x_i=1$ and if this is true we can then test $x_{i-1}\not\equiv\pm 1(\bmod n)$ for $0<i\leq s$ and if this is true then $n$ cannot be prime. This can be written in pseudocode as:
```pseudo
	\begin{algorithm}
	\caption{MillRabin($n,k$)}
	\begin{algorithmic}
		\If{$n=2$ \Or $n=3$}
			\Return \True
        \EndIf
		\If{$n\bmod 2=0$}
			\Return \False
        \EndIf
        \State $s\gets0$
        \State $t\gets n-1$
        \While{$t\bmod 2=0$}
	        \State $s\gets s + 1$
	        \State $t\gets t/2$
        \EndWhile
        \For{$i\gets 1$ \To $k$}
			\State $a \gets $ random number between $1<a<n-1$
			\State $x\gets a^t\bmod n$
			\If{$x=1$}
				\Continue
            \EndIf
            \For{$j\gets 1$ \To $s$}
	            \If{$x=n-1$}
		            \Break
                \EndIf
				\If{$x=1$}
					\Return \False
                \EndIf
                \State $x\gets x^2\bmod n$
            \EndFor
        \EndFor
        \Return \True
	\end{algorithmic}
	\end{algorithm}
```
The algorithm using a [[Number Theoretic Algorithms#Modular Exponentiation|repeated squaring]] approach has a runtime of $O(k\log^3 n)$. An iteration of the main loop of Miller-Rabin has an accuracy of $\frac{1}{4}$ as for any odd composite $n$ there are at most $\frac{n}{4}$ witnesses for which $n$ is a strong pseudo-prime. From this we can say the algorithm has an accuracy of $\frac{1}{4^k}$ where $k$ is the amount of witnesses we test in the main loop.

# Sieve of Eratosthenes
The Sieve of Eratosthenes is an approach to finding all prime numbers up to a limit. This is done by iteratively marking the multiples of each prime number. This improves a [[Primality Testing#Trial Division|naive approach]] as it skips non-prime numbers. The algorithm has a time complexity of $O(n\log\log n)$.
```pseudo
	\begin{algorithm}
	\caption{Sieve($n$)}
	\begin{algorithmic}
		\State $A \gets$ [\True for all $2..n$]
		\For{$i\gets 2$ \To $\sqrt n$}
			\If{$A[i]=$ \True}
				\For{$j\gets i^2$ \To $j<n \step i$}
					\State $A[j] \gets$ \False
                \EndFor
            \EndIf
        \EndFor
		\Return $A$
	\end{algorithmic}
	\end{algorithm}
```

A common optimisation to a prime sieve is changing the step count. This reduces the necessary amount of memory while also decreasing the amount of computations significantly. A basic example of this is using a step count of $2$ where the sieve starts at $3$ and checks all odd numbers. In general the higher the step count the more hard coded values are required beforehand with it following the rule that given a prime step size of $x$ you will have to hard code all primes up until the previous prime. Successive step count increases also have diminishing effects on speed.