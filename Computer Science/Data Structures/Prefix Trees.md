A Retrieval Tree, or **Trie**, is a [[String Retrieval Structures|string retrieval structure]] that functions as a multi-way [[Tree Data Structures|tree]] that keeps a set of strings arranged within a tree where words with a shared prefix are contained within the sub-tree. The tree is rooted with edges (or nodes) that correspond to a character. A path corresponds to a prefix of a word in the tree. A path from a root to an internal node is a common prefix of multiple strings.

A basic insertion operation, which can also be used to build a Trie through iterations of all words, follows the pseudocode:
```pseudo
	\begin{algorithm}
	\caption{Insertion($S[1..n]$)}
	\begin{algorithmic}
		\State $node \gets root$
		\For{$c \in S[1..n]$}
			\If{$node$ has edge for character $c$}
				\State $node \gets node.$\Call{GetChild}{$c$}
			\Else
				\State $node \gets node.$\Call{CreateChild}{$c$}
			\EndIf
		\EndFor
	\end{algorithmic}
	\end{algorithm}
```

A common application of Tries are within the **prefix matching problem**, where a list of strings that begin with a particular prefix need to be found. This is done through a query to the Trie where all children are found. A similar problem is **exact string lookup** where a string needs to be found. A lookup function for these problems follows the pseudocode:
```pseudo
	\begin{algorithm}
	\caption{LookUp}
	\begin{algorithmic}
		\State $node \gets root$
		\For{$c \in S[1..n]$}
			\If{$node$ has edge for character $c$}
				\State $node \gets node.$\Call{GetChild}{$c$}
			\Else
				\Return \False
			\EndIf
		\EndFor
		\Return \True
	\end{algorithmic}
	\end{algorithm}
```

**String sorting** is another common problem which can be done on Tries. Sorting a trie has a time complexity of $O(|\Sigma| T)$ for array implementations, for balanced trees a $O(T\log |\Sigma|)$, and assuming all strings are roughly the same length a complexity of $O(T\log n)$. The pseudocode for this follows:
```pseudo
	\begin{algorithm}
	\caption{Prefix Trie Sort}
	\begin{algorithmic}
		\Procedure{SortStrings}{$strings[1..n]$}
			\For{$s \in strings[1..n]$}
				\State \Call{Insert}{$s+'\$'$}
			\EndFor
			\State \Call{Traverse}{$root,""$}
		\EndProcedure
		\State
		\Procedure{Traverse}{$node, curString$}
			\If{$curString[-1] \neq '\$'$}
				\For{$c \in$ node sorted alphabetically}
					\State $curString.$\Call{append}{$c$}
					\State \Call{Traverse}{$node.$\Call{GetChild}{c},$curString$}
					\State $curString.$\Call{pop}{}
				\EndFor
			\EndIf
		\EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

## Implementation
There are three common implementations of the prefix tree, these are:
- Arrays to store child pointers for each character in the alphabet. This has an insertion of $O(n)$, where $n$ is the length of a query string. The disadvantage is the space complexity results in $O(|\Sigma| \cdot T)$, where $T$ is the longest query string.
- [[Search Trees#AVL Tree|Balancing Trees]] use the smallest space complexity as they only store pointers of children that exist. For larger alphabets this is useful however does result in an insertion time of $O(n\log (T))$ as each node must use a search tree to find the child pointer. The total space complexity is $O(T)$.
- [[Hashtables]] use the minimal space as it only stores children that exist, thus $O(T)$. It also allows lookup in $O(n)$ time since each search is constant. This implementation suffers from the inability to do possible advanced tricks such as looking up adjacent letters, and more.

A common implementation detail is the use of `$` or `\0` to terminate words as to designate a leaf.

## Compact Trie
A Compact Trie is a method of decreasing the space taken by a Trie. This is done by converting nodes with one child into the same node. Thus, the edge has a weight $ab$ rather than $a$ and $b$. This change decreases the space taken.