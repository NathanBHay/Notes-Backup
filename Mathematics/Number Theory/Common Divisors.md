Within [[Number Theory|number theory]] a **common divisor** is one for which two integers are divisible by. The **Greatest Common Divisor** (GCD) is the greatest of these common divisors. This can be viewed with the recurrence: 
$$\gcd(m,n)=\begin{cases}n&\text{if }m=0\\\gcd(n\bmod m,m)&\text{otherwise}\end{cases}$$
Interestingly the greatest common divisor is distributive in that $\gcd(km,kn)=k\cdot\gcd(m,n)$. Therefore, values can be factored out to decrease the complexity of the calculation.

# Euclid's Algorithm
From the recurrence the **Euclidean algorithm** can derived which finds the greatest common divisor. It follows the pseudocode:
```pseudo
	\begin{algorithm}
	\caption{GCD(a,b)}
	\begin{algorithmic}
		\Input $a \geq b$
			
		\WHILE{$b \neq 0$}
			\State $r \gets b$
			\State $b \gets a \bmod b$
			\State $a \gets r$
		\Endwhile
		\Return a
	\end{algorithmic}
	\end{algorithm} 
```
The time complexity of the algorithm is $O(\log (a \cdot b))$, which can also be written as $O(\log_\varphi n)$ for small integers and $O((\log n)^2)$ for larger integers.
# Stein's Algorithm
The **binary GCD algorithm** or Stein's algorithm is a variant of Euclid's algorithm that uses the binary representation of numbers. This allows division to be replaced with arithmetic shifts, comparisons and subtractions as to reduce the clock cycles required for computation. It works on four identities:
1. $\text{gcd}(0,v)=v$ because everything divides zero, and similarly $\text{gcd}(u,0)=u$.
2. $\text{gcd}(2u,2v)=2\cdot\text{gcd}(u,v)$ which states factor out both even values.
3. $\text{gcd}(2u,v)=\text{gcd}(u,v)$, if $v$ is odd 2 is not a common divisor, similarly $\text{gcd}(u,2v)=\text{gcd}(u,v)$
4. $\text{gcd}(u,v)=\text{gcd}(|u-v|,\min(u,v))$ if both values are odd.

Implementation of this algorithm replaces division by 2 in favour of bit shifts and the count trailing zeroes functionality to improve speed of identity three. The algorithm has a time complexity of $O(n)$ where $n$ is the number of bits in the larger of the two numbers. This algorithm uses about $60\%$ fewer operations than the normal Euclidean algorithm. A pseudocode example is given below:
```pseudo
	\begin{algorithm}
	\caption{Stein($u,v$)}
	\begin{algorithmic}
		\If{$v=0$}
			\Return $u$
		\EndIf
		\If{$u=0$}
			\Return $v$
		\EndIf
		\If{$u%2=0$ \And $v%2=0$}
			\Return \Call{Stein}{$u>>1, v>>1$} $<<1$
		\ElIf{$u%2=0$}
			\Return \Call{Stein}{$u>>1, v$}
		\ElIf{$v%2=0$}
			\Return \Call{Stein}{$u, v>>1$}
		\Else
			\Return \Call{Stein}{$|u-v|,\min(u,v)$}
		\EndIf
	\end{algorithmic}
	\end{algorithm}
```
