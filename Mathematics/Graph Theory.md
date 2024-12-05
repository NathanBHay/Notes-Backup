Graph theory is a branch of mathematics that deal with the [[Abstract Datatypes|abstract datatype]] of the graph. These graphs are defined through **nodes**/**vertices** and **edges** which connect to the nodes. These graphs normally are defined through a [[Set Theory|set]] of edges, and a set of vertices. They are used to represent the relation between entities within many fields.

There are multiple types of graphs which commonly occur, those being:
- **Simple Graph**, also just called a graph, can have one edge between nodes.
- **Multigraph** which can have multiple edges between nodes.
- **Directed Graph** where edges have a direction.
- **Hypergraph** has edges that connect multiple nodes.

# Walk
A walk is a sequence of vertices that are found within a graph that map a path from the start to a end. There are multiple walk variants, those being:
- **Trail** is a walk that traverses each edge at most once.
- **Path** is a series of vertices with no repeats.
- **Cycle** is a path that ends at the same point.
- **Hamiltonian cycle** is a cycle that visits all vertices exactly once.
- **Euler Trail** is a trail that uses every edge exactly once. A graph with $>2$ odd degree vertices has no Euler trail. A graph has to have only even degrees to have closed Euler trail. However, a connected graph with no odd degree has a closed Euler graph.

# Graph Properties
There are many common properties which are found within graphs. These are:
- **Completeness** which is when all nodes have an edge between each other.
- **Subgraphs** are defined as graphs whose vertices and edges are within a graph.
- **Bipartite** graphs are ones that can be divided into two sections. A graph is only bipartite if no odd-length cycles exists within the subgraphs.
- **Connectivity** is defined as having a subgraph.

The **degree** of a node can be found as the amount of outgoing connections at a point. The sum of all degree equals twice the amount of edges.

A **bridge** is a single edge that if deleted it will become disconnected.

# Trees
A tree is a connected graph that has no subgraph that is a cycle. The amount of edges for a tree can be calculated as 1 minus the total vertices. The **spanning tree** of a graph is a subgraph that is a tree. Any connected graph will contain a spanning tree. The **minimum spanning tree** is the spanning tree found within a graph that has the minimum total weights

# Graph Density
One of the big factors of graphs is the density. For simple graphs the maximum number of possible directed edges is $|V|^2$. For an undirected graph it is ${|V|+1} \choose 2$. If loops aren't allowed for these numbers minus one from $|V|$. A graph can be considered **dense** if $|E| \approx |V|^2$ meaning there are a lot of edges. A graph is sparse if $|E| \ll |V|^2$, meaning there is a small number of edges.

# Graph Implementations
There are a variety of common strategies for implementing a graph within computer science. The most common approaches are adjacency lists, adjacency matrices, and edge lists.

## Edge List
The edge list is the simplest approach however is very flawed. While it does allow all edges to be stored within one list that results in a space complexity of $O(|E|)$ it suffers from the fact that the nodes are unknown, and lookup of edges takes $O(|E|)$. This means finding the nodes in the graph will take $O(|E|)$, and won't find disconnected nodes.

## Adjacency List
An adjacency list stores each edge within a list of edges for each respective node. This makes lookup of edges take $O(1)$. This results in $O(|V|+|E|)$ space complexity which is much small for sparse graphs, and similar to an adjacency matrix for dense.

## Adjacency Matrix
An adjacency [[Linear Algebra|matrix]] is a matrix which contains all nodes and there edges. This is represented by nodes representing the rows and columns. These matrices can contain 0 or 1 to represent a connection, or a weight. The amount of walks between two vertices can be found from the $k^{th}$ power of the adjacency matrix.
