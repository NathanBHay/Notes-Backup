Computer Science has a variety of common problems found within the topic of [[Graph Theory|graph theory]]. These problems are usually used to depict real technical problems which are expressed mathematically. To this end here is a set of general graph problems that are commonly found but don't require an entire page.

# Transitive Closure
Transitive closure is a similar problem to all-pairs shortest-paths as its goal is to find a new graph $G'$ such that edges exist if and only if there is a path between $u$ and $v$. This means rather than computing the distance all that needs to be done is find if a connection exists. This is found through using a variant of [[DP Pathfinding Algorithms#Floyd-Warshall|Floyd-Warshall]] that rather than keeping a distance matrix keeps a matrix of Boolean values, $connected[1..n][1..n]$. To find the results of the problem use Floyd-Warshall but instead each iteration find:
$$connected[u][v] \lor (connected[u][k] \land connected[k][v])$$

# Critical Path Problem
The critical path problem is the problem of finding the **longest** path in a directed acyclic graph. This problem usually is used to represent the minimum amount of weight accrued from completing all prerequisites. This problem is another dynamic programming problem that attempts to find the $longest[v]$. This is found through finding the base case that all vertices with no outgoing edges is equal to $0$. To determine this path begin at a vertex $u$ and consider all outgoing edges of each vertex to find the longest total path. This finds the relation:
$$\text{longest}[u]=\max_{v\in \text{adj}[u]}(w(u,v)+\text{longest}[v]$$
This means the subproblems are dependent in a reverse topological order. Computing this order and iterating over every vertex and edge takes $O(|V|+|E|)$ which is the complexity of the problem. An algorithmic approach to this is:
```pseudo
	\begin{algorithm}
	\caption{CriticalPath($u$)}
	\begin{algorithmic}
		\If{$longest[u] = \null$}
			\State $longest[u] \gets 0$
			\For{$edge(u,v) \in u.E$}
				\State $longest[u] \gets \max(longest[u], w(u,v)+$\Call{CriticalPath}{$v$})
			\EndFor
		\EndIf
		\Return $longest[u]$
	\end{algorithmic}
	\end{algorithm}
```

The algorithm is similar to [[Graph Searches#Depth-First Search|depth-first search]] but uses a top-down dynamic programming approach to memoize the path.
