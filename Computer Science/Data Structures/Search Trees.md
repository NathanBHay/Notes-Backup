A search tree is a [[Graph Theory|tree]] [[Tree Data Structures|data structure]] that is used to locate specific keys within a set. Search trees function as a [[Data Structures#Lookup Tables|lookup structure]] that stores a key that can be ordered such that lookup times can improve over traditional arrays and tables. The main operations a search tree follows are:
- **Search** for a node in the tree
- **Min/Max** node of the tree.
- **Predecessor/Successor** of a certain node.
- **Insertion/Deletion** of nodes within the tree.

The goal of a search tree is for all main operations to be done in a time less than $O(n)$ to prove more efficient than normal arrays and tables. The most basic form of a search tree is a binary search tree which restricts children to two. This doesn't guarantee faster worst case complexity than $O(n)$ therefore it is common to use [[Self Balancing Search Trees|self balancing tree]] to improve complexity bounds.

| Operation                                                  | Space         | Search        | Insert        | Delete        |
| ---------------------------------------------------------- | ------------- | ------------- | ------------- | ------------- |
| [[Search Trees#Binary Search Tree\|Binary Trees]]          | $O(n)$        | $O(n)$        | $O(n)$        | $O(n)$        |
| [[Self Balancing Search Trees#AVL Tree\|AVL]]              | $O(n)$        | $O(\log n)$   | $O(\log n)$   | $O(\log n)$   |
| [[Self Balancing Search Trees#Red-Black Trees\|Red-Black]] | $O(1)^*$      | $O(\log n)$   | $O(1)^*$      | $O(1)^*$      |
| [[Search Trees#Splay Trees\|Splay]]                        | $O(\log n)^*$ | $O(\log n)^*$ | $O(\log n)^*$ | $O(\log n)^*$ |
| [[B-Tree]]                                                 | $O(\log n)$   | $O(\log n)$   | $O(\log n)$   | $O(\log n)$   |
Where $^*$ is amortized complexity.

# Binary Search Tree
A binary search tree is a [[Tree Data Structures#Binary Tree|binary tree]] that stores elements based upon the rule that elements in the left subtree are less than the root, and items in the right are greater than the root. Both of these subtrees being their own binary trees. In general all operations for binary search trees take $O(n)$ due to the worst case of a tree with only one child each. However, in the case of a randomly built binary tree this time complexity theoretically approaches $O(\log n)$. This changed conditions allows a search operation that uses a [[Searching Algorithms#Binary Search|binary search]] to find where an element is. This search follows the pseudocode:
```pseudo
	\begin{algorithm}
	\caption{BSTSearch(x,key)}
	\begin{algorithmic}
		\IF{$x= \nil$ \Or $x.val= key$}
			\RETURN $current$
		\ELIF{$key < x.value$}
			\RETURN \CALL{BSTSearch}{x.left,key}
		\ELIF{$key > x.value$}
			\RETURN \CALL{BSTSearch}{x.right,key}
		\ENDIF
	\end{algorithmic}
	\end{algorithm} 
```

This use of a binary search allows insertion to have a $O(h)$ time complexity, where $h$ is the size of the tree. This speed usually is less than $O(n)$, where $n$ is the total nodes, however in cases with only 1 child for all nodes this time complexity is achieved. An iterative tree search can be written as:
```pseudo
	\begin{algorithm}
	\caption{IterativeBSTSearch($x,key$)}
	\begin{algorithmic}
		\While{$x \neq \nil$ \And $x.val \neq key$}
			\If{$k < x.val$}
				\State $x \gets x.left$
			\Else
				\State $x \gets x.right$
			\EndIf
		\EndWhile
		\Return $x$
	\end{algorithmic}
	\end{algorithm}
```

## Insertion
Insertion of a node is handled through a binary search that finds a location where the node can be kept. This has the addition of operations to ensure the new node is placed correctly. Insertion functions through a search down to the bottom. Where after the node is added to the correct side of the node. It follows the pseudocode:
```pseudo
	\begin{algorithm}
	\caption{TreeInsert($T,z$)}
	\begin{algorithmic}
		\State $y \gets \nil$
		\State $x \gets T.root$
		\While{$x \neq \nil$}
			\State $y \gets x$
			\If{$z.val < x.val$}
				\State $x \gets x.left$
			\Else
				\State $x \gets x.right$
			\EndIf
		\EndWhile
		\State $z.parent \gets y$
		\If{$y = \nil$}
			\State $T.root \gets z$
		\Elif{$z.val < y.val$}
			\State $y.left \gets z$
		\Else
			\State $y.right \gets z$
		\EndIf
	\end{algorithmic}
	\end{algorithm}
```

## Deletion
The overall strategy for deletion follows three basic cases. These are:
- If $z$ has no children remove it, and set $\textbf{Nil}$ as the target.
- If $z$ has just one child then elevate that child to take $z$'s position in the tree by modifying $z$'s parent to replace $z$ by the child.
- If $z$ has two children find $z$'s successor $y$ and have it take the position of $z$ in the tree. Thus, the original right and left subtree becomes $y$'s new connections.

To achieve the behaviour exhibited by this deletion process a transplant operation is created to replace a subtree rooted at node $u$ with a new tree at $v$. This operation checks if the node lacks a parent, a left or right. Whereafter it inserts itself as an ancestor of the node before setting it as the parent. This code follows:
```pseudo
	\begin{algorithm}
	\caption{Transplant($T,u,v$)}
	\begin{algorithmic}
		\If{$u.parent = \nil$}
			\State $T.root \gets v$
		\Elif{$u = u.parent.left$}
			\State $u.parent.left \gets v$
		\Else
			\State $u.p.right \gets v$
		\EndIf
		\If{$v \neq \nil$}
			\State $v.parent \gets u.parent$
		\EndIf
	\end{algorithmic}
	\end{algorithm}
```

Through the tree transplant operation a deletion operation can be created to follow all three cases. The first two achieved through a basic transplant while the last case is solved through multiple transplants.
```pseudo
	\begin{algorithm}
	\caption{TreeDelete($T,z$)}
	\begin{algorithmic}
		\If{$z.left = \nil$}
			\State \Call{Transplant}{$T,z,z.right$}
		\Elif{$z.right = \nil$}
			\State \Call{Transplant}{$T,z,z.left$}
		\Else
			\State $y \gets$ \Call{TreeMinimum}{$z.right$}
			\If{$y.parent \neq z$}
				\State \Call{Transplant}{$T,y,y.right$}
				\State $y.right \gets z.right$
				\State $y.right.parent \gets y$
			\EndIf
			\State \Call{Transplant}{$T,z,y$}
			\State $y.left \gets z.left$
			\State $y.left.parent \gets y$
		\EndIf
	\end{algorithmic}
	\end{algorithm}
```

## Minimum & Maximum
The **minimum and maximum** operations can be found with a similar search that follows the respective direction, with it being left in the case of minimum and right in the case of maximum. These operations as they are a search follow the time complexity of $O(n)$. This is written as:
```pseudo
	\begin{algorithm}
	\caption{TreeMinimum($x$)}
	\begin{algorithmic}
		\While{$x.left \leq \nil$}
			\State $x \gets x.left$
		\EndWhile
		\Return $x$
	\end{algorithmic}
	\end{algorithm}
```

## Successor & Predecessor
The s**uccessor and predecessor** of a given node find the node which is either the next biggest or next smallest node. The following pseudocode avoids comparisons and finds it at the place that the node is suspected to be. In the case where the right-subtree is non-empty then the successor of $x$ is the leftmost node in the right subtree. In the case where the subtree is empty then the successor is the lowest ancestor of $x$ whose left child is also an ancestor of x. This algorithm has a time complexity of $O(n)$.
```pseudo
	\begin{algorithm}
	\caption{TreeSuccessor($x$)}
	\begin{algorithmic}
		\If{$x.right \neq \nil$}
			\Return \Call{TreeMinimum}{$x.right$}
		\EndIf
		\State $y \gets x.parent$
		\While{$y \neq \nil$ \And $x = y.right$} 
			\State $x \gets y$
			\State $y \gets y.parent$
		\EndWhile
		\Return $y$
	\end{algorithmic}
	\end{algorithm}
```

# Splay Trees
A splay tree is a self balancing binary search tree that decrease the access time of recently accessed elements. This is done through a process called **splaying** where every search results in the root being changed with the searched for element. This enables splay trees to function better that other balanced trees given similar items are requested.

The rotations required to balance a splay tree are first the **Zig rotation** which is similar to the left and right rotate found within AVL trees. The zig-rotation
```pseudo
	\begin{algorithm}
	\caption{Zig($parent,child$)}
	\begin{algorithmic}
		\If{$child=parent.left$}
			\State $parent.left \gets c.right$
			\State $c.right \gets p$
		\Else
			\State $parent.right \gets c.left$
			\State $c.left \gets p$
		\EndIf
		\Return $child$
	\end{algorithmic}
	\end{algorithm}
```

The **Zig-Zig rotation** is a double rotation that rotates three nodes going in one direction to the other. For example rotating a grandparent with a left child and a parent with a left child to the right. It follows the pseudocode:
```pseudo
	\begin{algorithm}
	\caption{ZigZig($gparent,parent,child$)}
	\begin{algorithmic}
		\State $isLeft \gets$ \True
		\State $parentOfG \gets gparent.parent$
		\If{$parentOfG \neq \nil$ \And $g=parentOfG.right$}
			\State $isLeft \gets$ \False
		\EndIf
		\State $parent \gets$ \Call{Zig}{$gparent,parent$}
		\State $child \gets$ \Call{Zig}{$p,child$}
		\If{$parentOfG \neq \null$}
			\If{$isLeft=$ \True}
				\State $parentOfG.left \gets child$
			\Else
				\State $parentOfG.right \gets child$
			\EndIf
		\EndIf
		\Return $child$
	\end{algorithmic}
	\end{algorithm}
```

The **Zig-Zag rotation** is another double rotation for when a grandparents child and child's child zig zag back and forth. It follows the pseudocode:
```pseudo
	\begin{algorithm}
	\caption{ZigZag($gparent,parent,child$)}
	\begin{algorithmic}
		\State $isLeft \gets$ \True
		\If{$parent=gparent.right$}
			\State $isLeft \gets$ \False
		\EndIf
		\State $child \gets$ \Call{Zig}{$parent,child$}
		\If{$isLeft=$ \True}
			\State $gparent.left \gets child$
		\Else
			\State $gparent.right \gets child$
		\EndIf
		\State $isLeft \gets$ \True
		\State $parentOfG \gets gparent.parent$

		\If{$parentOfG \neq \null$ \And $g=parentOfG.right$}
			\State $isLeft \gets$ \False
		\EndIf
		\State $child \gets$ \Call{Zig}{$gparent,child$}
		\If{$parentOfG \neq \null$}
			\If{$isLeft=$ \True}
				\State $parentOfG.left \gets child$
			\Else
				\State $parentOfG.right \gets child$
			\EndIf
		\EndIf
		\Return $child$
	\end{algorithmic}
	\end{algorithm}
```

From these rotations a **splaying** operation can be created that functions to balance the tree after a search or insertion. Splaying takes a path from the root to the splayed element as an array of pointers. This results in moving the splayed element above the tree until it reaches the root, becoming the new root. It functions through the code:
```pseudo
	\begin{algorithm}
	\caption{Splay($path$)}
	\begin{algorithmic}
		\State $i \gets path.length$
		\State $c \gets path[i]$
		\State $i \gets i-1$
		\While{$i>0$}
			\State $p \gets path[i]$
			\State $i \gets i-1$
			\If{$i=0$}
				\State $c \gets$ \Call{Zig}{$p,c$}
				\Return $c$
			\Else
				\State $g \gets path[i]$
				\State $i \gets i-1$
				\State $leftParent \gets$ \True
				\If{$p=g.right$}
					\State $leftParent \gets$ \False
				\EndIf
				\State $leftChild \gets$ \True
				\If{$c=p.right$}
					\State $leftChild \gets$ \False
				\EndIf
				\If{$leftParent=leftChild$}
					\State $c \gets$ \Call{ZigZig}{g,p,c}
				\Else
					\State $c \gets$ \Call{ZigZag}{g,p,c}
				\EndIf
			\EndIf
		\EndWhile
		\Return $c$
	\end{algorithmic}
	\end{algorithm}
```

The **insertion** process follows a regular binary insertion which is then followed by splaying the element. **Removal** follows a process of removing the specified element and joining the remaining left and right nodes. Both o these operations have a $O(\log n)$ amortized complexity or a worst case $O(n)$.
