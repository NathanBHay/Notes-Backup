Within Statistics counting methods quantify randomness as to illustrate the amount of possibilities of a given event. The two basic counting rules are
- **Addition Principle** which states there are $a$ ways to do $a$ and $b$ ways to do $b$ then $a+b$ total ways to do one thing.
- **Multiplication Principle** states that if you do both $a$ and $b$ then in total there are $a \times b$ ways.

# Permutation
A Permutation or an **Ordered Selection without Repetition** is written as:
$$ n(n-1)\dots(n-r+1)= \frac {n!} {(n-r)!}$$

# Combination
A Combination or a **Unordered Selection without Repetition** is written as:
$$ {n \choose k} = \frac {n!} {k!(n-k)!}=\frac{n(n-1)\dots(n-k+1)}{k(k-1)\dots(1)}$$
This can be read as $n$ *choose* $k$, where $n$ is the upper index, and $k$ is the lower index and seen as the $k$th order. Under the traditional *combinatorial interpretation* these numbers are restricted to only positive integers, however through an extended definition it can be found that:
$${r\choose k}=\begin{cases}\frac{r!}{k!(r-k)!}&\text{if } k\geq0\\0&\text{if }k<0\end{cases}$$
Some common formula's to memorize for combinations are for the first three basic cases for combinations. These are:
$${r\choose 0}=1\quad{r\choose 1}=r\quad{r\choose 2}=\frac{r(r-1)}{2}$$

## Pascal's Triangle
Pascal's Triangle is an arrangement of numbers associated with a series of combinations starting from $0\choose 0$, to $n\choose r$, where $n$ is the column and $r$ is the row.
![[Pasted image 20220425104808.png|#invert|300]]
The **Hexagon Property** is another weird property which states that all surrounding numbers in a hexagon around a given number can be put into two alternating multiplications and find the same number. For example, around the number $4$ finds $1\cdot6\cdot5=1\cdot3\cdot10$.

## Identities
Found from Pascal's triangle the **addition formula** is the most important identity. It states that all internal elements in Pascal's triangle can be found by the sum of the previous two adjacent elements. This can be written as:
$${n \choose r} = {n-1 \choose r} + {n-1 \choose r-1}\quad\text{for } 1 \leq r \leq n$$

The **symmetry identity** is the pattern that every internal element is the same as an outside element. This leads to the rule:
$${n \choose r} = {n \choose n-r}\quad\text{for } 0 \leq r \leq n$$
The **absorption identity** is an identity which allows movement of values out from binomial coefficients. It finds that:
$${r\choose k}=\frac{r}{k}{r-1\choose k-1}\quad\text{for }k\neq0$$
This identity is commonly modified to keep the lower index through:
$$(r-k){r\choose k}=r{r-1\choose k-1}$$
**Summation on the upper index** is a pattern using the addition formula that finds the value of $n$ choose $m$ by adding values with the same lower index:
$${n+1\choose m+1}=\sum_{0\leq k\leq n}{k\choose m}$$

## Binomial Theorem
The binomial theorem observes that given a polynomial term to the power of $n$ the expanded terms follow pascal's triangle. A formal definition of this is written as:
$$(x+y)^n = {n \choose 0} x^n y^0+{n \choose 1} x^{n-1} y^1 +\dots+ {n \choose n} x^0 y^n \;\text{ for }\; n \in \mathbb{N}$$
This equation however can be simplified to:
$$(x+y)^n = \sum_{k=0}^n {n \choose k} a^{n-k} b^k$$

# Ordered Selection with Repetition
An Ordered Selection with repetition is a sequence of $r$ terms within a set of $n$ elements written as:
$$n \times n \times \dots \times n = n^r$$

# Unordered Selection with Repetition
An Unordered Selection with Repetition is a multiset of $r$ elements from set $n$ written as:
$${n+r-1 \choose r} = \frac {(n+r-1)!} {r!(n-r)!}$$

# Counting Principles
There are a few key principles within counting that enable easy formalisation and proofs of certain ideas.

## Pigeonhole Principle
The pigeonhole principle states that if $n$ items are placed in $m$ containers then one container has $\frac n m$ items.

## Inclusion-Exclusion Principle
In general if you have two sets the amount of elements in $|A \cup B|$ is found by $|A| + |B| - |A \cap B|$. However, as you increase the amount of sets you follow the process:
1. Add the sizes of all sets.
2. Subtract the sizes of all even-way intersections.
3. Add the sizes of all odd-way intersections.
