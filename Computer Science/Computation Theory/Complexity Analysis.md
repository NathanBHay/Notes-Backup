The analysis of [[Algorithms|algorithms]] the process of determining the required computational resources that an algorithm takes. These computational resources can be divided into the *time* it takes for an algorithm to run, and the *space* the algorithm requires. There are a variety of common methods to analyse the time and space algorithms take. The most common methods of algorithm analysis follow:
- **Operation Counts**, is a method of determining complexity based upon how many of a certain operation is triggered.
- **Step Counts**, is a method of finding the number of steps and their frequency.
- **Counting Cache Misses**, is a method of determining the complexity by the number of memory references.
- **Asymptotic Complexity**, which is defined as a limit of the step count.
- **[[Amortized Analysis|Amortised Complexity]]**, which averages asymptotic complexity over operations.

# Asymptotic Complexity
Computational complexity is a relation used to measure the difficulty to compute a program. This relation is defined as $T(n)$ which is equal to the relative amount of instructions  or space required to compute input size $n$. This relation can be defined within two contexts, these are:
- **Time Complexity** which is the time it takes given the input. Output-sensitive complexity is the time-complexity given an output.
- **Space Complexity** which is the space it takes given the input. Auxiliary space complexity is the amount of space taken excluding the initial input.

Complexity analysis is done through multiple methods all which look at different aspects of an algorithms complexity.

## Big-O
The most important is **worst-case analysis**, or **big-Oh** complexity which is the inclusive upper bound of the time or space an algorithm takes. This means the largest cost of an algorithm is maximally restricted to the big-O complexity. It is represented with $O(f)$. Mathematically it is represented as $f \in O(g)$, which means for at least one choice of a constant $k>0$ there exists a constant $a$ such that the inequality $0 \leq f(x) \leq k\cdot g(x)$, for $k \in \mathbb{Z}^+$ holds.

## Big-$\Theta$
**Average-case analysis** or **big-Theta** complexity represents the average computational resources for an algorithm, averaged over all possible inputs. This allows more acute analysis of algorithms as the general amount of time an algorithm takes is computed rather than the worst case. To devise a average case a [[Discrete Probability|probability distribution]] over all inputs must be analysed. Another, method is to use a [[Random Number Generation|randomized algorithm]] to find the **expected complexity**.

## Big-$\Omega$
**Best-case analysis** or **big-Omega** is used to represent the best case time complexity of an algorithm. This means the lower bound for the computational resources for an algorithm. It is usually ignored as improvements to average and worst case complexity prove more significant.

## Little-$o$ & Little-$\omega$
**Little-oh** complexity is similar to big-Oh however is the exclusive upper bound. This means that the statement never grows to the amount, and thus $f\in o(g)$ exists where all constants $k>0$ satisfy the inequality $0 \leq f(x)<k\cdot g(x)$. This means there are cases where $O(f)$ can be true while $o(f)$ can be false. Therefore, it is a stronger statement.

**Little-omega** complexity is similar to little-o in that it represents the exclusive bound but rather than inclusive except for in this case the lower bound. This means

## Common Complexities
Complexity can be defined with the following classes from smallest to largest:
- **Constant** time complexity is defined as $O(1)$.
- **Logarithmic** time complexity is defined as $O(\log n)$.
- **Linear** time complexity is defined as $O(n)$.
- **Super Linear** time complexity is defined as $O(n\log n)$.
- **Quadratic** time complexity is defined as $O(n^2)$.
- **Cubic** time complexity is defined as $O(n^3)$.
- **Exponential** time complexity is defined as $O(2^n)$.
- **Factorial** time complexity is defined as $O(2!)$.

## Complexity Types
A constant space complexity is commonly called an **in-place** algorithm. This means it only takes constant space in addition to the input.

**Output Sensitive Algorithm** have results that are dependent on the output rather than the input. These algorithm follow different methods to minimize the amount of operations done.
