A partitioning [[Algorithms|algorithm]] deals with the issue of creating two [[Set Theory|subsets]] from a multiset. In general these algorithms create a left, right, and pivot set where elements less than the pivot are in the left, and greater than are in the right. The pivot set contains all elements equal to the pivot. Partitioning algorithms are used within other common algorithms such as [[Sorting Algorithms#Quick Sort|quick sort]]. A partitioning algorithm can have the additional constraint of balance, which happens if both subsets contain equal element amounts.

# Naïve Partition
The naïve partitioning algorithm simplifies partitions into three temporary array, one for elements greater, less than, and equal to the pivot. This function then returns the middle pivot. The algorithm is stable, and functions at $O(n)$. Despite this the algorithm isn't in-place meaning the space complexity uses $O(n)$ auxiliary space. The pseudocode for this algorithm follows:
```pseudo
	\begin{algorithm}
	\caption{Partition($A[1..n],pivot$)}
	\begin{algorithmic}
		\STATE $left \gets \emptyset$
		\STATE $pivots \gets \emptyset$
		\STATE $right \gets \emptyset$
		\FOR{$i$ in $A$}
			\IF{$A[i] < pivot$}
				\STATE $left.$\CALL{append}{A[i]}
			\ELIF{$A[i] = pivot$}
				\STATE $left.$\CALL{append}{A[i]}
			\ELSE
				\STATE $pivots.$\CALL{append}{A[i]}
			\ENDIF
		\ENDFOR
		\STATE $A \gets left + pivots + right$
		\RETURN $left.length + |pivots.length / 2|$
	\end{algorithmic}
	\end{algorithm} 
```

# Hoare Partition
Hoare partition is an in-place algorithm that instead of creating new arrays looks at the start and end swaps them to be on the correct side of the pivot. This results in the original array turning into a correctly partitioned array. It has a time complexity of $O(n)$, but has the disadvantage that it lacks stability. Despite this, it is more efficient in comparison to a naïve approach. Hoare partitioning as its first step does make the first element of the array swap with the pivot before finally setting it back. With the $j$ index being used to separate the left and right.
```pseudo
	\begin{algorithm}
	\caption{HoarePartition(A[lo..hi],pivot)}
	\begin{algorithmic}
		\STATE \CALL{swap}{A[lo],A[pivot]}
		\STATE $i \gets lo$, $j \gets hi$
		\WHILE{$i \leq j$}
			\WHILE{$i \leq j$ \AND $A[i] \leq A[pivot]$}
				\STATE $i \gets i+1$
			\ENDWHILE
			\WHILE{$i \leq j$ \AND $A[j] > A[lo]$}
				\STATE $j \gets j-1$
			\ENDWHILE
			\IF{$i \leq j$}
				\STATE \CALL{swap}{A[i],A[j]}
			\ENDIF
		\ENDWHILE
		\STATE \CALL{swap}{A[lo],A[j]}
		\RETURN $j$
	\end{algorithmic}
	\end{algorithm} 
```

A large disadvantage of Hoare partitioning is that it performs poorly when there are many elements equal to the pivot. This is as all elements equal to the pivot will end up on one side of the pivot, usually the left. To fix this a post-processing step can be added to balance the result

# Dutch National Flag Partitioning
Dutch National Flag Partitioning attempts to fix the issues of the Hoare Partitioning method through a redefinition of the problem as given an array of $n$ items that are colored *red*, *white*, or *blue* sort them such that all objects of the same color are together. This functions by partitioning red items as less than the pivot, white items as equal to the pivot, and blue items as greater than the pivot. To achieve this $lo,mid,hi$ pointers need to be maintained. This results in the array having the invariant and groups:
- $A[1..lo-1]$ for red elements that are less than the pivot.
- $A[lo..mid-1]$ for white elements equal to the pivot
- $A[mid..hi]$ for unknown elements.
- $A[hi+1..n]$ for blue elements larger than the pivot

Despite the advantages of the Dutch National Flag Partition it still lacks stability. It follows the pseudocode:
```pseudo
	\begin{algorithm}
	\caption{DutchFlagPartition(A[1..n],pivot)}
	\begin{algorithmic}
		\STATE $l \gets 1$, $mid \gets 1$, $hi \gets n$
		\WHILE{$mid \leq hi$}
			\IF{$A[mid] < pivot$} \COMMENT{Red Case}
				\STATE \CALL{Swap}{A[mid], A[lo]}
				\STATE $lo \gets lo+1$, $mid \gets mid+1$
			\ELIF{$A[mid]=pivot$} \COMMENT{White Case}
				\STATE $mid \gets mid+1$
			\ELSE \COMMENT{White Case}
				\STATE \CALL{Swap}{A[mid], A[hi]}
				\STATE $hi \gets hi -1$
			\ENDIF
		\ENDWHILE
		\RETURN $lo, mid$
	\end{algorithmic}
	\end{algorithm} 
```
