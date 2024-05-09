Suffix arrays are a compact [[String Retrieval Structures|string retrieval]] [[Data Structures|data structure]] that stores all suffixes in an [[Data Structures#Array|array]] indexed by lexicographical order. This means for a string $S[1..n]$ there exists $n+1$ suffixes, including the empty suffix which is first lexicographically. 

## Naive Creation
The simplest approach to building a suffix array follows the naive approach which simply builds a list containing the indices from $1$ to $n$ and sorts them by comparing suffixes. This implementation has a time complexity of $O(n^2\log n)$. It follows the code:
```pseudo
	\begin{algorithm}
	\caption{Naive Creation}
	\begin{algorithmic}
		\Function{CreateSuffixArray}{$S[1..n]$}
			\State $SA[1..n] \gets [1..n]$
			\State \Call{sort}{$SA[1..n]$,\Call{SuffixCompare}{$S,\dots$}}
			\Return $SA$
		\EndFunction
		\State
		\Function{SuffixCompare}{$S[1..n],i,j$}
			\Return $S[i..n] < S[j..n]$
		\EndFunction
	\end{algorithmic}
	\end{algorithm}
```

## Using Suffix Trees
A common approach to creating a suffix array is through iterating through a [[String Retrieval Structures#Suffix Trees|suffix tree]]. This is as the path from the root to all leafs in the tree represent a list of all suffixes. This operation involves a $O(n)$ operations, with it being bounded by the creation of the suffix tree. This can range depending on the approach used.

## Prefix Doubling
Another approach is the **prefix doubling algorithm** which constructs an array by sorting the suffixes by their first $k$ characters where $k$ is a power of $2$. This works due to **fast suffix comparison** which states that given two strings of the same even length split the strings in two such that $A_1, A_2$ and $B_1,B_2$. If these halves are sorted then just by checking one element you can find if there is any difference. As the sorted order exists within the creation algorithm this proves true. This results in a complexity of $O(n\log^2 n)$. The pseudocode for this follows:
```pseudo
	\begin{algorithm}
	\caption{Prefix Doubling}
	\begin{algorithmic}
		\Function{CreateSuffixArray}{$S[1..n]$}
			\State $SA[1..n] \gets [1..n]$
			\State $rank[1..n] \gets$ [\Call{ord}{$S[1..n]$}]
			\For{$k \gets 0$ \To $n, \step 2k$}
				\State \Call{sort}{$SA[1..n]$,\Call{SuffixCompare}{$rank,k,\dots$}}
				\State $temp[1..n] \gets 0$
				\For{$i\gets 1$ \To $n-1$}
					\State $temp[SA[i+1]] \gets temp[SA[i]]+$\Call{SuffixCompare}{$rank[1..n],k,SA[i],SA[i+1]$}
				\EndFor
				\State \Call{swap}{$temp,rank$}
			\EndFor
			\Return $SA$
		\EndFunction
		\State
		\Function{SuffixCompare}{$rank[1..n],k,i,j$}
			\If{$rank[i]\neq rank[j]$} \Comment{Compare by first halves}
				\Return $rank[i]<rank[j]$
			\Elif{$i+k\leq n$ \And $j+k\leq n$} \Comment{Compare by second halves}
				\Return $rank[i+k]<rank[j+k]$
			\Else \Comment{Second half is empty}
				\Return $j<i$
			\EndIf
		\EndFunction
	\end{algorithmic}
	\end{algorithm}
```

## Pattern Matching
Suffix arrays can be used for [[Pattern Matching]] in $O(m\log n)$. This follows an algorithm of:
```pseudo
	\begin{algorithm}
	\caption{FindPattern($SA[1..n],T[1..n],P[1..m]$)}
	\begin{algorithmic}
		\Comment{Binary Search to find first occurence of P}
		\State $lo \gets 0$, $hi \gets n$
		\While{$lo<hi-1$}
			\State $mid \gets |\frac{lo+hi}{2}|$
			\If{$T[SA[mid]..n]<P[1..m]$}
				\State $lo \gets mid$
			\Else
				\State $hi \gets mid$
			\EndIf
		\EndWhile
		\State $begin \gets hi$
		\State \Comment{Binary Search to find final occurence of P}
		\State $lo \gets 1$, $hi \gets n+1$
		\While{$lo<hi-1$}
			\State $mid \gets |\frac{lo+hi}{2}|$
			\If{$T[SA[mid]..n]\leq P[1..m]$}
				\State $lo \gets mid$
			\Else
				\State $hi \gets mid$
			\EndIf
		\EndWhile
		\State $end \gets lo$
		\Return $begin, end$
	\end{algorithmic}
	\end{algorithm}
```
