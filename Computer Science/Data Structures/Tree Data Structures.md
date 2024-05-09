A tree data structure is a data structure which stores a series of data through nodes that contain a value, and a list of connected nodes. Based on [[Graph Theory]] trees these structures have no cycles, making [[Recursion|recursive]] operations useful for tree traversal. There are many different implementations of trees that all attempt to maintain their own set of rules, and functions.

# Binary Tree
The most common tree data structure is a Binary Tree, also called a *binary search tree*. The main restriction of a binary tree is that it has a **left** and **right** field for adjacent nodes. Binary trees also occasionally have a **parent** $p$. This means all nodes have connections of $k \leq 2$. A binary tree is considered **rooted**, as it has a single root node. This means a full binary tree is either a single vertex, or a tree whose root node has two subtrees. Types of binary trees include:
- **Full** binary trees have either 0 or 2 children each. A full binary tree has between $2h+1 \leq n \leq 2^{h+1}-1$ nodes, or given leaf nodes $l$, $n=2l-1$ nodes.
- **Perfect** binary trees have all interior nodes with the same depth or level filled. The number of leaf nodes in a perfect tree is $(n+1)/2$.
- **Complete** binary trees have all nodes at that level filled. This means it has $2^h$ total nodes.
- **Balanced** binary trees if the left and right subtrees height doesn't differ by more than 1. The height of a balanced tree can be found as $h = \log_2{l} + 1=\log_2{n+1}$.

## Operations
Binary trees have the following common operations:
- **Insertion**, adds a node to the tree, usually specifying a parent node. A leaf node insertion simply assigns a leaf node, while an internal node insertion has to replace the previous pointer with a new one. The average time complexity of this operation is $\Theta(\log n)$, with a worst case of $O(n)$.
- **Traversal** can either take a [[Graph Searches#Depth-First Search|depth-first]] or [[Graph Searches#Breadth-First Search|breadth-first]] approach to traversal.
- **Deletion**, the deletion process usually operates either on leaf nodes, or cases where there are children reassigns the pointers. Different implementations account for cases with two children. Deletion has the same time complexity as insertion.
- **Transplant** is an operation which replaces one subtree with another subtree.

## Implementation
Binary trees can be implemented through the use of [[Object Orientated Programming|OOP]] using classes, type declarations, pointers or arrays. The type or class declaration usually declares a type `type Node = {value:any, left:Node, right:Node}`. An array can be used if the tree is complete. This method finds the children at the indices $2i+1$ for the left child, and $2i+2$ for the right. Thus, the parent can be found as $\frac{i-1}{2}$.

# Binomial Tree
A binomial tree is another tree implementation however each node holds a list of nodes. These trees are then defined recursively where a tree of rank 0 $B_0$ has only 1 node while a tree $B_k$ of rank $k$ is defined as two previous trees $B_{k-1}$ merged together with the root pointing to the second tree additionally. Another view is that the new root holds all previous ranks. Binomial trees are found within [[Heap Structures#Binomial|binomial heaps]].

## Implementation
The basic approach for a binomial tree is for each node to hold a list of children. This enables node of greater rank to hold the required amount of nodes. The advantage is the simplicity however requires extra memory as a [[Data Structures#Linked List|linked list]] or [[Data Structures#Array|dynamic array]] is required to store the nodes. Another implementation keeps a binary tree which points to a child and sibling.
