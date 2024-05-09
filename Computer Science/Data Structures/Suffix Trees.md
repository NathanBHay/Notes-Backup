A suffix tree is a compact trie that contains all the suffixes of a string. These trees usually have $n$ leaves numbered through $1..n$, with every internal node having at least two children. These edges are labelled similar to Tries. They also use a terminating character `$` or `\0` to designate leafs. Its main goal is to solve problems such as the **[[Pattern Matching|pattern matching problem]]**, and the **sub-string matching problem**. The sub-string matching problem finds a pre-processing of text $T$, such that a pattern $P[1..m]$ can be searched proportional to length $m$. The **longest repeated sub-string problem** states given a string $S[1..n]$, find the longest sub-string that occurs at least two times.

A suffix tree is created by inserting all suffixes into a prefix tree. This is done through inserting the longest suffix $S[1..]$, before inserting $S[2..]$ and so on. This allows us to compare itself with the adjacent nodes to allow for the tree to be constructed similar to a prefix tree. This approach takes  $O(m)$, since all strings of length $n$ have $n$ suffixes and will take $O(n^2)$ space unless stored compactly.

**Compact suffix trees** function by merging repeated nodes. This is then used to replace all entries with a tuple which represents $(x,y)$, where $x$ is starting index and $y$ is the length. This decreases the space to be $O(n)$ space. 

## Implicit Suffix Trees
An implicit suffix tree is a tree which lacks the terminating characters and is compressed. This means there are endings within the tree. To find an implicit suffix tree you remove all terminating characters, removing any edge with no text, and then remove all internal nodes that lack at least two children. 

## Ukkonen's Algorithm
Ukkonen's algorithm is an $O(n)$ suffix tree building algorithm. This algorithm works by first constructing the implicit suffix tree of $S[1..n]$. The algorithm is divided into $n$ phases where each phase $i+1$ builds upon $T_i$ to find $T_{i+1}$. These phases are then divided into $i+1$ extensions where the tree is added. These extensions have 3 different rules. What improves the speed of this algorithm are the addition of suffix links for fast tree navigation.

### Implementation
Implementation of Ukkonen's requires some modifications to implicit suffix trees and keeping track of multiple variables.

The implicit suffix tree needs to be kept as a set pairs which point to the left and right range of the string. This means that $(l,r)$ represent $S[l..r]$. This can be further optimised by keeping $\#$ for a right pointer which represents $i$. This removes the need to update the tree every time a new character is added.

The extra variables that need be kept of is the remainder and the active point which consists of the active node, edge and length. The **active point** is the node $v$ under whose edge the extension is being applied. The **remainder** is the characters $S[k..i]$ where the extension is applied to. The remainder therefore represents the number of suffixes that need to be inserted at the end of each step. is set of 1 at the start of all iterations.

### Extensions
The goal of an extension is to add the next character in the string to all respective edges in the current tree. This is done through three different cases:
1. The basic case is where substring $S[j..i]$ is a leaf node. In this case the extension is simply appending the string to the node. This happens when the character is yet to be already found within the tree.
2. In the case where $S[j..i]$ isn't a leaf edge and the next character $x$ isn't the same as $S[i+1]$ then a new internal node is created at $S[i]$. This node connects $x$'s edge and a new node $S[i+1]$.
3. In the last cases where $S[j..i]$ isn't a leaf edge but the next character $x$ is the same, do nothing.

Following the rules above you have a **naive implicit suffix tree creation** algorithm that is able to construct the tree in $O(n^3)$ time. This bound is caused by traversal time where to find the end of a path $O(i+1-j)$ characters must be traversed. This means a given phase has $O(i^2)$ traversals.

### Suffix Links
A suffix link is a pointer between two internal nodes $u$ to $v$ which improves traversal time. This is as the path from the root to $u$ for some $k$ is $S[j..k-1]$ while the path from the root to $v$ is $S[j+1..k-1]$. This pretty much means that if the path to $u$ is $\mathcal{x}\alpha$ then the path to $v$ is $\alpha$. Due to this we are able to do the same modifications to both.

Construction of suffix links happen during rule 2 where after a construction of the first node all consecutive nodes have a suffix link to the previously created node. This means that during extension of $j+1$ we link to $j$. As a result by the end of the phase all internal nodes will have a link to another node.

To follow suffix links during the extension phase, you set an active node during $j$, and upon the next phase $j+1$ follow the suffix link.

### Skip Counting
Skip counting is a method to skip traversal during extensions after jumping between suffix links. This is done by using the previous length of the tail and comparing it against the current node's edge's length. If the length of the tail is greater than the node can be skipped, which repeats until this isn't the case. This speeds up traversal given $O(1)$ length computation. Using suffix links and skip counting allows computation of suffix trees in $O(n^2)$ time.

### Extension Termination
Extension termination criterion or the **showstopper rule** works off the idea that once rule 3 is triggered then every successive extension in the phase will follow rule 3. This is as the extension from $S[j..i]$ must be continued by $S[i+1]$ however since $x$ continues the path $S[j..i]$ it must also continue the path $S[j+1..i]$. From this the extension $j+1$ will follow similarly. Therefore to improve the speed simply skip the entire rest of the phase.

### Rapid Leaf Extension
Rapid leaf extensions works of the idea that once a leaf is created and given its range $j$ it will always be a leaf, meaning that only rule 1 is ever applied to it. This is proven by the fact that all rule 1's are rule 1's in the next phase and extended by the lemma all rule 2's are rule 1's the next phase.