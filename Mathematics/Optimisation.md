Optimisation is simply the selection of the best element regarding a particular criteria. It selects this element usually based upon the maximisation or minimization of an *objective function* that represents inputs that could be used for the problem. This can be formalised as given a function $f:A\to \mathbb{R}$ where $A$ is some set of real numbers, find an element $x_0 \in A$ such that $f(x_0) \leq f(x)$ for all $x \in A$. The 'less than equal to' being flipped for maximisation. These problems assume that the data being optimised can be visualised as a smooth manifold. Optimisation problems can be sub classified into multiple categories, these are **continuous** and **discrete** optimisation. Beyond this optimisation techniques can be further categorised by how they operate. These techniques include:
- **Iterative algorithms** that operate to improve themselves after every iteration hoping that given as iterations grow the function is optimised, $\sum_{i=0} f(x_i) \leq f(x_{i+1})$. These functions can include ones that use heuristics.
- **Approximation algorithm**, that attempt to find the answer within $O(1)$ time using the data supplied by the initial state.

# Continuous
Continuous optimisation, commonly just referred to as optimisation, operates under the idea that the input of the objective function is real $A \in \mathbb{R}$. Due to this most continuous optimisation uses a differentiable function, that can be optimised with its derivative. Continuous optimisation approaches include:
- Hessian approaches that iteratively optimise using hessian matrices.
- [[Gradient Descent]] algorithms that attempt to use the derivative to jump from places within the

Continuous optimisation can be considered either **constrained** or **not constrained**. Constrained problems operate under the idea that the set of inputs is limited ($x \in [l,h]$), while problems without constrains have no limit to the inputs ($x \in \mathbb{R}$).

# Discrete
Discrete optimisation is the process of optimising data that can be considered discrete. These discrete values can be considered integers, or any other similar value ($A \in \mathbb{Z}$). Methods of solving these problems include:
- **[[Combinatorial Algorithms]]**, which deals with problems of a finite set of solutions with no value restrictions.
- **Integer programming**, which deals with problems where the input is restricted with integers.
- **Constraint programming**, which uses constraints to formalise the problem.
