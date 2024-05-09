Based on the principles of [[Graph Theory|graph theory]], a graph searching algorithm is similar to a [[Searching Algorithms|list searching algorithm]] however instead uses a graph [[Abstract Datatypes|abstract datatype]]. These searching algorithms are at the center of many other graphing algorithms due to the need to know if a graph contains an item. The following are a series of algorithms which solve the graph searching problem.

| Criterion | Breadth-First | Uniform Cost| Depth-First | Depth-Limited | Iterative Deepening | Bidirectional |
| --- | --- | --- | --- | --- | --- | --- |
| Complete | Yes$^a$ | Yes$^{a,b}$ | No | No | Yes$^a$ | Yes$^{a,d}$ |
| Optimal | Yes$^c$ | Yes | No | No | Yes$^c$ | Yes$^{c,d}$ |
| Time | $O(b^d)$ | $O(b^{1+\lfloor C^*/\epsilon\rfloor})$ | $O(b^m)$ | $O(b^\ell)$ | $O(b^d)$ | $O(b^{d/2})$ |
| Space | $O(b^d)$ | $O(b^{1+\lfloor C^*/\epsilon\rfloor})$ | $O(bm)$ | $O(b\ell)$ | $O(bd)$ | $O(b^{d/2})$ |
Where $b$ is the branching factor, $d$ is the depth of the shallowest solution, $m$ is the maximum depth of the tree, $\ell$ is the depth limit. The superscript caveats follow: $^a$ complete if $b$ is finite, $^b$ complete if step costs $\geq\epsilon$ for positive $\epsilon$, $^c$ optimal if step costs are identical, $^d$ if both directions use breadth-first search.

# Breadth-First Search
Breadth-First Search is an algorithm which searches all adjacent nodes of a graph by generating a breath-first tree where all current adjacent nodes to the tree are added to the tree. The breadth first search algorithm has a basic pseudocode of:
```pseudo
	\begin{algorithm}
	\caption{BFS(G,v)}
	\begin{algorithmic}
		\STATE $Q \gets$ \CALL{Queue}{$\emptyset$}
		\STATE $Q.$\CALL{enqueue}{$v$}
			\WHILE{$S \neq \emptyset$}
				\STATE $v \gets S.$\CALL{dequeue}{}
				\IF{$v.visited =$ \FALSE}
					\STATE $v.visited \gets$ \TRUE
					\FOR{$u \in v.adjacent$}
						\STATE $v.$\CALL{enqueue}{$u$}
					\ENDFOR
				\ENDIF
			\ENDWHILE
	\end{algorithmic}
	\end{algorithm} 
```

The algorithm has a linear time complexity of $O(v+e)$, where $v$ is the amount of vertices and $e$ is edges. Given edge checking is constant. Due to the fact it needs to keep track of discovered nodes the algorithm has a linear space complexity. This algorithm can also be represented as having a complexity of $O(b^d)$, where $b$ is the branching factor and $d$ is the length of the path between the start and goal. This algorithm is commonly implemented with a queue that allows for the nodes to be searched. Modifications of this algorithm can be used to create a breadth-first tree that can be used within other problems.

# Uniform-Cost Search
Uniform-cost search is a search algorithm which can be used on graphs with a uniform cost. It functions similar to BFS but rather than expanding the shallowest node it expands the one with the lowest cost. This 
```pseudo
	\begin{algorithm}
	\caption{UniformCostSearch(G,v)}
	\begin{algorithmic}
		\State $frontier \gets$ \Call{PQueue}{$(\emptyset)$}
		\State $visited \gets \emptyset$
		\State $frontier.$\Call{enqueue}{$(v,0)$}
		\While{$frontier \neq \emptyset$}
			\STATE $v \gets S.$\CALL{dequeue}{}
				\IF{$visited[v] =$ \FALSE}
					\STATE $visited[v] \gets$ \TRUE
					\FOR{$u \in v.adjacent$}
						\If{$u \notin frontier$}
							\State $frontier.$\CALL{enqueue}{$u$}
						\Elif{Path Cost $ < frontier$.\Call{get}{(u)}}
							\State $frontier.$\Call{decreasekey}{($u,cost)$}
						\EndIf
					\ENDFOR
				\ENDIF
		\EndWhile
	\end{algorithmic}
	\end{algorithm}
```
Due to the requirement of update operation/decrease key as well as a membership check the priority queue might need to have expanded capabilities that allows the use of hashing. Uniform cost search has a complexity bound by the cost of the optimal solution $C*$. As such the worst-case time and space complexity can be found as $O(b^{1+\lfloor C^*/\epsilon\rfloor})$ which is greater than BFS. This is as the algorithm searches uniformly possibly avoiding larger steps that may be more efficient. 

