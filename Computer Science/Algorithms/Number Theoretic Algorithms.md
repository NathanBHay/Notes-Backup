# Modular Exponentiation
Modular exponentiation finds the remainder of a number divided by $n$ where the number $a$ is first raised to the power of $b$. This means it finds:
$$a^b\bmod n$$
Modular exponentiation is common in number theoretic algorithms and therefore an improvement to its calculation is important. The naive approach to solving this simply calculates $a^b$ by doing $b$ multiplications of $a$, before finding the modulo of the result. This has a time complexity of $O(2^{2d_b}d_a^2+2^{d_b}d_ad_n)$ or $O(2^{d_b})$ for linear time multiplication, where $d_a$, $d_b$, and $d_n$ are the amount of binary digits to represent the various numbers.

This approach can be improved by leveraging the fact $xy\bmod z=((x\bmod z)\cdot(y\bmod z))\bmod z$ and the [[Number Systems#Binary|binary]] representation of a number $x=d_3d_2d_1d_0$ can be decomposed as the value $x^y=(a^{2^3})^{d_3}(a^{2^2})^{d_2}(a^{2^1})^{d_1}(a^{2^0})^{d_0}$ or $\prod ((a^{2^i})^{d_i})$.  Through this we can use *repeated squaring* to find the square of each digit allowing us to compute modular exponentiation as:
$$\text{result}\gets (\text{result}\cdot a^{2^i}\bmod n)\bmod n$$
Where $i$ is the set of binary digits where $d=1$. The complexity of this approach is bound by $O(d_ad_n+d_bd_n^2)$ where the first term represents evaluating $x_0$, and the second term represents squaring the previous result and dividing by $n$. The pseudocode to find this is:
```pseudo
	\begin{algorithm}
	\caption{ModularExpo($a,b,n$)}
	\begin{algorithmic}
		\If{$n=1$}
			\Return $0$
        \EndIf
        \State $result \gets 1$
        \State $a \gets a\bmod b$
        \While{$a > 0$}
	        \If{$b \bmod 2 == 1$} \Comment{If $d_b$ is 1}
		        \State $result \gets (res \cdot a) \bmod n$
            \EndIf
            \State $n \gets n >> 1$
			\State $a \gets (a\cdot a)\bmod n$
        \EndWhile
        \Return $result$
	\end{algorithmic}
	\end{algorithm}
```
