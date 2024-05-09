A string metric is a way of measuring the difference between two [[Datatypes#String|strings]], also commonly called **edit distance**. This difference can be measured in a variety of different ways which promote certain aspects of the difference between the string. String metrics provide a useful [[Loss Functions|cost function]] that can be used within metaheuristics or neural networks. Some common string metrics not included below can be found in algorithms used to measure set difference.

The edit distance problem can be formalized as the process of getting from string $a$ to $b$ where $a,b \in \Sigma$. The minimum weight of the function that transforms is called the edit distance. These have four possible common operations that usually increase edit distance by one. These follow:
- **Insertion** of a symbol which turns $uv$ to $uxv$, where $x$ is the new character.
- **Deletion** of a symbol which turns $uwv$ to $uv$.
- **Substitution** which transforms $uwv$ to $uxv$, where $x \neq w$.
- **Transposition** which switches symbols such as $uv$ to $vu$

# Hamming Distance
Hamming distance is a very simple check which operates on the idea that the distance is the amount of different characters, on a string of the same length. This means the only operation hamming distance measures is a substitution operation where one letter is replaced for another. Most implementations operate on the idea that the length of all measured strings are the same. For implementations that don't follow this rule the distance count is added to for null characters.
```pseudo
	\begin{algorithm}
	\caption{HammingDist(a,b)}
	\begin{algorithmic}
	\INPUT $a.length = b.length$
		\STATE $dist \gets 0$
		\FOR{$i\gets 0$ \TO $a.length$}
			\IF{$a[i] \neq b[i]$}
				\STATE $dist \gets dist + 1$
			\ENDIF
		\ENDFOR
		\RETURN $dist$
	\end{algorithmic}
	\end{algorithm} 
```
This algorithm has a time complexity of $O(n)$, where $n$ is the length of the largest string. The hamming distance on a binary sequence is equal to the amount of 1's found in an XOR, $s1 \oplus s2$.

# Levenshtein Distance
Levenshtein distance is a more complex string metric with insertion, deletion, and substitution operations. Given two strings $a$ and $b$, Levenshtein distance has a [[Recursion|recurrence]] relation which follows the rule:
$$\text{lev(a,b)}\begin{cases}
|a|&\text{if }|b|=0,\\
|b|&\text{if }|a|=0,\\
\text{lev(tail($a$),tail($b$))}&\text{if }a[0]=b[0],\\
1+\min\begin{cases}
	\text{lev(tail($a$),$b$))}\\
	\text{lev($a$,tail($b$))}\\
	\text{lev(tail($a$),tail($b$))}
\end{cases}&\text{otherwise}
\end{cases}$$
Where $\text{tail}(x)$ is equal to the rest of the string minus the first element. In list slices this can be called as $x[1:]$. The above definition is the naïve recursive implementation and as such can be improved through the use of [[Algorithmic Paradigms#Dynamic Programming|dynamic programming]]. An iterative approach to this problem usually results in a space complexity of $O((|a|+1)\cdot (|b|+1))$, as a matrix is generated. This matrix represents the letters of each string and functions by using using the diagonal to find the cases where the characters are equal and if not finds the minimum of the left, up and top right values. 

Levenshtein distance can be approximated between two strings of length $n$ as a factor within $(\log n)^{O(1/\epsilon)}$, where $\epsilon$ is a parameter that is tuned in time $O(n^{1+\epsilon})$. 

# Damerau-Levenshtein Distance
Damerau-Levenshtein distance adds extra complexity to the Levenshtein distance algorithm through the addition of a transposition operation, that switches two adjacent characters.  The algorithm can be expressed as the function $d_{a,b}(i,j)$, where $i,j$ is the distance between string $a$ and $b$ respectively. It follows the recurrence relation:
$$d_{a,b}(i,j)=\min\begin{cases}
0&\text{if }i=j=0,\\
d_{a,b}(i-1,j)+1&\text{if }i>0,\\
d_{a,b}(i,j-1)+1&\text{if }j>0,\\
d_{a,b}(i-1,j-1)+1_{a_i\neq b_j}&\text{if }i,j>0,\\
d_{a,b}(i-2,j-2)+1_{a_i\neq b_j}&\text{if }i,j>0\text{ and }a_i=b_{j-1}\text{ and }a_{i-1}=b_j,
\end{cases}$$
Where $1_{a_i\neq b_j}$, represents a function where the value is $1$ unless given the condition $a_i=b_i$, where it is $0$. More expressively the second case corresponds to deletion, the third is insertion, fourth is a match of mismatch, and fifth is transposition. This algorithm can be optimized like Levenshtein with dynamic programming. The naïve implementation results in a complexity equal to $O(M\cdot N\cdot \max (M,N))$, where $M$ and $N$ are the string lengths. This algorithm can be improve to have a time complexity equal to $O(M\cdot N)$.

# Jaro Distance
Jaro distance is a string metric which gives more of an approximate value that can be used to represent the difference between strings. It follows the rule:
$$\text{sim}=\begin{cases}
0&\text{if }m=0\\
\frac13 \bigl( \frac{m}{|a|}+\frac{m}{|b|}+\frac{m-t}{m} \bigl)&\text{otherwise}
\end{cases}$$
Where $m$ is the number of matching characters, and $t$ is the number of transpositions.
