Bayesian statistics functions on the central statement of **Bayes' Theorem** which allows a way to calculate [[Probability#Conditional Probability|conditional probability]]. This theorem is states:
$$\Pr(A|B) = \frac {\Pr(B|A)\Pr(A)} {\Pr(B|A)\Pr(A) + \Pr(B| \overline A)\Pr(\overline A)}= \frac {\Pr(B|A)\Pr(A)} {\Pr(B)}$$

# Bayesian Network
A Bayesian network is a [[Graph Theory|directed acyclic graph]] which represents a joint probability distribution. Nodes in the network are discrete or continuous random variables. The directed links represent a conditional probability based upon the parent, meaning $\Pr(X_i|\text{Parents}(X_i))$. Nodes that have parents are represented by a **conditional probability table** of all possible possibilities that effect the event, therefore any decision has infinite possibilities. Each row of the table adding up to one. This table can be calculated as the product of all possibilities $x_i$ in the node:
$$\Pr(x_1,\dots,x_n)=\prod_{i=1}^n\Pr(x_i|\text{Parents}(X_i))$$
A path is blocked given a set of nodes $E$ if there is a node $Z$ on the path for which at least on conditions holds:
- $Z$ is in $E$ and $Z$ has one arrow on the path leading in (chain).
- $Z$ is in $E$ and both path arrows leading out (common cause).
- Neither $Z$ nor any descendant of $Z$ is in $E$, and both path arrows lead into $Z$ (common effect).

A set of nodes $E$ d-separates two sets of nodes $X$ and $Y$, if every undirected path from a node in $X$ to a node in $Y$ is blocked given $E$.

## Node Types
There are three node types of found within Bayesian networks, these are:
- **Chance nodes** that have an associated probabilities of events happening possibly given the occurrence of other events
- **Decision nodes** don't take data but rather represent a choice required for the model to predict events.
- **Utility nodes** that allow decision nodes to work out the benefit/loss of taking a choice. Therefore, acting as a form of reward for the likelihood of an event happening.

Through using these more advanced node types you are able to construct models that rely on decisions and judge the reward based on the likelihood of multiple events happening.

# Naive Bayes Classifier
The naive Bayes classifier is a probabilistic [[Classification|classification]] algorithm that uses Bayes theorem. This can be done by assessing the likelihood of an event $a$ given a vector of features $b$, computed as $\Pr(a|b)$. These classifiers can usually be represented as a Bayesian network with one output and connections to all features.

Interestingly as our goal is classification during computation of the probabilities you can avoid calculation of all the features to find $\Pr(a_0|b)$ and $\Pr(a_1|b)$ as you know that  $\Pr(a_0|b)+\Pr(a_1|b)=1$ you can ignore calculation of $\Pr(b)$ in the denominator and just take the max $\max(\Pr(b|a_0))\Pr(a_0),\Pr(b|a_1)\Pr(a_1))$.