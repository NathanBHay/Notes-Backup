Topological sorting or ordering is the process of ordering vertices such that a edge's start comes before a edges target. A topological ordering can only be done on a directed acyclic graph. Furthermore, all DAGs have at least one valid topological ordering. Topological ordering can be used for scheduling problems.

# Kahn's Algorithm
Kahn's algorithm is the most common algorithm for topological sorting. It functions through the use of a queue of vertices that follow the topological ordering. The algorithm given the use of an appropriate data structure has a time complexity of $O(|V|+|E|)$ as each vertex is visited once, and each edge is removed. The algorithm follows the pseudocode:
```pseudo
	\begin{algorithm}
	\caption{KahnsAlgorithm($G(V,E)$)}
	\begin{algorithmic}
		\State $order \gets \emptyset$
		\State $ready \gets$ \Call{Queue}{$\dots$} \Comment{Add all Vertices with no Incoming Edges}
		\While{$ready \neq \emptyset$}
			\State $u \gets ready.$\Call{pop}{}
			\State $order.$\Call{append}{$u$}
			\For{$edge (u,v) \in u.Adj$}
				\State \Call{remove}{$edge (u,v)$}
				\If{$v.IncomingEdge = \emptyset$}
					\State $ready.$\Call{push}{$v$}
				\EndIf
			\EndFor
		\EndWhile
		\Return $order$
	\end{algorithmic}
	\end{algorithm}
```

# Depth-First Topological
[[Graph Searches#Depth-First Search|Depth-First Search]] can be used for topological ordering as all edges are visited before a node is fully searched. This means that if a vertex is added to the order array before visiting all descendants it will have already been visited. This algorithm takes $O(|V|+|E|)$ worst-case time as the algorithm is running a depth-first search. This follows the pseudocode:
```pseudo
	\begin{algorithm}
	\caption{DFS Topological Sort}
	\begin{algorithmic}
		\Function{TopologicalSort}{$G(V,E)$}
			\State $order \gets \emptyset$
			\State $visited[1..n] \gets$\False
			\For{$v \in G.V$}
				\If{\Not $visited[v]$}
					\State \Call{DFS}{$v$}
				\EndIf
			\EndFor
			\Return \Call{Reverse}{$order$}
		\EndFunction
		\State
		\Procedure{DFS}{$u$}
			\State $visited[u] \gets$\True
			\For{$v \in U.adj$}
				\If{\Not $visited[v]$}
					\State \Call{DFS}{$v$}
				\EndIf
			\EndFor
			\State $order.$\Call{append}{$u$} \Comment{Add to order after visiting descendants}
		\EndProcedure
	\end{algorithmic}
	\end{algorithm}
```
