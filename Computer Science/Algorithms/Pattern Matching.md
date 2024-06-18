The **exact pattern matching problem** is given a string $T[1..n]$ and a pattern $P[1..m]$ find all occurrences if any of $P$ in $T$. The goal of this problem is to minimise the number comparisons. An expansion of this problem is the **fuzzy-pattern matching problem** which approximates pattern matches given a certain threshold. 

# Naive Approach
The naive approach to pattern matching simply compares if at each letter within $T$ the pattern $P$ starts. Given the first letter matches now compare $T[i+j-1]=P[j]$ for each letter in the pattern. A full match returns the position. This approach in the worst case takes $(n-m+1)\cdot m$ or $O(mn)$ time complexity.

A basic improvement to this algorithm is in shifts. An algorithm can decrease computations by remembering previous comparisons and jumping to the next case of $P[1]$. These shifts can decrease the characters.

# Gusfield's Z-Algorithm
Gusfield's Z-Algorithm is a preprocessing algorithm used to find the structure of the string as to allow for faster exact pattern matching. Z-algorithm provides a way to create a faster pattern matching algorithms with [[Pattern Matching#Boyer-Moore Algorithm|Boyer-Moore]] and [[Pattern Matching#Knuth-Morris-Pratt|Knuth-Morris-Pratt]] all using the algorithm to help with their skipping strategies.

The algorithm works by finding the Z-values of a each character in a string. A **Z-value** is the length of the longest sub-string starting at position $i$ that matches its prefix (start), meaning $S[i..i+Z_i+1]=S[1..Z_i]$. The **Z-values** for a string are the set of values $\{Z_i,\text{ for }2\leq i\leq n\}$ for the string $S[1..n]$ . For a string the $Z_i$-box is defined as the interval of the longest sub-string or $[i..i+Z_i-1]$ of $S$. 

For every string there exists $r$ which is the **right-most endpoint** of all Z-boxes at or before $i$. This means $r_i$ is the largest value of $j+Z_j-1$ over $1<j\leq i$. Every string also has a **left end** which is the left end of the z-box that ends at $r_i$.

Gusfield's Z-algorithms computes $\{Z_i, Z_i-box,l_i,r_i\}$ for each non-starting position. This is done efficiently by keeping the most recently calculated $l$ and $r$ while creating a list of z-values. Given a string $S[1..n]$ the Z-algorithm computes all the Z-values for the string in $O(n)$-time.

The algorithm's begins with computing $Z_2$ by explicit comparison of characters $S[2..]$ with $S[1..]$ until a mismatch is found. After this the $l$ and $r$ are found as $r\gets Z_2 + 1$ and $l \gets 2$ or $0$ for both if there are no matches. 

The **first case** finds if the $k$ is outside the right-most $Z$-box meaning it can't use previous information and must use more comparisons to find $Z_k$. Specifically this means:
- Compute $Z_k$ by comparing $S[k..q-1]$ with $S[1..q-k]$ until a mismatch is found at some $q\geq k$.
- Then if $Z_k>0$ then $r\gets q-1$ and $l\gets k$. This means if $Z_k=0$ then no need to update $l$ and $r$.

The **second case** finds if $K$ is inside the right-most Z-box. In this situations it must find:
- If $Z_{k-l+1}<r-k+1$ (and $k\leq r$) then $Z_k\gets Z_{k-l+1}$, as the box doesn't need to extend the string.
- If $Z_{k-1+1}\geq r-k+1$ (and $k\leq r$) then the box needs to be extended by comparing $S[r+1]$ with $S[r-k+2]$ until a mismatch occurs. If a mismatch occurs at position $q\geq r+1$ then $Z_k\gets q-k$, $r\gets q-1$, and $l\gets k$.

## Z-Algorithm for Pattern Matching
The algorithm can be used to find linear time pattern matches through a process of constructing $S$ from the concatenated string $P+\$+T$ and preprocessing it with the Z-algorithm.  Where there exists a match for any $i>m+1$ for all $Z_i$. This algorithm has a time complexity of $O(n+m)$.

# Boyer-Moore Algorithm
The Boyer-Moore algorithm improves upon the naive method by successively aligning the pattern with text and checks for complete alignment. After a mismatch the pattern is shifted with respect to the new alignment. This is handled through the addition of three new rules. Right-to-left scanning, bad character rule, and the good suffix rule.

Boyer Moore's algorithm using Galil's optimisation allows it to achieve a runtime of $O(n+m)$ where $n$ is text length and $m$ is pattern length. An addendum to this is that the bad character algorithm is restricted by $O(m\cdot \mathcal{N})$ where $\mathcal{N}$ is the size of the alphabet, which is closer to its real complexity however most literature assumes that the size of the alphabet is constant.

## Right-to-Left Scanning
Boyer-Moore follows a right-to-left scanning structure. This means at any iteration it compares the last character in the pattern with the aligned text character until it reaches the start of the pattern. 

## Bad Character Rule
The bad character rule is done with the function $R(x)$ which finds the position of the rightmost occurrence of $x$ and shifting the pattern to the right to be aligned with the mismatched character. More formally this can be viewed as:
$$R(x)=\begin{cases}\text{Position of the rightmost occurence of }x\text{ in }P&\text{if }x\in P\\0&\text{Otherwise}\end{cases}$$
If a mismatch occurs at $k$ in $P[1..m]$ then let $x$ denote the character of the mismatch $T[j+k-1]$. This means that it is safe to shift the pattern by $\max(k-R(x), 1)$. The value $R(x)$ is usually calculated as a preprocessing step.

