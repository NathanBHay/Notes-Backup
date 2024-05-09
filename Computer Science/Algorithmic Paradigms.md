Algorithmic paradigms are the model which the design of an [[Algorithms|algorithm]] is based upon. These design patterns can be commonly found throughout computer science and are used to speed up the efficiency of a program.

# Brute Force
A brute force algorithm is on which manually solves all the problems until a final result is found. It is one of the slowest solutions however guarantees the best result as it has searched all possible examples. There are multiple types of brute forcing algorithm however **enumeration** is the most common. Where enumeration uses simple loop structures to search all candidates.

# Decrease and Conquer
Decrease and conquer is a process in which the algorithm solves smaller sub-problems as to find a result. This decomposition of the problem is done at a constant amount each time, therefore decreasing the size of the problem. Recursion is commonly used to do this.

# Divide and Conquer
Divide and conquer is also used to decompose problems into smaller disjoint sub-problems but instead divides the problem by a constant factor. These sub-problems when divided are partitioned by a certain part of the algorithm into disjoint problems that are able to be solved separately. This is done commonly through [[Recursion|recursion]] as it allows the variables to be split and recalled as to find a base case. Some common examples of divide and conquer are:

# Greedy
A greedy algorithm is one which finds the best decision at every step as to produce an effective result. While this isn't usually the best solution is does find a local optimal solution.

# Backtracking
Backtracking is a type of brute forcing algorithm where the previous states are kept in mind as it attempts to get to the goal state. Thus, a solution is built incrementally, backtracking whenever a candidate path is proved to be inefficient. This is similar to a depth first search algorithm. This can only be applied to problems with a **partial candidate solution** where an answer can be generated at each step. Backtracking is usually faster than brute-force enumeration.

# Dynamic Programming
Dynamic programming is a decomposition paradigm that focuses on solving of repeated calculations. These problems usually are optimization problems which require multiple calculations of the same segments of data. This is usually done by storing values with an [[Abstract Datatypes|abstract datatype]], a [[Memory#Cache|cache]] or any similar techniques. As a result of using these techniques there usually is a memory drawback to dynamic programming as while it decreases time efficiency it will increase space. Most dynamic programming problems can be expressed through a recursive relation, which mathematically can be called a **Bellman equation**.

When finding a solution to a dynamic programming problem the strategy is to characterize the structure of the solution, recursively define the value, compute in a bottom up solution, construct optimal solution from computed information. This means the problem has **optimal sub-structure** as the smaller subproblems can be combined to obtain a solution.

During dynamic programming optimal solutions can be reconstructed through two main methods. These are **backtracking** where the solution is found by going back through the memoized data to find the optimal route. The obvious disadvantage of backtracking is the fact another loop needs to be ran usually leading to $O(2\cdot f(n))$. **Decision tables** are another method of constructing an optimal solution by constructing a table of decisions that mirrors the memoization table. This is then used during each iteration or recursion to find the solution. Due to the construction of a new table the space complexity is doubled.

# Coding Patterns
A coding pattern can be seen as a method of [[Computer Science Problems|problem solving]] that uses a certain common technique to solve a problem. This can be seen as a lower level to an [[Algorithmic Paradigms]] as it describes a technique rather than an architecture of an algorithm. Coding patterns are useful to study in cases where basic problems (such as those for internships) need to be solved.

## Sliding Window
Sliding window is a technique which solves problems related to a sequence of data, for example within a [[Abstract Datatypes#List|list]]. It functions by moving a *window* of elements that are analysed at any given time. The process of sliding the window 

## Two Pointer
Two point is an approach which uses two variables that hold pointers to a sequence. This process usually involves moving these pointers as to find the problem's solution.