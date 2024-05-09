Similar to [[Computer Science Problems|computer science]], mathematics has a series of canonical problems which relate to a variety of mathematical concepts and theorems. The following is a page devoted to these miscellaneous problems.

# Josephus Problem
The Josephus problem contends there exists a circle of people who are being chosen every $k$ and removed from the circle. The goal of the problem is to find the places where a given person can stand to survive as the last member of the circle. The complexity of this problem is in the fact the group shrinks making it difficult to find whether a given position will survive the entire time.

The solution to this problem in a general form uses [[Algorithmic Paradigms#Dynamic Programming|dynamic programming]] to get a solution in $O(n)$ that is given by:
$$g(n,k)=\begin{cases}
0&\text{if } n=1\\
(g(n-1,k)+k)\bmod n&\text{otherwise}\\
\end{cases}$$
Another solution that works for small $k$ and large $n$ is to use dynamic programming but rather considered killing $k$-th, $2k$-th$,\cdots,(\lfloor n/k\rfloor k)$-th people as one step and then change the numbering. This results in a run-time of $O(k\log n)$ as near entire circles are considered for elimination. This can be given by the recurrence:
$$g(n,k)=\begin{cases}
0&\text{if } n=1\\
(g(n-1,k)+k)\bmod n&\text{if } 1<n<k\\
\begin{cases}
g(n-\lfloor\frac{n}{k}\rfloor,k)-n\bmod k+n&\text{if } g(n-\lfloor\frac{n}{k}\rfloor,k)<n \bmod k\\
\frac{k(g(n-\lfloor\frac{n}{k}\rfloor,k)-n\bmod k)}{k-1}&\text{otherwise}
\end{cases}&\text{if } k\leq n
\end{cases}$$
