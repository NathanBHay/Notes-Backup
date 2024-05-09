A hash table is a [[Data Structures#Lookup Tables|lookup data structure]] that keeps a key that is able to be used to find a value. This attempts to solve the 'dictionary' problem where there needs to exist a structure which can be searched for values while using key to retrieve values. This results in a storage and search process which is $O(1)$. There are three main operations of a hashtable are:
- **Insert** which inserts an item with a given key into the dictionary.
- **Delete** which removes an item with a given key into the dictionary.
- **Lookup** which finds the item given a valid key.

All keys come from a universe $\mathscr{U}$ typically consisting of integers or letters converted to integers. **Direct addressing** is the simple way of storing a hashtable where a direct address table of size $|\mathscr{U}|$ is used where any key $k$ slots into the table at location $k$. This approach results in $O(1)$ for all main operations however is only practical if the universe is small.

**Hashing** is a solution to the direct addressing problem that reduces the universe to a manageable size which uses a **hash function** where $h:\mathscr{U}\to \{0,1,\dots,m-2\}$, maps all keys onto the reduced universe. The items are therefore stored in a table of size $m$ but at the added disadvantage of collisions due to hash functions assigning the same key.

# Collision Resolution
There are a variety of common collision resolution methods available. Some of the most common methods are:

## Chaining
**Chaining** involves the process of maintaining a linked list at every position and inserting all elements into a linked list at a position. Assuming the function maps keys evenly then the expected number of items in each chain is $n/m$, where $n$ is the number of items in the hashtable, and $m$ is the table size. This value is also called the load factor. This results in a time complexity of $O(1+\frac{n}{m})$, where given $m \geq n$ then the average case is $\Theta(1)$.

## Open Addressing (Probing)
Open addressing is the process of storing all items in the table directly. This means that $m \geq n$ for the table to function. Open addressing changes so whenever a collision occurs an alternative location is chosen. This is done through a method called **probing**. This adjusts the hash function to suggest a sequence of locations. This can be written as:
$$h(k,i):\mathscr{U}\times \mathscr{N}\to \{0,1,\dots,m-1\}$$
A disadvantage of this method is increased deleting overhead as deletions now need to avoid deleting elements between other elements. The time complexity of the probing process follows $O(\frac{1}{1-\frac{m}{n}})$, which can also be written as $O(\frac{m}{m-n})$. This means that the amount of probes when $\frac m n=0.5$ should be around 2. Therefore, on average time complexity should be similar to $\Theta(1)$.

#### Linear Probing
Linear probing is a a technique which probes adjacent locations within a table until an empty slot if found. This results in a hash function which follows:
$$h(k,i)=(h'(k)+i)\bmod m$$
Where $h'(k)$ is the original hash function. In theory linear probing performs poorly as it is susceptible to **primary clustering**, where many keys end up sharing the same location. Despite this it is still fairly efficient due to cache locality.

#### Quadratic Probing
Quadratic probing attempts to avoid the primary clustering problem by making keys jump further away. This still results in a function which is prone to **secondary clustering** where keys with the same hash will always probe similar elements. It uses constant values $c_1$ and $c_2$ and follows a sequence of:
$$h(k,i)=(h'(k)+c_1i+c_2i^2)\bmod m$$

#### Double Hashing
Double hashing aims to avoid secondary clustering by using a second hash function to determine the distance between hashed elements. This eliminates secondary clustering however may be less efficient if the hash functions are slow. It follow:
$$h(k,i)=(h_1(k)+ih_2(k))\bmod m$$

## Cuckoo Hashing
Cuckoo Hashing is a hashing scheme that guarantees worse-case $O(1)$ operations assuming a sufficiently good hash function. It functions by maintaining two hashtables $T_1$ and $T_2$ with two hash functions $f(k)$ and $g(k)$. If a collision occurs move the collided item to another table. This results in a lookup function that attempts to search both tables before returning null. An insertion function follows a procedure of checking both tables and then calling a probing method on each table.

# Hash Functions
A hash function is the function which is used to allocate a key within the table. The main goal of this function is to minimize the probability of collisions occurring. Ideally a hash function will be uniform and result in a function that maps onto integers such that $h(k)=|km|$. This however doesn't work in practice as if most keys turn out to be close then the hash function will result in many collisions. Despite this, many hash functions assume that all keys are equally distributed.

## Divisional Hashing
The most common method of hashing is using keys that are integers. A basic method of achieving this is through a basic hash function of:
$$h(k)=k\bmod m$$
This function produces a hash value that is well distributed provided $m$ is chosen well. Avoiding a power of 2 is important as it will only use the least significant bits. Primes which aren't close two a power of two are strong choices.

## Multiplicative Hashing
Similar to divisional hashing multiplicative hashing is done on integers. It follows the idea of a constant $A$ where $0<A<1$ that is selected in addition to a fractional part of $kA$ which is $kA-|kA|$. This is then scaled by $m$ resulting in a hash that follows:
$$h(k)=|m(kA-|ka|)|$$
Unlike the divisional method $m$ doesn't effect the quality of the hash which enables a hashes to be sped up by using bitwise operations. The decision of a suitable $A$ is influenced by the characteristics of the keys. According to Knuth a good choice is:
$$A=\varphi^{-1}=\frac{\sqrt {5} -1}{2}\approx0.61803\dots$$
## Polynomial Hashing
Polynomial hashing is a technique which is common for hashing strings. Given a string $S[1..n]$ we associate each character with a numeric value such as its position in the alphabet. This results in a function given by:
$$h(S)=((S[1]x^{n-1}+S[2]x^{n-2}+\dots+S[n-1]x+S[n]) \bmod p)\bmod m$$
Where $p$ is a prime with the constraint $p>m$, and $x$ is a base that should be higher than the maximum attainable value of $S[i]$. This evaluates the polynomial hash for a given string term-by-term and will lead to a time complexity of $O(n^2)$ or $O(n\log n)$ if fast exponentiation is used.

This can be improved given **Horner's method** which states given a polynomial $p(x)=a_0+a_1x+a_2x^2+\dots+a_nx^n$, we can evaluate it in $O(n)$ time by computing the sequence of values to find $b_0$ through:
$$\begin{cases}
b_n=a_n\\
n_{n-1}=a_{n-1}+b_nx\\
\vdots\\
b_0=a_0+b_1x
\end{cases}$$
Polynomial Hashes allow for rolling of values to be done. This means that the adjacent strings or substrings can be quickly computed in linear time rather than quadratic.

## Universal Hashing
Universal hashing rather than using a single hash function randomly selects from a **universal family** of hash functions $\mathscr{H}$. This family satisfies:
$$\Pr_{h\in \mathscr{H}} \{h(k)=h(k')\} \leq \frac{1}{m},\text{ for all } k\neq k' \in \mathscr{U}$$
The average time complexity will still be $\Theta(1+\frac{m}{n})$, as universal hashing is not strong enough to guarantee $O(1)$. Some common universal hashing families include:
- The set of all hash functions, which is unrealistic.
- $\mathscr{H}= \{h_{a,b}(k)=\big( (al+b) \bmod p \big)\}$ for all $0<a<p$ and all $0\leq b<p$ for a fixed prime number such that $p \geq u$. This family has the disadvantage that table slots above $p\bmod m$ may be less likely to be occupied. Its main advantage is that it only stores three integers.
- $\mathscr{H}= \{h_{a,b}(k)=((ak+b) \bmod) \gg (\log u - \log m)\}$ for all odd $0<a<u$, and all $0\leq b< \frac{u}{m}$. This family works when $u$, $m$, the universe and table size are powers of two. This function then amount to simply taking the highest $\log m$ bits from the product $(ak+b)\bmod u$  which is very fast. This means all operations are bitwise, and thus faster.
