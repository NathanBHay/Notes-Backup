[[Algorithmic Paradigms#Dynamic Programming|Dynamic programming]] is a heuristic which can be used to solve [[Pathfinding|pathfinding problems]]. The two main algorithms which solve this problem are Bellman-Ford which solves single-source shortest path, and Floyd-Warshall which solves all pair shortest path.

# Bellman-Ford Algorithm
The Bellman-Ford algorithm solves the single-source shortest-paths problem in a general case where edge weights may be negative. Therefore, this assumes that the graph $G=(V,E)$ for weight function $w: E \to \mathbb{R}$. This is done by returning a value indicating whether a negative-weight cycle exists. The following pseudocode is a Bellman-Ford procedure:
```pseudo
	\begin{algorithm}
	\caption{BellmanFord(G,s)}
	\begin{algorithmic}
		\STATE \CALL{InitSingleSource}{G,s}
		\FOR{$i\gets 1$ to $|G.V|-1$}
			\FOR{edge $(u,v) \in G.E$}
				\STATE \CALL{Relax}{u,v}
			\ENDFOR
		\ENDFOR
		\FOR{edge $(u,v) \in G.E$}
			\IF{$v.d > u.d + w(u,v)$}
				\RETURN \FALSE \COMMENT{ Check for cycles}
			\ENDIF
		\ENDFOR
		\RETURN \TRUE
	\end{algorithmic}
	\end{algorithm} 
```

This results in a time complexity of $O(|E|\cdot|V|)$. The algorithm can also be expressed through a [[Algorithmic Paradigms#Dynamic Programming|bellman equation]] which states the following relation as:
$$\text{OPT}((v,i)=\begin{cases}
0&\text{if }i=0 \text{ and }v=s\\
\infty&\text{if }i=0 \text{ and }v\neq s\\
\min\begin{cases}
\text{OPT}(v,i-1)\\
\min_{(u,v)\in E}\text{OPT}(u,i-1)+w(u,v)
\end{cases}&\text{otherwise}
\end{cases}$$
An important note of the following algorithm is that the algorithm doesn't detect negative cycles that aren't detectable from the starting node. This means some negative cycles won't be found as they don't effect the single source aspect of the problem.

The correctness of Bellman-Ford can be proved by the theorem that the algorithm terminates with the correct distance estimates for all vertices whose shortest path is well defined after at most $|V|-1$ iterations.

Bellman-Ford can be further **optimised** through using a queue that holds the edges that need to be relaxed. If an edge doesn't successfully relax then it won't need to be relaxed later unless its source vertex has its distance estimate improved. Additionally another approach is during the main iteration if no relaxations are successful then the shortest path has been found and can terminate early. If an early termination happens then there are no negative cycles that exist.

# Floyd-Warshall
Floyd-Warshall is an algorithm used to solve the all-pairs shortest path algorithm. The algorithm is traditionally seen as fast for dense graphs however can be beaten by BFS or Dijkstra for sparse graphs. Floyd-Warshall operates on the idea that optimal substructure exists between the path of multiple vertices. It uses a 2D matrix which is similar to an adjacency matrix but instead stores the distance from one node to another. It follows:
```pseudo
	\begin{algorithm}
	\caption{FloydWarshall(G(V,E))}
	\begin{algorithmic}
		\State $dist[1..n][1..n] \gets \infty$
		\State $dist[v][v] \gets 0 \textbf{ for all }v$
		\State $dist[u][v] \gets w(u,v) \textbf{ for all }edge(u,v) \in E$
		\For{$k \gets 1$ \TO $n$}
			\For{$u \gets 1$ \TO $n$}
				\For{$v \gets 1$ \TO $n$}
					\State $dist[u][v] \gets \min (dist[u][v],dist[u][k]+dist[k][v]$)
				\EndFor
			\EndFor
		\EndFor
		\Return $dist[1..n][1..n]$
	\end{algorithmic}
	\end{algorithm}
```
The time complexity of Floyd-Warshall for sparse and dense graphs follows $O(|V|^3)$ due to all three loops. The algorithm follows the invariant after $k$ iterations, $dist[u][v]$ contains the length of a shortest path $u \to v$ consisting only of intermediate vertices from 1 to $k$.
