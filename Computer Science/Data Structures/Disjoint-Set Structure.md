The disjoint-set data structure or union-find data structure is a [[Data Structures|data structure]] that stores a collection of disjoint sets that usually represent graph [[Graph Connectivity|connectivity]]. The main operations of the data structure are:
- **Find**, which determines what set an element is in.
- **Union**, which joins the contents of sets into a single set.

Through these methods an efficient method of joining sets, and finding what set items are in can be done. This has application within connectivity problems, and thus many algorithms including [[Graph Spanning Tree Algorithm|spanning tree]] algorithms, and some [[Graph Shortest Distance|shortest path]] algorithms.

# Disjoint-Set Forest
The disjoint-set forest is a representation of the disjoint-set structure that functions through the storage of set's denoted by a rooted tree, where each node represents an element. The nodes within the forest only store a pointer to its parent, and in the case of a root node a pointer to itself. This implementation ensures the main operations follow a new method.

**Make-set** operation creates a disjoint set that holds a parent array, and rank array. The rank array helps during the union operation as discussed later.
```pseudo
	\begin{algorithm}
	\caption{Make-Set($n$)}
	\begin{algorithmic}
		\State $parent[1..n] \gets 1..n$
		\State $rank[1..n] \gets 0$
	\end{algorithmic}
	\end{algorithm}
```

**Find** follows the parent pointers until the root is reached for a naïve implementation. Through the use of *path compression* this process can be sped up by flattening the tree so that a node points directly to its root node. This will result in a time complexity of $O(m\log n)$, where $m$ is the amount of operations.
```pseudo
	\begin{algorithm}
	\caption{Find}
	\begin{algorithmic}
		\If{$parent[x] \neq x$}
			\State $parent[x] \gets$ \Call{Find}{$parent[x]$}
		\EndIf
		\Return $parent[x]$
	\end{algorithmic}
	\end{algorithm}
```

**Union** checks if both nodes are contained within the same set, and if not points the root node of one tree to another. The speed of the find can be further increased in speed through the *union-by-rank* technique which ensures an upper bound on the height of trees during a merge. This means the smaller rank tree will always be a child of a larger ranked tree. Through both of these changes the sequence of $m$ operations will cost $O(m\cdot\alpha (n))$, where $\alpha$ is the **inverse Ackermann function**, which is a slow growing function that is practically constant.
```pseudo
	\begin{algorithm}
	\caption{Union($x,y$)}
	\begin{algorithmic}
		\State $x \gets$ \Call{Find}{$x$}
		\State $y \gets$ \Call{Find}{$y$}
		\If{$rank[x] < rank[y]$}
			\State $parent[x] \gets y$
		\Else
			\State $parent[y] \gets x$
			\If{$rank[x] = rank[y]$}
				\State $rank[x] \gets rank[x] + 1$
			\EndIf
		\EndIf
	\end{algorithmic}
	\end{algorithm}
```
