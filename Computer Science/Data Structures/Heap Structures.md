A heap is a data structure based upon a [[Graph Theory#Tree|tree]] that satisfies the **heap property**. This property in the case of a max heap states that each child element is less than the parent. A minimum heap is similar however is restricted to the parent being smaller. The heap is partially ordered due to the property but lacks actual sorting. The most common use of a heap is a priority queue. This works by storing the priority of an element in the heap which allows lookup of an element given that priority.

The most common heap operations are:
- **Heapify** is the operation which is used to maintain the heap property.
- **Insert** is used to add a item to the heap.
- **Delete** which removes an element from the heap.
- **Create** which creates a heap from a list.
- **Find-Max** (or find-min) that finds the maximum item of the heap.
- **Extract-Max** (or extract-min) removes the maximum item from the heap and calls a heapify to ensure the heap constraint is maintained.
- **Merge** which joins two heaps together to create a valid heap.
- **Decrease-key** (or decrease-key) which is used to update a key within the heap.

| Operation | find-min | extract-min | insert | decrease-key | meld |
| --- | --- | --- | --- | --- | --- |
| Binary | $\Theta(1)$ | $\Theta(\log n)$ | $O(\log n)$ | $O(\log n)$ | $\Theta(n)$
| Leftist | $\Theta(1)$ | $\Theta(\log n)$ | $\Theta(\log n)$ | $O(\log n)$ | $\Theta(\log n)$
| Skew | $O(1)$ | $O(\log_\phi n)^*$ | $O(\log_\phi n)^*$ | $O(\log_\phi n)^*$ | $O(\log_\phi n)^*$
| Binomial | $\Theta(1)$ | $\Theta(\log n)$ | $\Theta(1)^*$ | $\Theta(\log n)$ | $O(\log n)^*$
| Fibonacci | $\Theta(1)$ | $O(\log n)^*$ | $\Theta(1)$ | $\Theta(1)^*$ | $\Theta(1)$
| Pairing | $\Theta(1)$ | $O(\log n)^*$ | $\Theta(1)$ | $o(\log n)^*$ | $\Theta(1)$
Where $^*$ denotes amortized complexity.

# Binary Heap
A binary heap is the most common form of a heap and follows a nearly complete [[Tree Data Structures#Binary Tree|binary tree]]. The most common implementation features an array that stores all elements. To find the parent of any element simply find $|\frac{i}{2}|$. The left child can be found as $2i$, while the right child can be found as $2i+1$ for 1 indexed structures. For 0 index add another one to both equations.

The most basic heap operation is the heapify operation. For a binary heap this operation runs in $O(\log n)$. To implement a heapify operation for a binary heap follow the below process:
```pseudo
	\begin{algorithm}
	\caption{Max-Heapify(A,i)}
	\begin{algorithmic}
		\STATE $l \gets$ \CALL{Left}{i}
		\STATE $r \gets$ \CALL{Right}{i}
		\STATE $largest \gets i$
		\IF{$l \leq A.size$ \AND $A[l] > A[i]$}
			\STATE $largest \gets l$
		\ELIF{$r \leq A.size$ \AND $A[r] > A[i]$}
			\STATE $largest \gets r$
		\ENDIF
		\IF{$largest \neq i$}
			\STATE \CALL{SWAP}{A[i],A[largest]}
			\STATE \CALL{Max-Heapify}{A,largest}
		\ENDIF
	\end{algorithmic}
	\end{algorithm} 
```
To switch this to a min-heapify switch the comparison operation to $A[\dots]<A[i]$. Using the heapify operation a heap can be built from an array. This operation is done in $O(n \log n)$, and follows the pseudocode:
```pseudo
	\begin{algorithm}
	\caption{Build-Max-Heap($A$)}
	\begin{algorithmic}
		\For{$i\gets \lfloor A.length/2 \rfloor$ \To $0 \step -1$}
			\State \Call{Max-Heapify}{$A,i$}
		\EndFor
	\end{algorithmic}
	\end{algorithm}
```
Another common operation found within a binary heap is the increase key operation. **Increase-key** for a binary heap has a time complexity of $O(\log n)$ and follows a basic process of:
```pseudo
	\begin{algorithm}
	\caption{Increase-Key($A,i,key$)}
	\begin{algorithmic}
		\If{$key < A[i]$}
			\Print error new key is smaller than current key
		\EndIf
		\State $A[i] \gets key$
		\While{$i>1$ \AND $A[$\Call{parent}{$i$}$]<A[i]$}
			\State \Call{swap}{$A[i],A[$ \Call{parent}{$i$}$]$}
			\State $i \gets$ \Call{parent}{$i$}
		\EndWhile
	\end{algorithmic}
	\end{algorithm}
```
Insertion with increase key follows a process of attaching a node to the end. This is then increase keyed as to correctly insert it into the right position.

# Leftist Trees
A leftist tree or leftist heap is another data structure which implements priority queues. Leftist heaps maintain the **heap invariant**, while also ensuring a binary tree invariant where the smallest of the two children is put on the left, and the larger on the right. The main advantage of leftist trees is the faster merge operation over binary heaps.

There are to types of leftist trees these are height-biased, and weight-biased. These store different values within the node that are used to ensure a tree that skews in a certain direction. Weight-biased perform better in practice however have a deletion of $\Theta(n)$ rather than the $O(1)$ of heigh-biased.

## Height Biased
Height biased leftist trees (HBLT's) store a **s-value** or rank that is the distance from a null pointer. Mathematically this is formalised as the distance from external nodes where **external nodes** are the set of nodes outside of the tree. Thus, there exists a function $s(x)$ which finds the s-value for internal nodes as:
$$\min (s(left),s(right))+1$$
Therefore, if a subtree with root $x$ has $m$ nodes, then $s(x)$ is at most $\log (m+1)$. Through this the **leftist tree property** can be maintained which states that during a merge if the s-value of the right subtree is bigger than the s-value of the left swap the subtrees. The **merge** operation which runs in $O(\log n)$ functions as the operation which all other operations in leftist trees use. This follows the pseudocode:
```pseudo
	\begin{algorithm}
	\caption{Merge($A,B$)}
	\begin{algorithmic}
		\If{$A=\null$ \Or $B=\null$}
			\Return other tree
		\EndIf
		\If{$A.key > B.key$}
			\Return \Call{Merge}{$B,A$}
		\EndIf
		\State $A.right \gets$ \Call{Merge}{$A.right,B$}
		\If{$A.left=\null$}
			\State \Call{swap}{$A.left,A.right$}
			\State $A.sValue \gets 1$
			\Return $A$
		\EndIf
		\If{$A.right.sValue > A.left.sValue$}
			\State \Call{swap}{$A.left,A.right$}
		\EndIf
		\State $A.sValue \gets A.right.sValue+1$		
	\end{algorithmic}
	\end{algorithm}
```
**Insertion** follows a process of creating a new tree with key and merging the new tree with the original. **Delete min** follows a similar process where the left and right subtrees are merge together replacing the original root. **Arbitrary deletion** is a non-standard operation that attempts to detach the subtree from the deleted node and replace with it with its own melded subtrees. After this the s-value needs to be updated and leftist tree property needs to be maintained. This happens in $O(\log n)$.

**Naïve initialisation** of a leftist tree takes $O(n\log n)$ since all nodes are individually merged into a single tree. A better approach can decrease complexity to $O(n)$ given the use of a queue of subtrees. Where a merge between the first and second tree in the queue is done before being added to the queue again until a single tree remains.

# Skew Heaps
A skew heap is a simple binary tree that satisfies the heap property while also ensuring a meld faster meld than a regular binary heap. As a result their main operation is a merge which on-paper is faster as it is bounded by the $O(\log_\phi n)$ which is slightly faster than leftist. **Merge** is similar to a leftist heap merge however forces the swap rather than maintaining an extra invariant, therefore making it simpler. This results in an amortized $O(\log n)$ complexity. The pseudocode for a skew heap merge follows:
```pseudo
	\begin{algorithm}
	\caption{Merge($A,B$)}
	\begin{algorithmic}
		\If{$A=\null$ \Or $B=\null$}
			\Return other tree
		\EndIf
		\If{$A.key > B.key$}
			\State \Call{swap}{$A,B$}
		\EndIf
		\State \Call{swap}{$A.left,A.right$}
		\State $A.left \gets$\Call{Merge}{$A.left,B$}
		\Return $A$
	\end{algorithmic}
	\end{algorithm}
```

# Binomial Heap
A binomial heap is a type of heap that keeps a forest of [[Tree Data Structures|binomial trees]] that maintain the heap property. Furthermore, number of nodes in each of these trees is always a power of two. Recursively this can be defined as the binomial tree $B_0$ consists of a single node while for the binomial tree $B_k$ it can be obtained by linking two trees $B_{k-1}$ together. Therefore, in general $B_k$ has $2^k$ nodes. Another definition views $B_k$ consisting of a root and subtrees $B_{k-1},B_{k-2},\dots,B_0$. The root of $B_k$ has $k$ children and the tree has a rank, and height of $k$. From this the name is found as the root of $B_k$ has ${k}\choose{j}$ descendants at distance $j$.

The structure of a binomial heap usually has nodes that hold there parent, the key value, their degree, and their children. Some approaches use a binary tree where children are kept as two pointers that point to a sibling and a child.

The key operation for binomial heaps is the meld operation. The **meld** operation follows a process of melding the trees into a single forest and then consolidating the pairs of trees with common ranks until all trees have a distinct rank. **Extract Min** operation returns a stored minimum node, removing it from the tree which after that is then melded with the forest consisting of the trees that remain from the original forest.

# Fibonacci Heap
A Fibonacci heap is a type of heap similar to a Binomial heap however with generalisation that not all trees are binomial trees but rather just trees that maintain the heap property. The main benefit of Fibonacci heaps are their fast meld operation and very fast decrease key implementation. The namesake for Fibonacci trees comes from the fact that a tree of order $n$ has at least $F_{n+2}$ nodes in it.

The structure of a Fibonacci heap is a list of roots, and a pointer to the minimum element. The respective trees in the root list contain a root node, with the root and all nodes storing a list of degree, a parent, left and right siblings, a list of children, and a mark. The mark being a Boolean that notes whether the node has lost a child since the last time it was made the child of another node.

The **insertion** process for a Fibonacci heap is basic as it just sets up the structure for later operations to operate on. Therefore, given a valid root list and a pointer to the min the pseudocode for $O(1)$ insertion is simply:
```pseudo
	\begin{algorithm}
	\caption{Insert($H,x$)}
	\begin{algorithmic}
		\State $x.degree \gets 0$
		\State $x.parent \gets \nil$
		\State $x.child \gets \nil$
		\State $x.mark \gets$\False
		\State $H.roots.$\Call{append}{$x$}
		\If{$x.key < H.min.key$}
			\State $H.min \gets x$
		\EndIf
	\end{algorithmic}
	\end{algorithm}
```

**Merging** two heaps is another operation which is made simple by the Fibonacci heaps as the operation concatenates both root lists, checking which heap has the lower key to assign to. It follows the code:
```pseudo
	\begin{algorithm}
	\caption{Merge($H_1,H_2$)}
	\begin{algorithmic}
		\State $H \gets \emptyset$
		\State $H.min \gets H_1.min$
		\State $H.roots \gets H_1.roots + H_2.roots$
		\If{$H_1.min = \nil$ \Or ($H_2.min \neq \nil$ \And $H_2.min.key < H1.min.key$)}
			\State $H.min \gets H_2.min$
		\EndIf
		\Return $H$
	\end{algorithmic}
	\end{algorithm}
```

The consolidate function is a helper function that consolidates trees until all roots have a distinct degree value. This functions by finding two roots with the same degree and linking them together by making one the child of another. The pseudocode for this operation follows:
```pseudo
	\begin{algorithm}
	\caption{Consolidate($H$)}
	\begin{algorithmic}
		\State $A[0..\lfloor\log (H.length) \rfloor] \gets \nil$
		\For{$w \in H.roots$}
			\State $x \gets w$
			\State $d \gets x.degree$
			\While{$A[d]\neq \nil$}
				\State $y \gets A[d]$
				\If{$x.key > y.key$}
					\State \Call{swap}{$x,y$}
				\EndIf
				\State $H.roots.$\Call{remove}{$y$}
				\State $y.mark \gets$ \False
				\State $x.root.child.$\Call{append}{$y$}
				\State $x.root.degree \gets x.root.degree+1$
				\State $A[d] \gets \nil$
				\State $d \gets d+1$
			\EndWhile
			\State $A[d] \gets x$
		\EndFor
		\State $H.min \gets \nil$
		\For{$i\gets 0$ \To $\lfloor\log (H.length)\rfloor$}
			\If{$A[i]\neq\nil$}
				\State \Call{Insert}{$H,A[i]$}
			\EndIf
		\EndFor
	\end{algorithmic}
	\end{algorithm}
```

**Extract Min** starts by adding all children of the minimum value to the root list of the heap. After this the minimum node is checked for siblings, if no siblings exist then the heap is nearly empty if not the consolidation process is called to maintain the Fibonacci heap. Extract min runs in $O(\log n)$ amortized time since the cost of performing a link is paid for by the reduction in potential due to the link's reducing the number of roots. This follows the pseudocode:
```pseudo
	\begin{algorithm}
	\caption{Extract-Min($H$)}
	\begin{algorithmic}
		\State $z \gets H.min$
		\If{$z\neq \nil$}
			\For{$x \in z.child$}
				\State $x.parent \gets \nil$
				\State $H.roots.$\Call{append}{$x$}
			\EndFor
			\State $H.roots.$\Call{remove}{$z$}
			\If{$z=z.right$}
				\State $H.min \gets \nil$
			\Else
				\State $H.min \gets z.right$
				\State \Call{Consolidate}{$H$}
			\EndIf
		\EndIf
		\Return $z$
	\end{algorithmic}
	\end{algorithm}
```

The cut operation is an auxiliary operation found within decrease key, it simply cuts the link between two nodes making one the parent. It follows a process of:
```pseudo
	\begin{algorithm}
	\caption{Cut($H,x,y$)}
	\begin{algorithmic}
		\State $y.child.$\Call{remove}{x}
		\State $y.degree \gets y.degree - 1$
		\State $H.roots.$\Call{append}{x}
		\State $x.parent \gets \nil$
		\State $x.mark \gets$ \False
	\end{algorithmic}
	\end{algorithm}
```

Similarly the cascading cut is another auxiliary operation that recurses up to find a node that has yet to be cut recently. It functions as:
```pseudo
	\begin{algorithm}
	\caption{Cascading-Cut($H,y$)}
	\begin{algorithmic}
		\State $z \gets y.parent$
		\If{$z\neq\nil$}
			\If{$y.mark=$ \False}
				\State $y.mark \gets$ \True
			\Else
				\State \Call{Cut}{$H,y,z$}
				\State \Call{Cascading-Cut}{$H,z$}
			\EndIf
		\EndIf
	\end{algorithmic}
	\end{algorithm}
```

**Decrease key** is one of the operations which is particularly fast for Fibonacci heaps and follows a process of first checking if the node is a root or has a parent with a smaller key if so it continues on to check if the new key is the minimum of the heap. If not the heap needs to be modified. The code for this follows:
```pseudo
	\begin{algorithm}
	\caption{Decrease-Key($H,x,key$)}
	\begin{algorithmic}
		\If{$key > x.key$}
			\Print error new key is smaller than current key
		\EndIf
		\State $x.key \gets key$
		\State $y \gets x.parent$
		\If{$y\neq\nil$ \And $x.key < y.key$}
			\State \Call{Cut}{$H,x,y$}
			\State \Call{Cascading-Cut}{$H,y$}
		\EndIf
		\If{$x.key < H.min.key$}
			\State $H.min \gets x$
		\EndIf
	\end{algorithmic}
	\end{algorithm}
```

**Deletion** of an arbitrary element is simple and follows a process of decreasing the key of the given node to $-\infty$, and extracting the minimum. Resulting in a $O(\log n)$ amortized deletion cost.

# Pairing Heaps
Pairing heaps are a self-adjusting analogue to a Fibonacci heap in that they are a simpler implementation of Fibonacci heaps. The only structure maintained within a pairing heap are three pointers one to the leftmost child (child's linked list), and two sibling pointers. With the leftmost child pointing to the parent. There are several variants of pairing heaps with the **two-pass** being the simplest.

**Meld** implementation is fairly simple with the operation simply adding a new left child pointer that has the siblings of the previous sibling list. **Insertion** calls the merge operation by creating a new node with the given key. **Two Pass Merge** is the first new operation added. This merge ensures that after a root is deleted the heap property is maintained. It follows:
```pseudo
	\begin{algorithm}
	\caption{TwoPassMerge($H,x$)}
	\begin{algorithmic}
		\If{$x=\nil$ \Or $x.nextSibling=\nil$}
			\Return $x$
		\EndIf
		\State $y \gets x$
		\State $z \gets x.nextSibling$
		\State $newNode \gets x.nextSibling.nextSibling$
		\State $y.nextSibling \gets \nil$
		\State $z.nextSibling \gets \nil$
		\Return \Call{Merge}{\Call{Merge}{$y,z$}, \Call{TwoPassMerge}{$newNode$}}
	\end{algorithmic}
	\end{algorithm}
```

Two Pass Merge allows the deletion of arbitrary nodes, as well as a $O(\log n)$ extract min. Decrease key implementation follows a process where the node's key is changed. If it proves to be smaller than its parent it is then cut from its linked list and place higher in the order.