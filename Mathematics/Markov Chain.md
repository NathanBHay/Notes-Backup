Markov chains are a [[Modelling|stochastic model]] that describes events as states where future states can be found from the previous state. This is done with a transition function which describes the [[Probability|probability]] that its next state is found given its current state $\Pr(X_{n+1}=x|X_n=x_n)$. The *Markov property* is this rule that only the current state is considered meaning the system's future states are independent of its past. This allows Markov chains to be a computationally efficient model.

Formally a Markov chain is a set of states $S=\{s_1,s_2,\dots,s_r\}$. Each state has a *transition property* from $s_i$ to $s_j$ where for each $\forall i: \sum_jp_{ij}=1$ as these are [[Probability#Random Variables|random variables]].  Representation of the transition function can be done through [[Graph Theory|graph theory]] or a [[Linear Algebra|transition matrix]]. In this approach we can also represent the current states a vector of Boolean states. This allows us to multiply the state vector $\pi_i$ by the transition matrix to find $\pi_iA$.

A trait of Markov chains is that we can calculate the probability that it will take $n$ steps to get to $j$ from $i$. This can be calculated by finding:
$$p_{ij}^{(n)}=\sum_kp_{ik}p_{kj}$$
The reason the above equation works is as we are finding all valid ways to get to $i$ from $j$. A faster approach can be to either use the state vector and multiply it $n$ times or to multiply the matrix by itself before computing $\pi_0A^n$, and looking at the correct position.

The long term behaviour of Markov chains sees them approach a steady state $P^*=\lim_{k\to\infty}P^k$.  During steady state analysis we need to find the cases where the state current state is equivalent to the next state. This can be found with the equation:
$$\pi A=\pi$$
This equation is similar to an [[Matrix Decomposition#Eigenvectors|eigenvector]] where the eigen value $\lambda=1$. In addition to this as we know that all values within $\pi$ need to sum to one:
$$\sum_{i\gets0}^r\pi[i]=1$$
Therefore if we solve for the two previous equations we can find the steady state of the Markov chain.

# Markov Chain Properties
There are various properties that Markov chains can follow. These properties include:
- **Ergodic** Markov chain has every state accessible from every other state given enough steps. These have unique behaviour where given enough iterations the initial state is forgotten. This means that for a chain $P$ we can find $PP^*=P^*$.
- **Regular** Markov chains if some power of the transition matrix has only positive elements.

# Absorbing Markov Chains
Absorbing Markov chain has at least one state where the probability of changing to a different state is 0. All states should also be reachable to an absorbing state in a finite number of steps. All states which are not absorbing are called **transient** states. The canonical representation groups transient states at the start of the matrix and absorbing at the end. Mathematically:
$$P=\begin{bmatrix}Q&R\\0&I_r\end{bmatrix}$$
Where $Q$ is a $t\times t$ matrix, and $R$ is a nonzero $r\times t$ matrix. And where $I_r$ is an [[Linear Algebra#Identity Matrix|identity matrix]]. In this absorbing chain the probability that a process is absorbed in $n$ is 1, meaning:
$$\lim_{n\to\infty}Q^n=0$$
This can be proven by minimising finding $m_j$ which is the minimum number of steps required to reach an absorbing state starting from state $\pi_j$. Letting $p_j$ be the probability that this will not occur in $m_j$ steps. Using these properties for the largest $m_j$ and $p$ we can find that the probability of not being absorbed in $mk$ steps is at most $p^k$. Therefore, the probability of not being absorbed goes to $0$ as $k$ increases.

## Fundamental Matrix
The **fundamental matrix** of an absorbing chain is the expected number of times the chain visits state $\pi_j$ starting at $\pi_i$ before absorption. This can be calculated as:
$$N=\sum_{k\gets0}^\infty Q^k=(I-Q)^{-1}$$
This equation is equivalent to the matrix equivalent of the [[Sequences#Geometric Series|geometric series]] can be computed as $(1-q)^{-1}$.

From the fundamental matrix we can compute the expected number of steps to be absorbed starting from state $\pi_i$. This can be computed as the value given by the $i$-th entry of the vector $N\mathbf{1}$ where $\mathbf{1}$ is a vector of 1's equal to the number of transient states. This works as we are finding the sum of all transient states before absorption.

The fundamental matrix can be used to find the probability from where starting from $\pi_j$ it will be absorbed. This can be calculated as:
$$B=NR$$
An approximation of this can be calculated as $P_{ij}^k$ for a large value of $k$, as the limit of this is equivalent to $B$.