Recursion is a type of [[Relations|relation]] that is commonly found within [[Algorithms|algorithms]]. It is the process of self reference within a relation as to form a definition or algorithm. [[Proofs#Induction|Induction]] is a closely related process as they are both on a set of natural numbers and have two steps. In the case of recursion these two steps are an initial value, and a recurrence relation. Recursion is a form of induction that is for a definition rather than a proof.

A recurrence relation is **homogenous** if each term is a multiple of another. A homogenous equation has a characteristic property that if solution $t_n=f(n)$ exists then solution $t_n=cf(n)$

Recursion is used within algorithms to solve smaller sub-problems as to build to the full problem. Therefore problems that can be decomposed to a level that is solvable and combined to form an answer are commonly found with recursion. These algorithms must converge to a base case. Some common algorithms which include recursions are binary search, [[Sorting Algorithms#Merge Sort|merge sort]], summations, and products.

Recursion has a close relation to **iteration** as both can be implemented instead of each other. When recursion is used instead of iteration a auxiliary function is commonly required. Opposingly when iteration is used instead of recursion a [[Abstract Datatypes#Stack|stack]] or **accumulators** are commonly required. Recursion is used instead of iteration as its easier to prove, and more natural in some cases. Its main disadvantage is the run-time and memory overhead.

# Recursive Notation
**Direct recursion** calls are calls to the same function, while **indirect** or **mutual** recursion is done through multiple methods that call between each other. There are three types of recursion are defined on the amount of recursive calls. These are:
- **Unary** where there is a single recursive call.
- **Binary** where there is two recursive calls.
- **n-ary** which is *n* recursive calls.

**Tail-recursion** is where the result of the recursive call is the result of the function. Simply this happens when recursion doesn't do anything on its way back, as the final recursive call found the result. This allows the memory to close the previous stack frame.

# Recursion Solutions
Recursive relations are commonly found as a way to represent recursive algorithms with mathematical notation. It follows the structure:
$$
T[n]=\begin{cases}c, &n=0 \\ T[n-1]+c,&n>0\end{cases}
$$These equations follow a base case, and a recursive case. Where [[Algorithmic Paradigms#Divide and Conquer|divide and conquer]] is represented with $T[\frac{n}{b}]$, while [[Algorithmic Paradigms#Decrease and Conquer|decrease and conquer]] is represented with a $T[n-b]$. These equations can be further expander with odd special cases denoted by the input of n. This results in equations such as:
$$
\begin{align}T[1]&=0\\T[2n]&=T[n]-c_1\\T[2n+1]&=T[n]+c_2\end{align}
$$
Solving recursive equations convert the recursive relation into a non-recursive function. There are three approaches to solving these: telescoping with induction, recursive trees, and masters theorem.

## Telescoping
Telescoping is an approach of solving recursive relations through a brute force approach that relies upon intuition. This can be done with by:
$$
\begin{aligned}
&T[n]=T[n-1]+c\\
\Rightarrow &T[n-1]=T[n-2]+c\\
\Rightarrow &T[n]=(T[n-2]+c)+c
\end{aligned}
$$
Repeating this process will yield a pattern of expansion that can be described by an equation. To easier visualize this process put the base case into the $T[n]$ case as to work out how it expands at each step.

## Recursive Trees
Recursive Trees are a easy way to visualise the recursion at every step. These are especially helpful for algorithms which use divide and conquer. It works by visualising each recursive case as another sub tree. This then can be solved by adding up all the nodes of a certain depth. From there the subproblem size is derived by finding when $i=1$ from the predicted growth of the divide and conquer function. For example $T[n/4^i]$ has a subproblem size of $\log_4{n}$. From here each recursive depth is found with a summation. This then finally is derived into a real equation.

## Master Theorem
The master theorem is an easy way of solving recursive equations through the use of a standard formula. It follows the rule:
$$
T[n]= aT[n/b]+f(n)
$$
Where $n/b$ is the decrease in subproblem size, and $a$ is the amount of recursive calls. From here there are three cases, these are:
1. If $f(n)=O(n^{\log_b{a}-\epsilon})$  for a constant $\epsilon >0$, then $T(n)= \Theta (n^{\log_b{a}})$.
2. If $f(n)=\Theta(n^{\log_b{a}})$ , then $T(n)= \Theta (n^{\log_b{a}}\log n)$.
3. If $f(n)=\Omega(n^{\log_b{a}+\epsilon})$  for a constant $\epsilon >0$, and if $af(n/b) \leq cf(n)$ for a constant $c<1$ and all large $n$, then $T(n)= \Theta (f(n))$.

Intuitively this states than in case 1 if the subproblems at each level increase by a certain factor the value $f(n)$ will be smaller than the right side. Thus, the time complexity is capped by the last level. In case 2 if the sub problem at each level is nearly the same $f(n)$ will equal the right side. Therefore the time complexity will be $f(n)$ times the total number of levels. In case 3 the cost of the subproblems decrease at each level by a certain factor. Therefore $f(n)$ will be larger and therefore be the time complexity.

For a decreasing case this equation changes to:
$$T[n]=aT[n-b]+f(n)$$
1. If $a<1$ then $T(n)=O(f(n))$, as the inner function is the largest part of the function.
2. If $a=1$ then $T(n)=O(n\cdot f(n))$, as the function increases at every step.
3. If $a>1$ then $T(n)=O(a^{\frac{n}{b}}\cdot f(n))$, since the function increases at each step.