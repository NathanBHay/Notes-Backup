String retrieval structures are [[Data Structures|data structures]] that function to store textual data in a way that allows for easy operations. These can be done through arrays or [[Tree Data Structures|tree data structures]]. They are similar to [[Search Trees|search trees]] however store data with overlapping data as to increase space efficiency and allow for unique operations. These trees trees usually rely upon an alphabet defined as $\Sigma$. This value is usually equal to the English alphabet however may be restricted for cases such as DNA, or increased for larger character sets.

Some common terminology for strings include:
- **Sub-strings** which are a string $S[i..j]$ found within a string.
- **Prefixes** which is the start of the string $S[1..j]$.
- **Suffixes** that are at the end of the string $S[i..n]$.

There are a variety of common string retrieval structures. With the main ones being:
- [[Prefix Trees]] which are a tree which represents all prefixes of a string.
- [[Suffix Trees]] which are trees which hold all suffixes of a string.
- [[Suffix Arrays]] which are arrays which hold all suffixes.

String retrieval structures are usually used for search operations such as [[Pattern Matching|pattern matching]] and related problems. 