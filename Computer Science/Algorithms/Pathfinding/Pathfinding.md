Pathfinding algorithms are used to find the optimal routes between points. This usually involves a minimisation of the distance to get between nodes. These are a closely related to the **shortest-distance** problem found within graph theory. Formally, using a [[Graph Theory|graph]] representation $G=(V,E)$, with a weight function $w:E\to\mathbb{R}$ where $w(v_0,v_1)$, the shortest path can be found as a path $p = \{ p_0, p_1, \dots, p_n \}$, that is optimised such that: 
$$w(p)=\sum_{i=1}^n w(v_{i-1},v_i)$$
The result of this algorithm finds the shortest path from $u$ to $v$ as: $$\delta(u,v)=\begin{cases}
\min\{w(p):u \leadsto^p v \} &\text{if path $u$ to $v$ exists}\\
\infty &\text{otherwise}
\end{cases}$$
# Variants
There are a multiple types of pathfinding problems which relate to each other. These all involve one agent.
- **Single-source** which finds the shortest path from a starting node to all possible other nodes.
- **Single-destination** where the goal is to find the shortest path to a particular destination given a start from any vertices. This is just a reverse of the single-source shortest-path.
- **Single-pair** finds the shortest path between a pair of vertices.
- **All-pairs shortest-paths** finds the shortest path between all vertices.

In addition to these variants there are also some common constraints that can be put on the problem definition. The normal assumption for this problem is no negative weights or cycles. This assumption stops certain algorithms such as Dijkstra's from breaking.

**Unweight shortest path** is a variant where the edges are unweighted. This can be seen in **uniform grid** representations of pathfinding problem where the graph is nodes connected on all 4, or 8 in the case of diagonals. The approach to solving these can either use basic [[Graph Searches|graph searches]] such as BFS or iterative deepening, or heuristic driven algorithms such as A*.

**[[Multi-Agent Pathfinding]]** is an expansion upon pathfinding problems that consider multiple agents planning paths.

# Motion Planning
**Motion planning** is an expansion upon [[Pathfinding]] that introduces the idea that vertex, and agents occupy a certain shape, volume and space. These agents also have to accelerate and take in account current motion. 

## Collision Avoidance
Collision avoidance is the process of ensuring that the given size of an agent doesn't conflict with the pathfinding environment. This can be done through a variety of ways. A basic way of ensuring collision avoidance is pruning the environment representation as to ensure no collisions. In the case of multiple different agents different versions of the map could be held. Precomputing clearance values can also be done.

## Turn Constraints
Turn constraints are an aspect of motion planning where the transition function and states of a node are now a three tuple equal to $(x,y,\theta)$, where $\theta$ is an angle. This introduction of an angle has an impact on possible turning actions.

# Approaches
There are a variety of different approaches to solving pathfinding problems. These include through the use of algorithmic paradigms such as [[DP Pathfinding Algorithms|dynamic programming]], or families of algorithms such as [[A-Star]].

**Bi-directional** searching algorithms are an approach to solving single pair pathfinding that searches from both sides as to find the shortest path. In many cases the bidirectional approach is considered faster as it ignores branches that lack a direct route to the path. For example a basic BFS search has a time complexity of $O(b^n)$ where $b$ is the branching factor while a bi-directional implementation decreases this to $O(n^\frac{n}{2})$. The best cases for bi-directional algorithms usually follow cases where an initial and end state are defined and the branching factor of both sides is the same.
# Common Procedures
Many algorithms use procedures to solve pathfinding problems. These include operations to compare quality of shortest paths, initialization of the problem, and finding the path once a solution is found.

## Relaxation
A common procedure many shortest-path algorithms use is a relax operation. The goal of this operation is to assign a new predecessor $\pi$ due to a lower weighted path being found.
```pseudo
	\begin{algorithm}
	\caption{relax(u,v,h(v))}
	\begin{algorithmic}
		\IF{$v.d > u.d + w(u,v)$}
			\STATE $v.d \gets u.d + w(u,v)+h(v)$
		\ENDIF
	\end{algorithmic}
	\end{algorithm} 
```
Where $h(v)$ is a possible heuristic function that can be used to improve search quality.

## Initialization
A single-source problem can be initialised by the assignment of all vertices to a distance equal to infinity with no predecessors. This process enables relaxation operations to be done on later algorithms. This follows the basic pseudocode:
```pseudo
	\begin{algorithm}
	\caption{InitSingleSource(G,s)}
	\begin{algorithmic}
		\FOR{$v \in G.V$}
			\STATE $v.d \gets \infty$
			\STATE $v.\pi \gets \nil$
		\ENDFOR
		\STATE $s.d\gets 0$
	\end{algorithmic}
	\end{algorithm} 
```
This approach works on cases where graphs have a list of vertex objects. In the case a locally stored list is being used just create an array with distance set to infinity for all nodes, with the first node having $0$. 

## Get Path
In cases where the algorithm is required to return a path rather than just a Boolean value, a path can be constructed through the use of a [[Algorithmic Paradigms#Backtracking|backtracking]] algorithm that follows the predecessor list until finding the start.
```pseudo
	\begin{algorithm}
	\caption{GetPath($s,u,pred[1..n]$)}
	\begin{algorithmic}
		\State $path \gets [u]$
		\While{$u \neq s$}
			\State $path.$\Call{append}{$pred[u]$}
			\State $u \gets pred[u]$
		\EndWhile
		\Return \Call{reverse}{$path$}
	\end{algorithmic}
	\end{algorithm}
```
