Flow networks are a [[Graph Theory|network]] of nodes that have a single source vertex, and a single target or sink vertex. Furthermore, each edge has a non-negative capacity that gives the amount of flow that an edge can carry. The set of all incoming edges to a vertex $v$ is considered $E_{in}(v)$, and outgoing edges as $E_{out}(v)$. The source vertex has $E_{in}(s)=0$, and the sink has $E_{out}(s)=0$. A flow network must maintain two properties:
- **Capacity Constraint** which states that for each edge the flow is denoted as $f(e)$, and has a bounded capacity of its edge $0 \leq f(e) \leq c(e)$ where $c(e)$ is capacity of the edge.
- **Flow conservation** which states that any vertex $v$ has total flow coming in as it does out. Formally this can be expressed as:$$
\sum_{\forall e_{in}\in E_{in}(v)}f(e_{in})=\sum_{\forall e_{out}\in E_{out}(v)}f(e_{out})
$$The main advantages of network flow algorithms is their generalised approach to solving [[Combinatorial Algorithms|combinatorial optimization problems]]. Their efficiency over other approaches enables a representation of the problem which can be solved by max flow networks.

# Maximum Flow Problem
The **maximum flow problem** states that given the total flow out of the source vertex what is the maximum value that can can be sent from $s$ to $t$ without violating the properties of a flow network. This means the value can be given by:
$$|f|= \sum_{v\in V} f(s,v)$$
Where the problem finds $\max |f|$ to get the maximum flow of the network.

## Ford-Fulkerson Method
The Ford-Fulkerson method is an algorithm which solves the maximum flow problem. The method relies of a **residual network** which for every edge found on the original network $u \to v$ add two edges, the **forward/residual edge** and the **backward/reversible flow edge**. The residual edge is in the same direction as $u \to v$ with the remaining capacity. The reversible edge has the opposite direction $v\to u$ with weight equal to the current flow of $u\to v$. This allows for the algorithm to use this edge to remove flow added given cases where a less optimal flow was pushed.
```pseudo
	\begin{algorithm}
	\caption{MaxFlow(G=(V,E),s,t)}
	\begin{algorithmic}
		\STATE Set initial flow $f$ to $0$ on all edges
		\WHILE{there exists an augmenting path $p$ in the residual network $G_f$}
			\STATE Augment the flow $f$ along the augmenting path $p$
		\ENDWHILE
		\RETURN $f$
	\end{algorithmic}
	\end{algorithm} 
```

Cost of finding an augmenting path depends on the algorithm used, with DFS resulting in a complexity of $O(|E|\cdot |f_{max}|$ as the worst case each augmentation only increases the flow by one unit. This means the algorithm is heavily dependent on the quality of augmented path. In the case of using [[Graph Searches#Breadth-First Search|BFS]] the shortest augmenting path is found which will result in $O(|V||E|^2)$ time complexity. This algorithm is commonly called **Edmond-Karp**. Another approach is using a [[Graph Spanning Tree Algorithm|maximum spanning tree]] to find the augmenting path. This is called the **fattest augmenting path** and results in a better runtime than Edmond Karp equal to:
$$O\Big( |E|^2\log (|V|) \log \Big( |E|\max_{u,v\in V} c(u,v) \Big) \Big)$$

# Minimum Cut Problem
The minimum flow problem states that given a flow network find a set of edges of minimum total capacity that if removed would disconnect the start from the target. Therefore, a **cut** is defined as $C=(S,T)$ where the partition of vertices $V$ into two disjoin subsets $S$ and $T$ such that $s \in S$ and $t \in T$. The capacity of the cut $C$ is defined to be the total capacity of all edges that begin in $S$ and end in $T$, formally expressed as:
$$c(S,T)=\sum_{u\in S}\sum_{v\in T} c(u,v)$$
Where $c(u,v)=0$ if there does not exist an edge. The minimum cut problem attempts to find $\min c(S,T)$. The minimum cut problem can use the Min-cut Max-Flow theorem to find the minimum cut for any graph using Ford-Fulkerson.

# Min-cut Max-Flow Theorem
The **min-cut max-flow theorem** states that the maximum value of the $s-t$ flow of the network in $G$ is equal to the minimum capacity $s-t$ cut in $G$. Mathematically:
$$\max_f |f| = \min_{(S,T)}c(S,T)$$
Informally this relation is proven by the idea that the net amount of flow that crosses the cut must be equal to the value of the flow $|f|$. Therefore, by finding the maximum flow the minimum amount of edges weight are used to transfer the flow.

This idea also proves the correctness of Ford-Fulkerson as the algorithm terminates when there are no augmenting paths left. Since when there are no paths from $s-t$ that flow across the cut $c(S,T)$ then the flow across the cut must be equal to the capacity of the cut. This therefore implies that the flow is at its maximum.

# Maximum Bipartite Matching
The maximum bipartite matching problem functions on a bipartite graph $G=(V,E)$ with $V=L\cup R$ where a matching is a subset $M$ of the edges $E$ such that no vertex $v \in V$ is incident multiple edges in $M$. The problem attempts to maximize these matchings. If $|L|=|R|$ and the matching $|M|=|L|$ then the matching is perfect.

This problem is solved through creating a maximum flow network where the matches are represented as units of flow. The graph assigns a source $s$ and connects all $L$ nodes, while also adding a sink $t$ that has all $R$ connected to it. Edges are then connected from $s$ to $t$ with a flow of $1$ assigned to each edge.

# Circulation with Demands
The basic circulation with demands problem states that given a directed graph $G=(V,E)$ denote the capacity of an edge by $c(u,v)$ where associated with each vertex $u\in V$ there is an integer $d_u$ that denotes its demand. A circulation with demands is a function $f$ that maps each pair of vertices to a non-negative real number that satisfies the constraints:
- **Capacity constraint**, where the flow along an edge must no exceed the capacity of an edge. Mathematically seen as $0 \leq f(u,v)\leq c(u,v)$.
- **Demand constraint** which states the relation below, where $f(u,v)=0$ if there is no edge:
$$\sum_{v\in V} f(v,u)-\sum_{v\in V} f(u,v)=d_u$$
To solve the problem add a start node $s$ to be connected to all nodes with $d_u<0$, with edges values equal to $d_u$. Then add a sink $t$ to each node where $d_u>0$. These can be called the super-sink and super-start. After this simply run the maximum flow algorithm to find a feasible solution.

This problem can be further expanded in the **circulation with demands and lower bounds problem**, where the capacity constraint is now restricted to a lower bound and thus $\ell(u,v)\leq f(u,v) \leq c(u,v)$. To solve this problem first find $f^\ell(u,v)=\ell(u,v)$ for each edge. After which there exists a flow $f^*$ such that $f=f^\ell+f^*$ with the same demands. This flow can be found by creating a new graph $G^*$ where vertices are the same as $G$ but have a demand $d^*_u=d_u-\sum_{v\in V}f^\ell(v,u)+\sum_{v\in V}f^\ell(u,v)$. Additional the edges are the same but now have a capacity $c^*(u,v)=c(u,v)-\ell(u,v)$ and no lower bounds. This allows the problem to be solved similar to a normal circulation problem.
