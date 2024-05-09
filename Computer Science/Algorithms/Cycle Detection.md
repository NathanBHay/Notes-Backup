Cycle detection algorithm find a cycle in a sequence of values. Mathematically, for any function $f$ that maps a finite set $S$ to itself, and any initial value $x_0\in S$ the sequence of iterated values must repeat over a certain length. Cycle detection finds the first value $x_i$ and the last value $x_j$.



```pseudo
	\begin{algorithm}
	\caption{Floyd($f, x0$)}
	\begin{algorithmic}
		\Comment{}
		\State $slow \gets f(x0)$
		\State $fast \gets f(f(x0))$
		\While{$fast \neq slow$}
			\State $slow \gets f(slow)$
			\State $fast \gets f(f(fast))$
        \EndWhile
	\end{algorithmic}
	\end{algorithm}
```
