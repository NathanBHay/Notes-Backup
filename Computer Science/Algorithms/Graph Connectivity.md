Graph connectivity is a problem which attempts to find all the connected nodes within a [[Graph Theory|graph]]. The connectivity problem can be further expanded given extra conditions such as the ability for graphs to change.

# Basic Graph Connectivity
Basic graph connectivity simply has the goal to check if nodes are connected. The usual approach for this is to use a [[Graph Searches|graph searching algorithm]] to find all nodes connected to a certain node. This can be further expanded by creating a component that stores all connected vertices. Usually done through the use of an array that stores what component each vertex is in. By doing this a simple equality check can be used to see if two vertices are connected.

# Incremental Connectivity
Incremental Connectivity problems deal with graphs that can have edges added to them. This can be solved simply by recomputing the graph connectivity each addition, however would be needlessly expensive. A better method is the use of a [[Disjoint-Set Structure|disjoint-set data structure]]

# Dynamic Connectivity
Dynamic connectivity is used for cases where nodes and edges can be both added and deleted.