The **extended bad character rule** replaces the function with: 
$$R_k(x)=\begin{cases}\text{Position of rightmost occurence of }x\text{ to the left of }k\text{ in the }P&\text{if }x\in P\;\&\;x\text{left of }k\\0&\text{Otherwise}\end{cases}$$
From this we are able to make a table from the pattern's length. Which allows us to find $k-R_k(x)$. This can be done in $O(|\mathcal{N}|m)$ time and space where $\mathcal{N}$ is the alphabet of $T$ and $P$. The bad character rule is good for alphabets with many characters as it decreases the need to check multiple times.

## Good Suffix Rule
The good suffix rule is the idea that given a suffix of $T$ that is found within $P$ we can shift to allow for the suffix to align with the pattern. To implement this you need to store the rightmost occurrence of the suffix within a table. This can be done by finding $Z_i^{\text{suffix}}$ for $P[1..m]$. Where $Z_i$ is found by scanning backwards. From this we can calculate a **good suffix** as $gs(j)=i$ where $j=m-Z_i^{\text{suffix}}+1$ for each index $i$ of $P$. Additionally an extra entry to the table needs to be added to ensure proper program execution. This approach however ignores future occurrences of the same pattern. To rectify this we calculate a matched prefix.

The **matched prefix** is used for cases where there is no good suffix ie: $gs(i)=0$. In this case the matched prefix, which is calculated as the largest matching prefix from $P[i..]=P[1..]$. This can be computed by running the Z-algorithm on the string. After this traverse backwards finding $mp(i)=\max(Z_i,mp(i+1))$. 

### Galil's Optimisation
Galil's optimisation is a way to decrease the amount of unnecessary comparisons by using the good suffix's knowledge of their being matching prefixes or suffixes to skip a certain amount of text within the main comparison loop. This is done by holding a $\text{start}$ and $\text{stop}$ variables that given good suffix values is used will be $\text{start}\gets p-m+k+1$ and $stop\gets p$. In the case the matched prefix is used it finds $\text{start}\gets1$ and $\text{stop}\gets mp(k+1)$.

# Knuth-Morris-Pratt
The Knuth-Morris-Pratt Algorithm (KMP) is a functionally worse version of the Boyer-Moore algorithm. It functions through a traditional method of finding cases where a jump is available. This works by finding the aligned prefixes of the pattern with the suffixes of the matched region of text. To achieve this you compute the $SP_i$-values which are the longest proper suffix for $P[1..i]$ that matches a prefix $P$, such that $P[i+1]\neq P[SP_i+1]$. This can be found by preprocessing the Z-values for the pattern and then for each value $j\in[m, 2]$ find $i\gets j+Z_j-1$ and then $SP_i\gets Z_j$. From this if a mismatch at position $i+1$ shift the pattern right by $i-SP_i$ places, otherwise if $P$ is found in $T$ shift the pattern by $m-SP_m$ places. This algorithm therefore has a worse case complexity of $O(m+n)$ 

# BWT for Pattern Matching
							The [[Data Compression#Burrows-Wheeler Transform|Burrows-Wheeler Transform]] can be used for pattern matching in $O(m)$ time. This algorithm is particularly efficient for cases where the pattern is small and the text is large. The algorithm functions by first finding the BWT of $T$. After this initialisessstwo pointers on the encoded string $sp\gets1$ and $ep\gets n$. These pointers can then be updated each iteration by finding:
$$\begin{align}sp&\gets\text{rank}(P[i])+\text{nOccurences}(P[i], L[1..sp))\\ ep&\gets\text{rank}(P[i])+\text{nOccurences}(P[i], L[1..ep])-1\end{align}$$
Where $i$ is from $m$ (length of $P$) to $1$. This works by finding the range of suffixes that start with the character $P[i]$ for every respective character until matches are found. Once the final $sp$ and $ep$ are found we know the range of suffixes that are equal to the pattern $[sp,ep]$. Using this range you can convert the positions to the original places within the string to find all occurrences. In cases where $ep<sp$ there are no valid matches.

# Bitap
Bitap also called shift-and or shift-or is a pattern matching algorithm that takes advantage of bit-manipulations to allow for fast pattern matching across a small alphabet. The algorithm works by first preprocessing the set of [[Bit Fields|bit masks]] across the alphabet, and then using a bit comparison to compare the two bit arrays. Together with the shift, each iteration is able to quickly match patterns within the text. Bitap is a commonly used in the fuzzy pattern matching as it allows for easy extensions to incorporate [[String Metrics|string distance]].
```pseudo
	\begin{algorithm}
	\caption{BitAp($T[0..n], P[0..m]$)}
	\begin{algorithmic}
		\State $B \gets \emptyset$
		\For{$c \in \Sigma$}
			\State $B[P[c]] \gets \sim0$
        \EndFor
        \For{$i \gets 0$ \To $m$}
	        \State $B[P[i]] \gets B[P[i]]\;\&\;\sim(1 << i)$
        \EndFor
        \State $S \gets \sim0$
        \For{$i\gets 0$ \To $m$}
	        \State $S \gets (S << 1)\;|\;B[T[i]]$
	        \If{$S < 1 << m - 1$}
		        \Return $i - m + 1$
            \EndIf
        \EndFor
	\end{algorithmic}
	\end{algorithm}
```