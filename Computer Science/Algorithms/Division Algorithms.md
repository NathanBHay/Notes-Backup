Division algorithms find given two integers $n$ and $d$ what is their quotient or remainder. These algorithms are closely related to [[Number Theory|divisors]] and their associated theorems and algorithms. Division algorithms are classified in two ways - fast and slow. Slow division algorithms result in a digit being found at each iteration while fast methods compute approximations of values to speed up the process. Most algorithms take a dividend, and divisor as input and result in a quotient and remainder.

# Division by Repeated Subtraction
Subtraction is one of the few core operations on all computer architectures, and thus division by repeated subtraction is a common method. It is usually the first method of division taught. The method can only be done on unsigned integers and follows:
```pseudo
	\begin{algorithm}
	\caption{UnsignedDivide($n,d$)}
	\begin{algorithmic}
		\State $q \gets 0$; $r \gets n$
		\While{$r \geq d$}
			\State $r \gets r - d$
			\State $q \gets q + 1$
		\EndWhile
	\Return $q,r$
	\end{algorithmic}
	\end{algorithm}
```

This method has a time complexity of $O(q)$, and thus is considered very slow. Despite this for small numbers or numbers with a divisor similar to the dividend this algorithm can prove efficient. This method can be further expanded to include signed integers through converting both $n$, and $d$ to be positive. This is done through:
```pseudo
	\begin{algorithm}
	\caption{DivideSigned($n,d$)}
	\begin{algorithmic}
		\If{$d < 0$} \Comment{Ensure divisor is positive}
			\State $q,r \gets$ \Call{DivideSigned}{$n,-d$}
			\Return $-q,r$
		\EndIf
		\If{$n<0$} \Comment{Ensure Dividend is positive}
			\State $q,r \gets$ \Call{DivideSigned}{$-n,d$}
			\If{$r=0$} 
				\Return $-q,0$
			\Else
				\Return $-q-1, d-r$
			\EndIf
		\EndIf
		\Return \Call{DivideUnsigned}{$n,d$}
	\end{algorithmic}
	\end{algorithm}
```

# Long Division
Long division is the standard algorithm used to compute division by hand. It functions through shifting from the left to right side of the dividend, subtracting the largest possible multiple from the divisor. This method is further simplified on [[Number Systems#Binary|binary]] system as division operations result in two possible outputs. The pseudocode for a binary divide is:
```pseudo
	\begin{algorithm}
	\caption{LongUnsignedDivision($n,d$)}
	\begin{algorithmic}
		\State $q,r \gets 0$
		\For{$i \gets n.size$ \To $0\step-1$} \Comment{Where n.size is number of bits}
			\State $r \gets r << 1$
			\State $r[0] \gets n[i]$
			\If{$r \geq d$}
				\State $r \gets r-d$
				\State $q[i] \gets 1$
			\EndIf
		\EndFor
		\Return $q,r$
	\end{algorithmic}
	\end{algorithm}
```

The algorithm above uses $n$, and $d$ as inputs which are binary integers that can be accessed through $[i]$. This works through bit shifting the digit down to allow for a number to be subtracted to from the result, where a one is placed given $r>d$. The time complexity of this algorithm is found as $O(q^2)$, where $q$ is the number of digits in the quotient.

# Slow Division
Slow division methods are the main method of fixed-point division found on base computer architectures. They all rely upon a standard [[Recursion|recurrence equation]]:
$$R_{j+1}=B\cdot R_j-D \cdot q_{n-(j++1)}$$
Where $R_j$ is the $j$-th partial remainder of the division, $B$ is the base, $Q_{n-(j+1)}$ is the digit of the quotient in position $n-(j+1)$ where the digit positions are numbered from least significant $0$ to most $n-1$. $n$ is the number of digits in the quotient, and $D$ is the divisor.

## Restoring Division
Restoring division operates on fixed-point fractional numbers and depends on the assumption $0<D<N$. A basic form of the algorithm for binary is:
```pseudo
	\begin{algorithm}
	\caption{RestoringDivision($N,D$)}
	\begin{algorithmic}
		\State $R \gets N$
		\State $Q \gets 0$
		\State $D \gets D << n$
		\For{$i \gets n$ \TO $0 \step -1$}
			\State $R \gets 2\cdot R - D$
			\If{$R \geq 0$}
				\State $Q[i] \gets 1$ \Comment{Result-bit 1}
			\Else
				\State $Q[i] \gets 0$ \Comment{Result-bit 0}
				\State $R \gets R+D$ \Comment{New Partial Remainder Restored}
			\EndIf
		\EndFor
		\Return $Q,R$
	\end{algorithmic}
	\end{algorithm}
```

## Non-Restoring Division
Non-restoring division uses a digit set of ${-1,1}$ for integer digits which results in a more complex algorithm. Despite this the process enables a possible decrease in operations by up to half resulting in faster execution. This is due to the lack of a restoring step where a new partial remainder is restored.
```pseudo
	\begin{algorithm}
	\caption{NonRestoringDivision($N,D$)}
	\begin{algorithmic}
		\State $R \gets N$
		\State $D << n$
		\For{$i\gets n$ \To $0 \step -1$}
			\If{$R \geq 0$}
				\State $q[i] \gets q[i] + 1$
				\State $R \gets 2 \cdot R -D$
			\Else
				\State $q[i] \gets q[i] - 1$
				\State $R \gets 2 \cdot R +D$
			\EndIf
		\EndFor
		\Return $Q,R$
	\end{algorithmic}
	\end{algorithm}
```
