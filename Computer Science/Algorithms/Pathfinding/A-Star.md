The A* algorithm is a common approach to solving [[Pathfinding|pathfinding problems]] and is considered an informed [[Graph Searches|graph search]]. It uses a [[Algorithmic Paradigms#Greedy|greedy]] heuristic to find the shortest distances between either all nodes or between two pairs. The algorithm works on a directed graph $G=(V,E)$, for cases where all edge weights are non-negative $W: E \to \mathbb{R}^+$. The algorithm works by maintaining a set of vertices called the **open list** whose shortest path weights have been determined. This set is then modified by selecting adjacent vertices with a minimum shortest path estimates and relaxing the edges as to get the values. It is usually implemented with a priority [[Abstract Datatypes#Queue|queue]] as a [[Abstract Datatypes#Heap|heap]]. The shortest path weights are found as  $w(u,v) + h(v)$, where $h(v)$ is the search heuristic. This search heuristic enables the algorithm to be make smart decisions.
```pseudo
	\begin{algorithm}
	\caption{Dijkstra(G,s)}
	\begin{algorithmic}
		\STATE \CALL{InitSingleSource}{G,s}
		\STATE $S \gets \emptyset$
		\STATE $Q \gets$ \CALL{MinPriorityQueue}{$G.V$}
		\WHILE{$Q \neq \emptyset$}
			\STATE $u \gets$ \CALL{Extract-Min}{Q}
			\STATE $S \gets S \cup \{u\}$
			\FOR{$v \in u.adjacent$}
				\STATE \CALL{Relax}{$u,v$}
			\ENDFOR
		\ENDWHILE
	\end{algorithmic}
	\end{algorithm} 
```
The algorithm has a loop invariant that states each iteration of the while $v.d=(s,v)$. A* algorithm has a time complexity of $O(V^2)$ when implemented with an adjacency matrix or with a list for a queue instead of a heap. When using a heap and an adjacency list the complexity becomes $O(|E|\log {|V|})$.

There are two main implementations of A*'s algorithm when it comes to adding vertices to the queue. The first implementation is the decrease-key implementation that inserts all vertices into the priority queue, and uses an update function to change the priorities. The second implementation initialises an empty queue which is inserted to during each iteration.

The algorithm is considered **optimally efficient** meaning there exists no algorithm $A$ which is less informed than A* that can expand fewer nodes. 

**Tie breaking** is the process of deciding which node to take given an equal distance in the priority-queue. There are a variety of strategies for this process these include FIFO and LIFO choices as well as comparisons between $h$ and $w$ values.
# Dijkstra's
Dijkstra's algorithm is a generalisation of A* that uses a search heuristic where $h(v)=0$. This algorithm is usually easier to implement, and useful in cases where a heuristic isn't obvious. 

# Weighted A*
Weighted A* (WA*) is a variant of A* that is sub-optimal meaning it doesn't guarantee a correct result. This however is corrected by the fact that it expands less nodes, and therefore is faster. The main concept behind WA* is to multiply the heuristic by some factor $w^*$. This results in a function: 
$$w(u,v) + w^*\cdot h(v)$$
 For cases with a low $w^*$ the result is more optimal however less fast, and inverse for larger values.

# D* Algorithm
D* is similar to A* in that it maintains a list nodes called the *open list (the priority queue)* while also marking every node with five possible states. These are:
- **New** which indicates it has never been place on the open list.
- **Open** which indicates it is on the open list.
- **Closed** which means it is no longer on the list.
- **Raise** which indicates its cost to be higher than the last time it was on the open list.
- **Lower** which indicates its cost is lower than the last time it was on the open list.

The algorithm iteratively adds items from the open list and propagates the changes marking nodes with the possible states. This process is similar to A* or Dijkstra's however computes the path backwards from goal to start. D*'s main advantage over traditional search algorithms is during the search process it if an obstruction is detected all affected nodes are placed on the open list marked as *raise*. This then forces a check on adjacent neighbours on whether a *lower* distance can be found. This forces the searcher to move in "waves" where if an obstacle is encountered adjacent search opportunities are explored.

# IDA*
IDA* is a informed variant of [[Graph Searches#Iterative Deepening|Iterative Deepening]] that rather than using the depth to restrict the searches uses a heuristics $w(u,v) + h(n)$. This modification allows for its application within [[Pathfinding|shortest path]] algorithms as to find an efficient result. The main advantage of this algorithm over [[A-Star|A*]] is its limited memory usage but at the cost of repeating the exploration of some nodes. Implementation of this algorithm is similar to IDA however with the addition of a function call in the $\text{DLS}$ algorithm which checks if the bound is lower than the search cost. Additionally the loop value is no longer restricted to $[0,n]\in\mathbb{Z}$ but rather $[0,n]\in\mathbb{R}$.

# Jump Point
Jump point search is an optimization of A* for uniform-cost graphs. This is done through decreasing the selection space of A* through graph pruning.
