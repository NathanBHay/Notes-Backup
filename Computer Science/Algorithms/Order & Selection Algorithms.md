The **order statistics problem** attempts to find the $k$ smallest element in the array. This can be used to find the first order statistic which is the minimum, the $n$ order for the maximum or the median which is given by the $(n+1)/2$ order statistic. This problem can be extended by the **selection problem** which states that the input data includes a sequence and its given values.

The naïve approach to this problem would sort the array to find the $k$ element. This would result in an algorithm with a time complexity of $O(n\log n)$ for fast sorting algorithms. However, additional algorithms have been made to speed up this process significantly.

# Min/Max Algorithm
The most basic selection algorithm attempts to find the minimum or maximum of the given array. It does this through a simple comparison of all elements. It follows the basic pseudocode of:
```pseudo
	\begin{algorithm}
	\caption{Minimum(A)}
	\begin{algorithmic}
		\STATE $min \gets A[1]$
		\FOR{$elem \in A$}
			\IF{$elem < min$}
				\STATE $min \gets elem$
			\ENDIF
		\ENDFOR
		
	\end{algorithmic}
	\end{algorithm} 
```

This algorithm is a $O(n)$ algorithm, and has a space complexity of $O(1)$. Another interesting case for this problem is searching for minimum and maximum where to find the result $2n$ comparisons will be done. This can be improved by iterating through two numbers and only comparing the lower of the two with the minimum and the higher with the maximum. This cuts down on the amount of comparisons to $1.5n$. The algorithm can be written as:
```pseudo
	\begin{algorithm}
	\caption{SelectMinMax(A)}
	\begin{algorithmic}
		\STATE $min, max \gets A[1]$
		\FOR{$i \gets 1+n\bmod 2$ \TO $n\step 2$}
			\If{$A[i]<A[i+1]$}
				\If{$A[i]<min$}
					\State $min \gets A[i]$
				\EndIf
				\If{$A[i+1]>max$}
					\State $max \gets A[i+1]$
				\EndIf
			\Else
				\If{$A[i]>max$}
					\State $max \gets A[i]$
				\EndIf
				\If{$A[i+1]<min$}
					\State $min \gets A[i+1]$
				\EndIf
			\EndIf
		\ENDFOR
		\Return $min, max$
	\end{algorithmic}
	\end{algorithm} 
```

# Quickselect
Quickselect is a generalised algorithm for the problem that attempts to find $k$ at any order. This algorithm is based on the idea from [[Sorting Algorithms#Quick Sort|quick sort]] that selecting from the half of the array that doesn't contain the answer is unnecessary. The algorithm follows the pseudocode:
```pseudo
	\begin{algorithm}
	\caption{QuickSelect(A[1..n],k)}
	\begin{algorithmic}
		\IF{$hi > lo$}
			\STATE $pivot \gets A[1]$ \Comment{Change Pivot for Better Results}
			\STATE $mid \gets $ \CALL{Partition}{$A,pivot$}
			\IF{$k < mid$}
				\RETURN \CALL{QuickSelect}{$A[lo..mid-1],k$}
			
			\ELIF{$k > mid$}
				\RETURN \CALL{QuickSelect}{$A[mid+1..hi],k$}
			\ENDIF
		\ENDIF
		\RETURN A[k]
		
	\end{algorithmic}
	\end{algorithm} 
```

This function has a worse case time complexity of $O(n^2)$ given the use of minimum and maximum pivot. To decrease the time complexity of this algorithm the choice of pivot can be modified.

## Randomized Pivot Selection
One approach to decrease the complexity of quick select is the use of a **random pivot selection**. This is usually done through the use of a [[Random Number Generation|Pseudo-RNG]]. This algorithm can proves more efficient with a worst case complexity of $O(n)$, despite this it lacks deterministic properties.

## Median of Medians
Median of medians is a pivot selection technique that can be ran in $O(n)$, while maintaining deterministic behaviours. The median of medians is an algorithm that selects an approximate median by dividing the original list into $\frac{n}{5}$ groups. This finds the median of each group (normally through sorting), and whereupon quick select is used to find an approximate median. The median will be bounded between the middle $40\%$. This code can be expressed as:
```pseudo
	\begin{algorithm}
	\caption{Median of Medians}
	\begin{algorithmic}
		\FUNCTION{MedianOfMedian}{A}
		\IF{$hi - lo < 5$}
			\RETURN \CALL{MedianOfFive}{A}
		\ENDIF
		\STATE $medians \gets \emptyset$
		\FOR{$i \gets lo$ \TO $hi$ step $5$}
			\STATE $j \gets $ \CALL{Minimum}{i+4,hi}
			\STATE $medians.$\CALL{append}{\CALL{MedianOfFive}{$A$}}
		\ENDFOR
		\STATE $n \gets$ \CALL{Length}{$medians$}
		\RETURN \CALL{QuickSelect}{$medians[1:n], \frac{(n+1)}{2}$}
	\ENDFUNCTION
	\State
	\FUNCTION{MedianOfFive}{A}
		\STATE \CALL{InsertionSort}{A}
		\RETURN $A[(lo+hi)/2]$
	\ENDFUNCTION
	\end{algorithmic}
	\end{algorithm}
```
