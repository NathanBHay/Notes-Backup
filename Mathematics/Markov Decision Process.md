Markov decision process (**MDP**) expands upon [[Markov Chain|Markov chains]] to have an [[Artificial Intelligence|intelligent agent]] that determines the actions given a state. This means for any state $s$ in the chain their exists a set of actions $A_s$ which determines the probabilities at any given step. This allows the modelling of uncertainty in a decision driven environment.

Formally a Markov decision process is a 4-tuple of $(S,A,P_a,R_a)$, where:
- $S$ is the state space, equivalent to states in a Markov chain.
- $A_s$ is the actions space, given a current state $s$.
- $P_a(s,s')$ is the probability that given an action $a$ in state $s$ that the next state will be $s'$. In terms of chains this is the transition property given an action.
- $R_a(s,s')$ is the reward earned from taking action $a$ in state $s$, given the next state is $s'$.

The **policy** $\pi(s)$, which maps $S\to A$, is a function which determines the next action given a state. This function can be probabilistic or deterministic depending on the problem. Once a policy is chosen results can now be computed as a traditional Markov chain.

# Utility
The goal of using MDP is the [[Optimisation|optimisation]] of the policy $\pi^*$. To compute how good a policy is **utility function** $U([r_0,\dots,r_\infty])$ which functions as the objective function. One approach to computing this function is the **expected discounted sum over a potentially infinite horizon**:
$$E\Big[\sum_{t=0}^\infty\gamma^tR_{a_t}(s_t,s_{t+1})\Big]$$
Where $a_t=\pi(s_t)$ is the action given a policy and $\gamma$ is the **discount factor** $\gamma\in[0,1]$ used to weight later actions lower by taking a smaller factor.

An alternative approach to this is the **H-step return** which calculates the suitability given a certain amount of steps in the future. It can be found given a *time horizon* $H$ as:
$$E\Big[\sum_{t=0}^{H-1}R_{a_t}(s_t,s_{t+1})\Big]$$

# MDP Algorithms
MDP is traditionally solved through using [[Algorithmic Paradigms#Dynamic Programming|dynamic programming]] to solve for the values and the policies. These algorithms assume a finite state and action space and calculate both a policy $\pi$ and its values $V$. These are done with the two equations:
$$V(s)=\sum_{s'}P_{\pi(s)}(s,s')(R_{\pi(s)}(s,s')+\gamma V(s'))$$
$$\pi(s)=\arg\max_a\sum_{s'}P_{\pi(s)}(s,s')(R_{\pi(s)}(s,s')+\gamma V(s'))$$
Through these equations you can compute the given policy and its associated values. Depending on the algorithm and implementation these equations converge at different rates.

## Value Iteration
Value iteration is a variation upon these dynamic programming algorithms that starts by computing the values until they converge before a final policy computation step. This approach is simpler to implement however suffers from a slower convergence rate that other variations. Below is an example of this approach.
```pseudo
	\begin{algorithm}
	\caption{ValueIteration($S,P,R,\gamma$)}
	\begin{algorithmic}
		\State Initialise $V(s)$ arbitrarily
		\State $\Delta\gets0$
		\While{$\Delta<0$}
			\For{$s\in S$}
				\State $v\gets V(s)$
				\State $V(s)\gets\max_a\sum_{s',r'}P_a(s,s')(R_a(s,s')+\gamma V(s')$
				\State $\Delta\gets\max(\Delta,|v-V(s))$
            \EndFor
        \EndWhile
		\Return $\pi(s)=\arg\max_a\sum_{s',r'}P_a(s,s')(R_a(s,s')+\gamma V(s')$
	\end{algorithmic}
	\end{algorithm}
```

## Policy Iteration
Policy iteration starts similar to value iteration by computing the values until it converges, however has the additional step of policy improvement which is done by finding the best action according to a look-ahead. This will find an optimal policy. This converges faster than value iteration.
```pseudo
	\begin{algorithm}
	\caption{PolicyIteration($S,P,R,\gamma,\eta$)}
	\begin{algorithmic}
		\State Initialise $V(s)$ arbitrarily
		\State $\Delta\gets\eta$
		\While{$\Delta>0$}
			\For{$s\in S$}
				\State $v\gets V(s)$
				\State $V(s)\gets\max_a\sum_{s',r'}P_a(s,s')(R_a(s,s')+\gamma V(s')$
				\State $\Delta\gets\max(\Delta,|v-V(s))$
            \EndFor
        \EndWhile
		\State $stable\gets$ \True
		\For{$s\in S$}
			\State $old-action\gets\pi(s)$
			\State $\pi(s)\gets\arg\max_a\sum_{s',r'}P_a(s,s')(R_a(s,s')+\gamma V(s')$
			\If{$old-action\neq\pi(s)$}
				\State $stable\gets$ \False
            \EndIf
        \EndFor
		\If{$stable$}
			\Return $V, \pi$
        \EndIf
		\State Go to policy evaluation
	\end{algorithmic}
	\end{algorithm}
```

# Partially Observable MDP
**Partially observable Markov decision process** (**POMDP**) further generalises MDP to model [[Artificial Intelligence#Environment Types|environments]] that are partially observable. This means the agent requires a sensor model that maps the history of observations to actions. As a result this approach works based on probabilities that given an action the new

Formally this can be defined as a 7-tuple $(S,A,P,R,\Omega,O,\gamma)$ where the states $S$, actions $A$, transition probabilities $P$, reward $R$, and discount value $\gamma$ are the same however with the addition of:
- $\Omega$ the set of observations.
- $O$ the set of conditional observation probabilities.