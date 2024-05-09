A B-Tree is a  [[Search Trees|search tree]] which allows for multiple children for a given node. In addition to this it maintains a [[Self Balancing Search Trees|self balancing]] aspect that improves insertion speed. B-Trees are used due to their ability to minimise [[Memory|disk read/write operations]] by playing on spatial locality.

A B-Tree's is a [[Tree Data Structures|rooted tree]]. A *node* $x$ in the tree holds a number keys that are stored in order. A node contains $t-1$ to $2t-1$ keys, where $d$ is the branching factor/**minimum degree**. Where a node is *full* if it has $2t-1$ keys.  *Leaf nodes* have a boolean value specifying whether they are a leaf node. All leaves have the same depth which is the height of the tee. *Internal nodes* contain pointers to at least $m/2$ to $m$ children. These pointers to the subtrees are "between" the keys, with all keys within the subtree being between keys.

**Search** functions similar to doing a [[Searching Algorithms#Binary Search|binary search]] on each node, and if it finds the result to be between two keys it descends. 
```pseudo
	\begin{algorithm}
	\caption{BTreeSearch($x,k$)}
	\begin{algorithmic}
		\State $i \gets 1$
		\While{$i\leq x.n$ \And $k > x.key_i$}
			\State $i \gets i + 1$
        \EndWhile
        \If{$i \leq x.n$ \And $k= x.key_i$}
	        \Return $(x,i)$
		\Elif{$x.leaf$}
			\Return $\nil$
		\Else 
			\State \Call{DiskRead}{$x.c_i$}
			\Return \Call{BTreeSearch}{$x.c_i, k$}
        \EndIf
	\end{algorithmic}
	\end{algorithm}
```

**Split** is an operation required by insertion that splits a node into two.
```pseudo
	\begin{algorithm}
	\caption{BTreeSplit($x,i$)}
	\begin{algorithmic}
		\State $z \gets$ \Call{AllocateNode}{}
		\State $y \gets x.c_i$
		\State $z.leaf \gets y.leaf$
		\State $z.n \gets t-1$
		\For{$j\gets 1$ \To $t-1$}
			\State $z.key_j \gets y.key_{j+1}$
        \EndFor
        \If{\Not $y.leaf$}
	        \For{$j \gets 1$ \To $t$}
		        \State $z.c_j \gets y.c_{j+1}$
            \EndFor
        \EndIf
        \State $y.n \gets t-1$
		\For{$j \gets x.n+1$ \DownTo $i+1$}
			\State $x.c_{j+1} \gets x.c_j$
        \EndFor
		\State $x.c_{i+1} \gets z$
		\For{$j\gets x.n$ \DownTo $i$}
			\State $x.key_{j+1}\gets x.key_j$
        \EndFor
		\State $x.key_{i}\gets x.key_t$
		\State $x.n \gets x.n + 1$
		\State \Call{DiskWrite}{$y$}
		\State \Call{DiskWrite}{$x$}
		\State \Call{DiskWrite}{$z$}
	\end{algorithmic}
	\end{algorithm}
```


**Insertion** 
```pseudo
	\begin{algorithm}
	\caption{BTreeInsert($T, k$)}
	\begin{algorithmic}
		\State $r \gets T.root$
		\If{$r.n=2t-1$}
			\State $s \gets$ \Call{AllocateNote}{}
			\State $T.root \gets s$
			\State $s.leaf \gets$ \False
			\State $s.n \gets 0$
			\State $s.c_1 \gets r$
			\State \Call{BTreeSplit}{$s, 1$}
			\State \Call{BTreeInsertNonFull}{$s,k$}
		\Else
			\State \Call{BTreeInsertNonFull}{$r,k$}
        \EndIf
	\end{algorithmic}
	\end{algorithm}
```

**Insert Non-Full**
```pseudo
	\begin{algorithm}
	\caption{BTreeInsertNonFull($x, k$)}
	\begin{algorithmic}
		\State $i \gets x.n$
		\If{$x.leaf$}
			\While{$i\geq1$ \And $k<x.key_i$}
				\State $x.key_{i+1} \gets x.key_i$
				\State $i \gets i - 1$
            \EndWhile
			\State $x.key_{i+1} \gets k$
			\State $x.n \gets x.n + 1$
			\State \Call{DiskWrite}{$x$}
		\Else
			\While{$i\gets 1$ \And $k<x.key_i$}
				\State $x \gets i-1$
            \EndWhile
            \State $i \gets i+1$
			\State \Call{DiskWrite}{$x$}
			\If{$x.c_i.n=2t-1$}
				\State \Call{BTreeSplit}{$x,i$}
				\If{$k>x.key_i$}
					\State $i \gets i+1$
                \EndIf
            \EndIf
            \State \Call{BTreeInsertNonFull}{$x.c_i,k$}
        \EndIf
	\end{algorithmic}
	\end{algorithm}
```

# B+ Trees
A B+ tree is a variant of B-Tree