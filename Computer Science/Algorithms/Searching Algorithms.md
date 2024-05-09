Search is a problem solving technique that allows agents to systematically explores actions through growing a tree. Search maps the state space to nodes in a tree. The root represents the initial, and leaf nodes the goal state.

There are two approaches to search algorithms these are **uniformed** algorithms that only have the problem definition to operate on. This includes basic [[Graph Searches|graph searches]] and Dijkstra's algorithm. **Informed** algorithms have additional information that allows the use of heuristics

# Binary Search
A binary search is a linear search of a sorted list. It has a worst case complexity of $O(\log n)$.
```pseudo
	\begin{algorithm}
	\caption{BinarySearch(A,t, low, high)}
	\begin{algorithmic}
			\IF{$low > high$}
				\RETURN \FALSE
			\ENDIF
			\STATE $mid \gets (low + high)/2$
			\IF{$t=A[mid]$}
				\RETURN $mid$
			\ELIF{$t > A[mid]$}
				\RETURN \CALL{BinarySearch}{$A,t,mid+1, high$}
			\ELSE
				\RETURN \CALL{BinarySearch}{$A,t,low, mid-1$}
			\ENDIF
		
	\end{algorithmic}
	\end{algorithm} 
```

