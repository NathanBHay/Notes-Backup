A set is an unordered collection of distinct **elements** or members. A set is equal if all elements are the same. To define a set you do either:
- $\{ x_1,\dots,x_n \}$ is the set with those elements.
- $\{ x : P(x) \}$ is the set with property $P(x)$.

Through this both [[Functions]] and [[Relations]] can be defined through set notation.

If an item is an element of a set is can be written as $x \in S$. For a finite set $S$ the number of elements is defined as $|S|$.

A **subset** is written as $A \subseteq B$ where all elements is $A$ are within $b$. Every set is a subset of itself and a blank set $\emptyset$ is a subset of every set. A **superset** is written as $A \supseteq B$ and is the same as $A \subseteq B$. A **subset** can be specified by the **characteristic function** $\chi_A$ which tells elements of B are in A. Written as:$$\chi_A = \begin{cases}
1 &\text{if} \; x \in A \\
0 &\text{if} \; x \notin A
\end{cases}$$A **Power Set** written as $\mathcal{P}(n)$ is defined as the set of all subsets. The amount of elements within this set is equal to $2^n$.

# Common Sets
There are sets of numbers that are commonly found within mathematics, and thus have been given a letter to represent them. These numbers are:
- **Natural Numbers** $\mathbb{N}$ which is the set of whole numbers greater than zero.
- **Integers** $\mathbb{Z}$ which is the set of all whole numbers.
- **Rationales** $\mathbb{Q}$ which is all real numbers formed by dividing one number by another.
- **Irrationals** $\mathbb{P}$ which is all real numbers that aren't rational, which is $\mathbb{R} \backslash \mathbb{Q}$.
- **Algebraic Numbers** $\mathbb{A}$ which is all numbers which can solve a quadratic.
- **Transcendentals** which doesn't have a symbol but is found as $\mathbb{R} \backslash \mathbb{A}$.
- **Real Numbers** $\mathbb{R}$ which is the set of all non-complex numbers.
- **Imaginary Numbers** $\mathbb{I}$ which is the set of all imaginary numbers.
- **Complex Numbers** $\mathbb{C}$ which is the set of all numbers.

# Set Operations
A set operation is a [[Relations]] done on a set. Some common ones include:

| Operation | Symbol | Note |
| --- | --- | --- |
| Union | $A \cup B$ | A And B|
| Intersection | $A \cap B$ | A Or B |
| Difference | $A-B$ | Only A |
| Symmetric Difference | $A \bigtriangleup B$ | A Nand B |
| Complement | $\overline {A}$ | Not A |
These can be shown through the Venn diagrams:
![[Pasted image 20220424155000.png|#invert|300]]

# Ordered Pair
An ordered pair is a set of items which have an order. These are written as $(a,b)$. These can be implemented with a set of sets where on set notes what is in it and the other notes the order.

**Cartesian Product** is a set of ordered pairs which is written as:
$$ A \times B = \{ (a,b) : a \in A \text{ \& } b \in B\}$$
The amount of ordered pairs within this set is found by $|A| \times |B|$.

# Partition
The partition of a set is a set of subsets such that each element in in exactly one subset. This can be seen within [[Sorting Algorithms]].

# Interior & Boundary
An interior point is one in Euclidean space where if given a circle drawn around the point that circle would be entirely within the set. A boundary point is one where the centre of the circle is on the edge of the set. A set or region is considered **closed** if it consists entirely of boundary points, and is **open** if it only has interior points.

A point is **bounded** if the interval's boundary points are included within the interval. It is **unbounded** if they aren't

# Cantor's Diagonal Argument
Cantor's diagonal argument is a method of proving that given an infinite number of unique sets of length $1$ to $\infty$ that a new set can always be created by changing the diagonal element of each respective set to generate a new unique set. This means one-to-one sets are uncountable. 