# Depth-First Search
Depth-First Search is an algorithm which searches one adjacent node, making that node the new node to search from. This means the algorithm searches deeper rather than wider like breadth-first search. The algorithm can be implemented either through a stack approach such as below:
```pseudo
	\begin{algorithm}
	\caption{IterativeDFS(G,v)}
	\begin{algorithmic}
		\STATE $S \gets$ \CALL{Stack}{$\emptyset$}
		\STATE $S.$\CALL{push}{v}
		\WHILE{$S \neq \emptyset$}
			\STATE $v \gets S.$\CALL{pop}{}
			\IF{$v.visited =$ \FALSE}
				\STATE $v.visited \gets$ \TRUE
				\FOR{$u \in v.adjacent$}
					\STATE $S.$\CALL{push}{$u$}
				\ENDFOR
			\ENDIF
		\ENDWHILE
	\end{algorithmic}
	\end{algorithm} 
```

The algorithm can also be implemented recursively such as the pseudocode:
```pseudo
	\begin{algorithm}
	\caption{RecursiveDFS(G,v)}
	\begin{algorithmic}
		\STATE $v.visited \gets$ \TRUE
		\FOR{$u \in v.adjacent$}
			\IF{$u.visited =$ \FALSE}
				\STATE \CALL{DFS}{G,u}
			\ENDIF
		\ENDFOR
	\end{algorithmic}
	\end{algorithm} 
```

The algorithm has a linear time complexity of $O(v+e)$, where $v$ is the amount of vertices. Due to the fact it needs to keep track of discovered nodes the algorithm has a linear space complexity. The complexity can also be represented as $O(bd)$ where $b$ is branching factor and $d$ is distance between start and goal. This can also be seen as the longest path length searched. The algorithm commonly is implemented with a stack that allows for the nodes to be searched.

## Applications
A common application of graph traversal is finding cycles. A cycle can be found by performing a depth first search that upon iterating over a already found edge returns true for the cycle. Another application is topological ordering of a directed acyclic graph. This can be used to order vertices by keeping a value of distance for each node.

## Depth Limited Search
Depth limited search is a type of depth first search that has a declared bound for how far it can travel. This allows it to explore graphs in which you know the distance from solutions faster. This algorithm has a complexity of $O(b^\ell)$, where $\ell$ is the depth limit assigned.

# Iterative Deepening 
Iterative Deepening is a more space efficient alternative to BFS and speed efficient alternative to DFS that uses multiple depth-bounded searchers to find a path. This is done by running a depth first search of depth $n$ and if no path exists running a new depth first search of depth $n+1$. This process functions similar to a BFS however lacks the space complexity as only the currently DFS path is being held. This algorithm has a time complexity of $O(b^d)$, where $b$ is branching factor and $d$ is the depth of the shallowest solution. It's has space complexity of $O(d)$. The algorithm has an implementation of:
```pseudo
	\begin{algorithm}
	\caption{IterativeDeepening($G,v$)}
	\begin{algorithmic}
		\For{$depth$ \To $\infty$}
			\State $found, remaining \to$ \Call{DLS}{$v,depth$}
			\If{$found$}
				\Return \True
			\Elif{\Not $remaining$}
				\Return \False
			\EndIf
		\EndFor
	\end{algorithmic}
	\end{algorithm}
```

Where $\text{DLS}$ is a depth limited depth first search. This is usually implemented with an additional clause in depth first search which checks if $depth=0$.
