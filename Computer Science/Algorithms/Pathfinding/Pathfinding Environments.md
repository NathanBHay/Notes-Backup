An important aspect of constructing [[Pathfinding|pathfinding]] problems is the data structure used to represent the environment. The standard approach is to discretise the environment. The process of creating a discrete data structure causes changes in the space and time complexity of running certain algorithms. As well as changing the depending on the ability for the graph to find an optimal result.

| Type | Creation | Insertion | Update | Search | Complete | Optimal |
| --- | --- | --- | --- | --- | --- | --- |
| Grids | $O(n)$ | $O(1)$ | $O(1)$ | $O(\vert V\vert\log\vert V\vert+\vert E\vert\log\vert V\vert)$ | ?? | ?? |
| Vis Graphs | $O(V^2)$ | $O(V)$ | $O(V^2)$ | $O(\vert V\vert\log\vert V\vert+\vert E\vert\log\vert V\vert)$ | Yes | Yes |
| Nav Meshes | $O(n\log n)$ | $O(\log\vert V\vert)$ | $\Omega(\log\vert V\vert)$ - $O(\vert V\vert)$ | Mesh Type | Yes | No |
Where ?? means that it is dependent on the obstacles and grid resolution. The search of visibility grids also depends on branching factor $O(|E|)=|V|^2$.
# Grids
A common approach is to discretise the environment into a grid of uniform shapes. The most common shapes used for uniform grids are squares, hexagons, and triangles. These grids can be created in $O(n)$, with updates and insertions of $O(1)$. The A* search on the grid can be found as $O(|V|\log |V| + |E|\log |V|)$ depending on the obstacles. 

When constructing a grid choosing what to turn into nodes and edges is important. In general there are three ways to construct a graph from a grid. These are to make the node the center of the shape, the borders of the shape or the intersection of the borders.

There are a variety of approaches to constructing a grid. These include:
- **[[Data Structures#Array|Arrays]]** or lists are the most basic approach and can be constructed from a series of Boolean array or arrays. These have a fast access time at the cost of a sizeable space complexity.
- **[[Hashtables|Hashtables]]** or [[Set Theory|Hash Sets]] store all the grid's obstacles in a dictionary. This is space efficient as the hash-table only ever grows to half the size of the actual grid (as you can flip the obstacles) however suffers from collisions caused by the hashing function resulting in slightly slower times for grids with many obstacles.
- **[[Bit Fields]]** which allow for grids to be constructed as a series of bits held within an array of binary numbers. This approach is more space efficient than arrays while also having similar speed as only bit manipulation operations are used.

# Visibility Graphs
Visibility grids which are graphs which have nodes at corners in the environments and edges which connect to visible corners. This can be further improved to only include optimal paths through pruning. These can be created in $O(V^2)$ where $V$ is the amount of corners in the environment. 

# Navigation Meshes
Navigation meshes are a common approach used in video-games which divides the environments into merging triangular geometry. This breaks the map into large polygons. To create a mesh there are three techniques:
- **Adjacency graphs** where the polygon's face represents the node, and edges are distance between adjacent face.
- **Door graphs** where each node is a polygon border, and all edges are borders of the face.
- **Directly use the mesh** rather than creating a graph.
