A self balancing search tree is a form of a [[Search Trees|search tree]] that maintains an invariant that ensures the tree is balanced so that it can achieve a worst case $O(\log n)$ lookup. This is usually achieved by ensuring the tree is balanced as this improves search speed.

The comparison between the balancing trees follows a belief that red-black trees provide faster insertion and removal while AVL's provide faster searches. As a result in cases where many insertions are required red-black prove better while for more searches an AVL tree is better. Furthermore, for searches with similar values a splay can prove more efficient despite the amortized complexity.

# Red-Black Trees
A red-black tree is a binary search tree with color field which can be either **red** or **black**. This constraint of node color enables the tree to be approximately balanced. These colors function on the set of rules:
1. Every node is red or black, with $\text{Nil}$, and root nodes being considered black.
2. A red node does not have a red child (*red violation*).
3. Every path from a given node to any descendant node goes through the same number of black nodes (*black violation*).

This means that a perfect binary tree only has black nodes. Red-black trees have the same operations such as minimum and successor which run the same way in both tree types.

## Insertion
**Rotation** is a process used within insertion or deletion which ensures that the binary-search tree properties are maintained. Left rotation results on a left node being changed with the parent, while right changes the parent with the right. It has a time complexity of $O(1)$ as only pointers change during rotation. It follows the pseudocode:
```pseudo
	\begin{algorithm}
	\caption{LeftRotate(T,x)}
	\begin{algorithmic}
		\STATE $y \gets x.right$
		\STATE $x.right \gets y.left$ \Comment{Turn y's left subtree into x's right subtree}
		\IF{$y.left \neq T.$Nil}
			\STATE $y.left.parent \gets x$
		\ENDIF
		\STATE $y.parent \gets x.parent$ \Comment{Link y's parent to x's}
		\IF{$x.parent = T.$Nil}
			\STATE $T.root \gets y$
		\ELIF{$x = x.parent.left$}
			\STATE $x.parent.left \gets y$
		\ELSE
			\STATE $x.parent.right \gets y$
		\ENDIF
		\STATE $y.left \gets x$ \Comment{Put x on y's left}
		\STATE $x.parent \gets y$
	\end{algorithmic}
	\end{algorithm} 
```

**Fixup** is a process of ensuring both the red, and black properties are maintained. This is achieved through a function that finds what rule what violated, and after that maintains the rule. The maximum the while loop occurs is $O(\log n)$ times. It uses the code:
```pseudo
	\begin{algorithm}
	\caption{RBInsertFixup($T,z$)}
	\begin{algorithmic}
		\While{$z.parent.color =$ red}
			\If{$z.parent = z.parent.parent.left$}
				\State $y \gets z.parent.parent.right$
				\If{$y.color = $ red}
					\State $z.parent.color \gets$ black
					\State $y.color \gets$ black
					\State $z.parent.parent.color \gets$ red
					\State $z \gets z.parent.parent$
				\Else
					\If{$z = z.parent.right$}
						\State $z \gets z.parent$
						\State \Call{LeftRotate}{$T,z$}
					\EndIf
					\State $z.parent.color \gets$ black
					\State $z.parent.parent.color\gets$ red
					\State \Call{RightRotate}{$t,z.parent.parent$}
				\EndIf
			\Else
				\State Same as above but with right and left exchanged
			\EndIf
		\EndWhile
		\State $T.root.color \gets$ black
	\end{algorithmic}
	\end{algorithm}
```

**Insertion** functions similar to a binary-tree insertion however after an item is inserted the node is colored red, and the rest of the tree is corrected. It follows the pseudocode:
```pseudo
	\begin{algorithm}
	\caption{RBInsert($T,z$)}
	\begin{algorithmic}
		\State $y \gets T.\nil$
		\State $x \gets T.root$
		\While{$x \neq T.\nil$}
			\State $y \gets x$
			\If{$z.val < x.val$}
				\State $x \gets x.left$
			\Else
				\State $x \gets x.right$
			\EndIf
		\EndWhile
		\State $z.parent \gets y$
		\If{$y = T.\nil$}
			\State $T.root \gets z$
		\Elif{$z.val<y.val$}
			\State $y.left \gets z$
		\Else
			\State $y.right \gets z$
		\EndIf
		\State $z.left \gets T.\nil$
		\State $z.right \gets T.\nil$
		\State $z.color \gets$ red
		\State \Call{RBInsertFixup}{$T,z$}
	\end{algorithmic}
	\end{algorithm}
```

## Deletion
Red-black tree deletion is done through a similar process as normal deletion however with a new fixup function to ensure the color is maintained. The delete fixup follows:
```pseudo
	\begin{algorithm}
	\caption{RBDeleteFixup($T,x$)}
	\begin{algorithmic}
		\While{$x \neq T.root$ \And $x.color =$ black}
			\If{$x = x.parent.left$}
				\State $w \gets x.parent.right$
				\If{$w.color =$ red}
					\State $w.color \gets$ black
					\State $x.parent.color \gets$ red
					\State \Call{LeftRotate}{$T,x.parent$}
					\State $w \gets x.parent.right$
				\EndIf
				\If{$w.left.color =$ black \And $w.right.color =$ black}
					\State $w.color \gets$ red
					\State $x \gets x.parent$
				\Else
					\If{$w.right.color =$ black}
						\State $w.left.color \gets$ black
						\State $w.color \gets$ red
						\State \Call{RightRotate}{$T,w$}
						\State $w \gets x.parent.right$
					\EndIf
					\State $w.color \gets x.parent.color$
					\State $x.parent.color \gets$ black
					\State $w.right.color \gets$ black
					\State \Call{LeftRotate}{$T,x.parent$}
					\State $x \gets T.root$
				\EndIf
			\Else
				\State Same as above but right and left exchanged
			\EndIf
		\EndWhile
		\State $x.color \gets black$
	\end{algorithmic}
	\end{algorithm}
```

