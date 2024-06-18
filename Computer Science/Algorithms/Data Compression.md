Data compression or bit-rate reduction algorithms attempt to encode information in less bits than its original representation. There are two approaches to this are lossless and lossy compression.

**Lossless** compression finds ways to reduce the amount of bits without a reduction in information. This usually uses statistical redundancy to remove repeated data. This process of statistical redundancy calculates what space is considered wasted by considering the entropy of data. Examples which use lossless compression include  [[Data Compression#Burrows-Wheeler Transform|Burrows-Wheeler transform]].

**Lossy** compression reduces the amount of bits with an acceptance of a certain loss of information. This tries to balance the loss of information with the space reduction. Most of these compression algorithms leverage the medium they are within, such as pictures and music leveraging the data's order.

# Code Words
One trait of compression is the difference between code words. Where a **code word** is a segment of information that represents a value, for example a character in ASCII can be represented in binary or octal. 
- **Fixed length code word** means that each code word is of equal size. Fixed length compression can be done through traditional transformation methods.
- **Variable length code word** means that code words have different lengths. In the case of variable length compression, it can be done by assigning frequent symbols to shorter code words.

The issue with variable length code words is that decoding can become ambiguous as there is no way to know where a code word starts and ends. Therefore to achieve a uniquely decodable word all symbol's code words must have a different prefix to others. This is called **prefix-free** codes or *instantaneous codes*.

The **optimal code** can be seen as the minimal encoding of a text within the provided format.

A common approach to encoding data is through a **binary encoding**. This uses [[Number Systems#Binary|binary]] digits to represent the data. A **minimal binary encoding** is a representation where the most significant bit is 1.

# Run-Length Encoding
Run-length encoding (RLE) is a way of compressing data in a lossless way by storing consecutive code words as a count. This approach is efficient for data that has adjacent repeated elements. For example an encoding of $aaabbaa$ would be $(3, a),(2,b),(2,a)$. This approach while simple requires the string to be in a form that can be easily compressed.

# Huffman Coding
Huffman coding is a method of generating reliable prefix-free code words for characters. From the character frequencies it is able to find code words of length ordered by the frequency. Huffman's algorithm is used for finding a table of variable-length codes with a [[Algorithmic Paradigms#Greedy|greedy]] approach. 

The algorithm works on a set of unique characters with their computed frequencies. To construct an encoding, each character can be seen as a [[Graph Theory#Trees|leaf]] within a [[Tree Data Structures#Binary Tree|binary tree]]. Therefore to find an encoding simply join the two characters with the smallest frequencies to form a new node which is connected to the tree, maintaining the invariant that $l<r$. Where the edge connecting the left node has weight $0$, and the right has weight $1$. After add the new node to the list of nodes, and remove the previous. Continue this until a full tree is constructed. Once this is done traverse the tree to every leaf concatenating the edges to find a binary string for every character.

A common approach to computing this is using a [[Abstract Datatypes#Priority Queue|priority queues]] to hold the list priorities of letters and pointers to trees. This approach takes $O(n\log n)$ time where $n$ is the number of symbols. The alternative approach is the use of two [[Abstract Datatypes#Queue|queues]] that hold the weights, but aren't ordered by them. In this approach during each step the two lowest values are chosen from either queues. This results in a $O(n)$ time algorithm. Additionally to minimise variance caused by an unbalanced tree tie break by choosing the original queue.

# Universal Encoding
A **universal code** is a prefix-free code that maps positive integers onto binary code words, with the additional property that it doesn't need to know the true [[Probability Distribution Models|distribution]], but rather knows that it is monotonic ($\Pr(i)\geq\Pr(i+1)$ for all positive $i$). This means that the expected length of code words are within a constant factor of the expected lengths of optimal code for that true distribution.

## Elias Omega Code
Elias Omega code is a universal code for encoding positive integers. The strategy for encoding an integer $N$ follows by encoding $L_i\gets\text{Length}(\text{minimum\_binary\_code}(L_{i-1}))-1$ where $L_0=N$. This allows computation of the **length component** $L$ for the code component of $N$. The minimum binary code being the binary number. A trait of this is that when encoding the length component flip the leading 1 to 0. Once the length component is equal to $0$ stop the encoding process. The decoding process, given a code word $C[1..]$ follows:
```pseudo
	\begin{algorithm}
	\caption{Elias$\Omega$Decode($C[1..]$)}
	\begin{algorithmic}
		\State $component \gets \null$
		\State $p \gets 1_{dec}$
		\State $r \gets 1$
		\While{\True}
			\State $component \gets C[p..p+r-1]$
			\If{most-significant bit is $1$}
				\Return $(component)_{dec}$
			\Else
				\State flip most-significant bit to 1
				\State $p \gets p+r$
				\State $r \gets (component)_{dec}+1$
            \EndIf
        \EndWhile
	\end{algorithmic}
	\end{algorithm}
```

# Burrows-Wheeler Transform
The Burrows-Wheeler transform (**BWT**) also called **block-sorting compression** is a [[Data Compression|data compression algorithm]] which rearranges a string into a format which can be easily compressed. The algorithm has two parts, the compression section and the decompression section.

BWT can also be used for $O(m)$ [[Pattern Matching#BWT for Pattern Matching|pattern matching]] where $m$ is the size of the pattern, given the string has been compressed.

## Compression
The *compression algorithm* functions by generating the cyclic rotations of the input $S$. This means that for $i\in[n,1]$ we find $S[i..]+S[..i]$, for example $cab$ is a rotation of $abc$. After all [[Counting Methods#Permutation|permutations]] are found, they are sorted. From this we find the compressible string as the last characters of the sorted table. A naive approach to this can be done in $n\log n$ with a basic rotation and a [[Sorting Algorithms|sort]]. An improvement to this uses [[Suffix Arrays#Prefix Doubling|prefix doubling]] to construct the array in $n\log^2 n$. Algorithms such as [[String Retrieval Structures#Ukkonen's Algorithm|Ukkonen's algorithm]] are able to further improve this generation to be $O(n)$.

## Inversion
BWT can be reversed from the generated output of the function. This *inverse function* can be thought of as a series of concatenations and sorts. This inverse functions by inserting the encoded string into a matrix and sorting it. After this concatenate the encoded string to the the front of the sorted array in the matrix to create string pairs. After this sort the strings again. This process continues until the length of the string sorted. From this the row with the row with the terminating character at the front is the true string. When finding the inverse this sorting method usually isn't used however similar principles are used when finding the original input. 

**LF-mapping** is the process used to invert the BWT. It works off the idea that letters in L, the last column in the matrix, always go before letters in F, the first column string  in the matrix, as the sorted matrix is of cyclic permutations. Where F can be found by sorting L. This means that given $k\leq1$ occurrences of $x$ in the string in the sorted matrix there will be $k$ occurrences in the same row of the sorted matrix. This means that for any letter $L[i]=x$ in the L column, these has to be a suffix starting with this specific $x$ in F. Meaning that $F[pos]=x$. From this we are able to derive $pos$ as:
$$pos=\text{Rank}(x)+\text{nOccurences}(x,L[1..i))$$
Where $\text{Rank}(x)$ is the position where $x$ first appears in $F$. And where $\text{nOccurrences}(x,L[1..i])$ is the number of times $x$ appears in $L[1..i)$. 

# LZ77
Lempel-Ziv algorithm (LZ77) is an encoding which uses a [[Algorithmic Paradigms#Sliding Window|sliding window]] approach to compression to find repeated substrings within the string. It uses a *search window* (also called the dictionary) and a *look-ahead buffer* (also called the buffer) to restrict the search of repeated substrings. The algorithm functions by finding the longest repeated occurrence from the dictionary in the buffer. This match is used to find $(\text{offset}, \text{length}, c)$ which is the distance from the start of the buffer to where the match starts in the dictionary, the length of the matched characters, and the first mismatched character. After this the dictionary adds $l+1$ where $l$ is the match length from the start of the buffer. With the buffer removing the front $l+1$ and adding $l+1$ to the end from the input.

For example with a dictionary of $abcde$ and a buffer of $cda$ we would find $(3,2,a)$ as the distance from $c$ to $c$ in $abcdecda$ is $3$, with a match length of $|cd|=2$ and $a$ being the source of the mismatch. After this we remove $abc$ from the dictionary and $cda$ from the buffer and add it to the window now having $decda$ in the window. This continues until the input is done.

The pseudocode for the algorithm is written below where $S$ is the input:
```pseudo
	\begin{algorithm}
	\caption{LZ77($S, windowSize, bufferSize$)}
	\begin{algorithmic}
		\State $W \gets \emptyset$
		\State $L \gets S[..bufferSize]$
		\State $result \gets \emptyset$
		\While{$S \neq \emptyset$}
			\State $match \gets$ Longest repeated occurence of input in window
			\State $d \gets$ distance to start of $match$
			\State $l \gets$ \Call{length}{$match$}
			\State $c \gets$ mismatched character
			\State $result.$\Call{append}{$(d, l, c)$}
			\State $W \gets W[l+1..] \doubleplus L[..l+1]$
			\State $L \gets L[l+1..] \doubleplus S[..l+1]$
			\State $S \gets S[l+1..]$
        \EndWhile
	    \Return $result$
	\end{algorithmic}
	\end{algorithm}
```

Decoding follows a process of using these triplets to produce the dictionary and buffer for each iteration. This allows the original word to be built from these triplets.

## LZSS
Lempel-Ziv-Storer-Szymanski is a variation of LZ77 reduces complexity of the result by keeping small length mismatches in a different format. This uses a bit flag at the start of the tuples to find the cases where:
- Match lengths $\geq3$ kept as $(0, \text{offset}, \text{length})$ where offset and length are same as before.
- Match lengths $<3$ kept as $(1, c)$, where $c$ is the mismatched char.