A problem within computer science can be defined as a formulated question which requires a agent to solve an issue.  Formally a problem can be seen to have 5 components. These are:
- An **initial state** which is used to represent the starting position within the problem.
- A description of the possible **actions** available to the agent.
- A **transition model** which that represents the result of taking an action from a given state.
- The **goal test** that checks if the given state fulfil the goal.
- **Path cost** that assigns a numeric cost to each path through the transition model.

The initial state, actions and transition model define the **state space** of the problem. This state space can be represented by a [[Graph Theory|graph]]. Commonly the path cost is used to calculate the overall cost of a solution.

# Common Problems
Computer science has many common problems, also called **toy problems** or **canonical problems** which relate to real world technical issues and the given [[Algorithms#Computational Complexity|computational complexity]] associated with them. These problems are usually provide either simple solutions to a problem described to be computationally complex, or are combinatorial problems that are solved with heuristics or other methods. The following problems are a set of general problems that don't constitute their own page. For general problems related to graph theory check [[Graph Problems|general graph problems]].

## Travelling Salesman
The travelling salesman problem (TSP) is a problem which asks given a list of cities and their associated distances, which can be represented as a graph, find the possible [[Graph Theory|walk]]. This problem is NP-Complete.

## Graph Colouring
The graph colouring problem tries to find a graph where each node has a colour that is different from the adjacent node. This problem is considered NP-Complete. This problem can be formulated to be a satisfaction problem if the goal is to find a graph with $k$ colours. It can also be expanded to an optimisation problem that finds the least amount of colours required to colour the graph.

## Knapsack
The knapsack problem is a series of problems which all deal with the idea of a knapsack which has a maximum weight it can carry, $C$ and a set of items with weights and values that can be held by the knapsack. The goal is to maximise the value found within the knapsack while ensuring the items don't go over the weight limit. This problem is further subdivided into a variety of extra restraints that further contextualise the problem.

#### Unbounded Knapsack
Unbounded knapsack follows the original prompt however all items can be taken an unlimited amount of times. The equation resulting from these restrictions can be solved with the [[Recursion|recursive]] relation:
$$\text{MaxValue}[c]=\begin{cases}
0&\text{if } c<w_i \text{ for all i}\\
\max_{1\leq i \leq n} (\text{MaxValue}[v_i,c-w_i)&\text{otherwise}
\end{cases}$$

#### 0,1 Knapsack
The 0,1 knapsack problem adds the restriction that each item can only be taken once. This results in a problem which is more difficult than unbounded as now the program needs to check if the selected item is already in the knapsack. The solution to this problem results in a pseudo-time complexity of $O(NC)$, where $N$ is the number of items and $C$ is the knapsack's maximum weight. The real time complexity of this problem is $O(2^BN)$, as the amount of space to store $C$ is equal to $2^B$, where $B$ is the number of bits. A possible recursive solution would follow:
$$\text{MaxValue}[i,c]=\begin{cases}
0&\text{if } i=0\\
\text{MaxValue}[i-1,c]&\text{if } w_i>c\\
\max(\text{MaxValue}[i-1,c],\text{MaxValue}[i-1,c-w_i)&\text{otherwise}
\end{cases}$$
## N-Queens
The N-queens problem finds the positions of $n$ queens that can be placed on a board.

## DP Problems
[[Algorithmic Paradigms#Dynamic Programming|Dynamic programming]] problems are a common type of problem which use the paradigm usually as a method to teach it.

#### Coin Change
The coin change is a problem which states that given a set of coins of different denominations $C=(x_0,x_1,\dots,x_n)$, what is the minimum amount of coins to get to a certain amount $V$. This problem is common as it would normally result in a time complexity of $O(|C|^V)$, however through the use of [[Algorithmic Paradigms#Dynamic Programming|dynamic programming]] the problem becomes $O(|C|\cdot V)$. Through the use of a bellman equation the problem can be described as:
$$\text{MinCoins}[v]=\begin{cases}
0&\text{if } v=0\\
\infty&\text{if } v<c[i] \text{ for all i}\\
\min_{1\leq i \leq n} (\text{MinCoins}[v-c[i]])&\text{otherwise}
\end{cases}$$
#### Rod Cutting
The rod cutting problem states that given a rod of size $n$, and a table that states how much each length $i$ up to $n$, gives in terms of $p_i$, what is the maximum amount of prices. This problem is solved with dynamic programming as it builds up a solution of cuts that maximise it's value. The solution to this problem can be view as $r_n=\max (p_i, r_1+r_{n-1},r_2+r_{n-2},\dots,r_{n-1}+r_1)$, which represents a series of disjoint sub-problems that can be solved individually. As a result of this trait the problem can be viewed as $r_n=\max_{0\leq i \leq n} (p_i+r_{n-1})$.

#### Optimal Matrix Multiplication
Optimal matrix multiplication is another common dynamic programming problem as it exhibits optimal substructure in that during the multiplication of multiple matrices the amount of operations can be minimised through the order of multiplication. This is as matrix multiplication is associative. Thus, there exists a function $\text{DP}[i,j]$ that is equal to the minimum number of multiplications of $(A_i,A_{i+1},\dots,A_j)$ for all $1\leq i\leq j\leq n$. A recurrence to solve this equation uses the sequence of columns $(c_1,c_2,\dots,c_n)$ to find the optimal number of multiplications for the sequence. This gives the relation:
$$\text{DP}[i,j]=\begin{cases}
0&\text{if } i=j\\
\min_{i\leq j \leq k} (\text{DP}[i,k]+\text{DP}[k+1,j])+c_kc_jc_{i-1}&\text{if } i<j
\end{cases}$$
Therefore to find the solution simply find $\text{DP}[1,n]$, for the sequence.

## K-Armed Bandits
Multi-armed bandit models a [[Reinforcement Learning|reinforcement learning]] problem where a gambler is stationed at a row of slot machines.  This gambler needs to decide which machines to bet on as to maximise profits given their current information. More formally, the problem states that their are $k$ actions each with an expected reward. With each action $A_t$ at the timestep $t$ corresponds to a reward $R_t$ with an expected reward given by $q_*(a)=E[R_t|A_t=a]$, and a maximisation of $\arg\max_aq_*(a)$.

The **action-value method** solution calculates the value from the mean reward of the given choice at a timestep. This allows for an estimation of the quality of the solution. 
$$Q_t(a)=\frac{\sum_{i=1}^{t-1}R_i\cdot\delta_{A_t=a}}{\sum_{i=1}^{t-1}\delta_{A_t=a}}$$
Where $\delta_{A_t=a}$ is $1$ if the predicate $A_t=a$ is true, otherwise $0$. This means as more data is added the prediction will converge to the true value. One approach to using this value is the **epsilon-greedy** strategy which behaves greedily at a probability of $\epsilon$. The algorithm follows:
$$A_t=\begin{cases}\max Q_t(a)&\text{with probability }1-\epsilon\\\text{random action }a&\text{with probability }\epsilon\end{cases}$$
This problem can be further modified with an maximum number of time-steps. An incremental implementation of this considers only its rewards and estimates after $n+1$ rewards. This then computes:
$$Q_n=\frac{\sum_{i=1}^{n-1}R_i}{n-1}$$
From this we can derive a part of the Q-learning equation for the next iteration:
$$Q_{n+1}=Q_n\frac1n[R_n-Q_n]$$
Adding uncertainty to this can be done by adding an [[Optimisation#Exploration vs Exploitation|exploration]] term.

##