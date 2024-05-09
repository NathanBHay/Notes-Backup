In [[Graph Theory]] a spanning tree is a tree that includes all the vertices within a graph. A common problem within computer science is finding the minimum spanning tree, with the minimum being derived from the total of all weighted edges of the graph. A mathematical way to view this is to find use the undirected graph $G=(V,E)$, to find the minimum spanning tree using the idea that weights can be found with $w(u,v)$. We must find the acyclic subset $T \subseteq E$ that connects all vertices whose total weight can be found as:
$$
\min \Bigl( \sum_{(u,v)\in T} w(u,v) \Bigl)
$$
This function finds the minimum, or possibly maximum spanning tree. To solve this problem there are two common algorithms used, those are Prim's, and Kruskal's.

# Kruskal's Algorithm
Kruskal's algorithm solves the minimum spanning tree problem by growing a forest of minimum spanning trees at the lowest weight. It uses a [[Algorithmic Paradigms#Greedy|greedy]] approach to solving the problem. It follows the pseudocode:
```pseudo
	\begin{algorithm}
	\caption{Kruskal($G(V,E)$)}
	\begin{algorithmic}
		\State \Call{Sort}{$E,key=w(u,v)$}
		\State $forest \gets$ \Call{UnionFind.Initialise}{$n$}
		\State $T \gets (V,\emptyset)$
		\For{$edge (u,v) \in E$}
			\If{$forest.$\Call{Find}{$u$} $\neq forest.$\Call{Find}{$v$}}
				\State $forest.$\Call{Union}{$u,v$}
				\State $T.$\Call{AddEdge}{$u,v$}
			\EndIf
		\EndFor
		\Return $T$
	\end{algorithmic}
	\end{algorithm}
```

Due to the sorting operation being the most intensive the algorithm runs at a time complexity of $O(E \log V)$ due to the union-find operations, and $O(|E|\log |E|)$ in the sorting procedure. The invariant states that every iteration of Kruskal's the current set of edges $T$ is a subset of some minimum spanning-tree of $G$.

# Prim's Algorithm
Prims algorithm is also a greedy approach, but unlike Kruskal's is more similar to [[A-Star#Dijkstra's|Dijkstra's algorithm]]. It operates under the idea that the minimum spanning tree can be created from a single tree that grows, rather than multiple sparse trees. This is usually done through the use of priority queue that store the edges of adjacent nodes as to find the minimum value to add to the tree. Prim's follows the pseudocode:
```pseudo
	\begin{algorithm}
	\caption{Prim($G(V,E),r$)}
	\begin{algorithmic}
		\State $dist[1..n] \gets \infty$
		\State $parent[1..n] \gets \null$
		\State $T \gets ({r}, \emptyset)$
		\State $dist[r] \gets 0$
		\State $Q \gets$\Call{PriorityQueue}{$V[1..n],key(v)=dist[v]$}
		\While{$Q \neq \emptyset$}
			\State $u \gets Q.$\Call{ExtractMin}{}
			\State $T.$\Call{AddVertex}{$u$}
			\State $T.$\Call{AddEdge}{$parent[u],u$}
			\For{$edge (u,v) \in u.Adj)$}
				\If{\Not $v\in T$ \And $dist[v] > w(u,v)$}
					\State $Q.$\Call{DecreaseKey}{$v,w(u,v)$}
					\State $dist[v] \gets w(u,v)$
					\State $parent[v] \gets u$
				\EndIf
			\EndFor
		\EndWhile
		\Return $T$
	\end{algorithmic}
	\end{algorithm}
```

The use of a priority queue results in a time complexity of $O(|E|\log |V|)$. The algorithm follows an invariant of every iteration the current set of collected edges in $T$ is a subset of some minimum spanning tree.
