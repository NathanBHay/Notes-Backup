The maximum subarray problem also called the maximum segment sum problem is a problem where the maximum sum within a contiguous subarray. Formally this can be expressed as find indices $i$ and $j$ such that:
$$\arg\max\sum_{x=i}^jA[x]$$
There are several techniques to solving this problem which includes [[Algorithmic Paradigms#Brute Force|brute force]], [[Algorithmic Paradigms#Divide and Conquer|divide and conquer]], and [[Algorithmic Paradigms#Dynamic Programming|dynamic programming]].

The naive approach to solving this 
```pseudo
	\begin{algorithm}
	\caption{Naive($nums$)}
	\begin{algorithmic}
		\State $best \gets -\infty$
		\For{$i\gets 0$ \To \call{length}{$nums$}}
			\State $curr \gets 0$
			\For{$i\gets 0$ \To \call{length}{$nums$}}
				\State $curr \gets curr + nums[j]$
				\State $best \gets \max(best, curr)$
			\EndFor
        \EndFor
		\Return $best$		
	\end{algorithmic}
	\end{algorithm}
```

**Kadane's algorithm** is a form of the dynamic programming version where the algorithm 
```pseudo
	\begin{algorithm}
	\caption{Kadane($nums$)}
	\begin{algorithmic}
		\State $best \gets -\infty$
		\State $curr \gets 0$
		\For{$x\in nums$}
			\State $curr \gets \max(x, curr + x)$
			\State $best \gets \max(best, curr)$
        \EndFor
		\Return $best$
	\end{algorithmic}
	\end{algorithm}
```