The main deletion function follows:
```pseudo
	\begin{algorithm}
	\caption{RBDelete($T,z$)}
	\begin{algorithmic}
		\State $y \gets z$
		\State $yOriginalColor \gets y.color$
		\If{$z.left = \nil$}
			\State $x \gets z.right$
			\State \Call{RBTransplant}{$T,z,z.right$}
		\Elif{$z.right = \nil$}
			\State $x \gets z.left$
			\State \Call{RBTransplant}{$T,z,z.left$}
		\Else
			\State $y \gets$\Call{TreeMinimum}{$z.right$}
			\State $yOriginalColor \gets y.color$
			\State $x \gets y.right$
			\If{$y.parent = z$}
				\State $x.parent \gets y$
			\Else
				\State \Call{RBTransplant}{$T,y,y.right$}
				\State $y.right \gets z.right$
				\State $y.right.parent \gets y$	
			\EndIf
			\State \Call{RBTransplant}{$T,z,y$}
			\State $y.left \gets z.left$
			\State $y.left.parent \gets y$
			\State $y.color \gets z.color$			
		\EndIf
		\If{$yOriginalColor = $ black}
			\State \Call{RBDeleteFixup}{$T,x$}
		\EndIf
	\end{algorithmic}
	\end{algorithm}
```

# AVL Tree
The Adelson-Velskii Landis Tree improves the binary tree through ensuring that the heights of the left and right subtree differ by one at most. This functions through a balancing factor that is given by the idea:
$$\text{BalanceFactor}(u)=\text{height}(u.left) - \text{height}(u.right)$$
An imbalance occurs when the balance factor isn't equal to 0. There are four possible imbalances and they are:
- **Left-Left** imbalance which means the balance factor is $2$ and the left node's left subtree is as tall as the left node's right subtree. This is solved through a right rotation that makes the pivot's left tree and parent equal to its left and right children. It follows the pseudocode:
```pseudo
	\begin{algorithm}
	\caption{RightRotate($root$)}
	\begin{algorithmic}
		\State $par \gets root.parent$
		\State $pivot \gets root.left$
		\State $temp \gets pivot.right$
		\State $pivot.$\Call{SetRightChild}{$root$}
		\State $pivot.$\Call{SetLeftChild}{$temp$}
		\State $pivot.$\Call{SwapChild}{$root,pivot$}
	\end{algorithmic}
	\end{algorithm}
```

- **Right-Right** imbalance happens when the balance factor is $-2$ and the right node's subtree is at least as tall as the right node's left subtree. This does a left rotation where the pivot's parent and right child become its left and right children.
```pseudo
	\begin{algorithm}
	\caption{LeftRotate($root$)}
	\begin{algorithmic}
		\State $par \gets root.parent$
		\State $pivot \gets root.right$
		\State $temp \gets pivot.left$
		\State $pivot.$\Call{SetLeftChild}{$root$}
		\State $pivot.$\Call{SetRightChild}{$temp$}
		\State $pivot.$\Call{SwapChild}{$root,pivot$}
	\end{algorithmic}
	\end{algorithm}
```

- **Left-Right** imbalance occurs when a node's balance factor is $2$ and the left node's right subtree is taller than the left node's left subtree. This is solved with a double right rotation where the root's left child's right child becomes the parent and with the root becoming the right child of the new root.
```pseudo
	\begin{algorithm}
	\caption{DoubleRightRotate($root$)}
	\begin{algorithmic}
		\State \Call{RotateLeft}{$root.left$}
		\State \Call{RotateRight}{$root$}
	\end{algorithmic}
	\end{algorithm}
```

- **Right-Left** imbalance occurs when the balance factors is $-2$ and the right node's left subtree is taller than the right node's right subtree. This is solved with a double left rotate where the root's right child's left child becomes the new root and the root becomes the left child.
```pseudo
	\begin{algorithm}
	\caption{DoubleLeftRotate($root$)}
	\begin{algorithmic}
		\State \Call{RotateRight}{$root.left$}
		\State \Call{RotateLeft}{$root$}
	\end{algorithmic}
	\end{algorithm}
```

This all can be grouped together in a rebalance operation that satisfies all the conditions. This follows the pseudocode:
```pseudo
	\begin{algorithm}
	\caption{Rebalance($node$)}
	\begin{algorithmic}
		\If{\Call{BalanceFactor}{$node$} $=2$}
			\If{\Call{BalanceFactor}{$node.left$} $<0$}
				\State \Call{DoubleRightRotate}{$node$}
			\Else
				\State \Call{RightRotate}{$node$}
			\EndIf
		\Elif{\Call{BalanceFactor}{$node$} $=-2$}
			\If{\Call{BalanceFactor}{$node.right$} $>0$}
				\State \Call{DoubleLeftRotate}{$node$}
			\Else
				\State \Call{LeftRotate}{$node$}
			\EndIf
		\EndIf
	\end{algorithmic}
	\end{algorithm}
```

Due to these operations a AVL tree is always balanced and thus has a worst case complexity of $O(\log n)$ for insertions, deletions and lookups.