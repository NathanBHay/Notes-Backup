A double ended heap is a [[Data Structures|data structure]] used to implement a double ended [[Abstract Datatypes#Priority Queue|priority queue]] done with a [[Heap Structures|heap data structure]]. Due to this consideration a DEPQ usually has all the basic heap operations with the addition of its inverse extract minimum or extract maximum. Due to these changes a meld operation becomes difficult to implement. In general all double ended heap schemes have a insertion and deletion of $O(\log n)$ complexity.

# Symmetric Min-Max Heap
The simplest implementation of a double-ended heap comes in the form of the symmetric min-max heap. This heap similar to a [[Heap Structures#Binary Heap|binary heap]] as it uses an all most [[Tree Data Structures#Binary Tree|complete binary tree]] that keeps the minimum element of the subtree as the left child and the maximum element of the subtree as the right, with the root being a null value. Additionally every node in the heap needs to follow:
- **Property 1** every node $x$ that has a right sibling, it needs to be less than or equal to the right sibling of $x$.
- **Property 2** every node $x$ that has a grandparent needs the element in the left child of the grandparent to be greater than or equal to it.
- **Property 3** every node $x$ that has a grandparent needs the right child of the grandparent to be greater than or equal to it.

These additions result in a data structure which upon insertion attempts to maintain all three properties as to ensure safe insertion. In general all operations have a $O(\log n)$ complexity.

# Interval Heaps
Interval, pair heaps, or twin heaps are similar data structures that keep nodes with a minimum and maximum value. The heap is similar to a binary heap except each node depicts an interval where the interval of the root $[a,b]$ is the larger interval than its child $[c,d]$, thus $a\leq c \leq d \leq b$. This results in an insertion process where an odd numbered element is inserted into the last node, successively comparing with previous node elements to test if it is outside the interval. For even number of elements this insertion process pairs the last node with only one element with the even element. Comparing to find its place within the heap.

# Min-Max Heap
Min-Max heaps are another form of binary heap that uniquely alternates between min and maximum levels. This means every node is either smaller or bigger than its previous nodes, with a root being its minimum element when $n>1$. These two properties are called the min-node property, and the max-node property.

**Insertion** follows a process where it checks its parent element, if that element is equal to the new element it is placed into the heap, if it is less than and its parent is a min-node the min-node property is violated and a **trickle-up** process is called. This swaps the nodes and then continues to check if the grandparent of the node is less, and if so swaps it. The inverse of this process is present for if a node parent is less than the new element.

