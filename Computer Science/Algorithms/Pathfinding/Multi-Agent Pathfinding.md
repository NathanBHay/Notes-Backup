Multi-agent pathfinding is an expansion upon traditional [[Pathfinding|pathfinding]] that has the added constraint of multiple agents moving concurrently, without collisions. Formally the problem can be defined as a three tuple of $k$ agents $\langle G,s,t\rangle$ where $G=(V,E)$ is the graph, and $s:[1,\dots,k]\to V$ maps an agent to a source, and $t:[1,\dots,k]\to V$ maps an agent to a target vertex. Time is assumed to be discrete, with each step representing a single action. An action is a function $a:V\to V$ such that given a starting vertex $v$ it can traverse to $v'$ using $a(v)=v'$. Agents have the option to move using this function or to wait. A sequence of actions $\pi=(a_1,\dots,a_n)$ and an agent $i$ can be denoted by $\pi_i[x]$. This represents the first $x$ actions in $\pi$ starting from the source $s(i)$. A sequence of actions is a **single-agent plan** for agent $i$ if and only if executing this sequence of actions in $s(i)$ results in being at $t(i)$. That is if it has actions to get from the start to end. The solution is therefore a set of $k$ single-agent plans.

There are two common objective functions that are found within MAPF. The first is **make span** which finds the maximum amount of time steps to reach all targets. The second is **sum of costs**, also called flow-time, which finds the sum of all time steps required by each agent.

Once an agent reaches a target there are a few assumptions of what happens to it. The first approach is to **stay at the target vertex**, the other is to **disappear at the target vertex**. 

# Conflicts
A **conflict** in MAPF occurs when two agents collide in a way. A **solution** is considered valid if there are no conflicts. The types of conflicts allowed define the difficulty of the problem. Therefore given a pair of single agent plans $\pi_i$ and $\pi_j$ we find:
- **Vertex conflict** occurs if they are planned to occupy the same vertex at the same time. This means $\pi_i[x]=\pi_j[x]$.
- **Edge conflict** occurs when a plan paths agents through the same edge. This means $\pi_i[x]=\pi_j[x]$ and $\pi_i[x+1]=\pi_j[x+1]$.
- **Following conflict** occurs between two paths if one agent is planned to occupy a vertex that was occupied by another agent in the previous time step.
- **Cycle conflict** occurs between a set of single agent plans $\pi_i,\pi_{i+1},\dots,\pi_j$ if and only if in the same time step every agent moves to a vertex that was previously occupied, forming a rotation cycle.
- **Swapping conflict** occurs if and only if the agents are planned to swap locations as the same time. This means that $\pi_i[x+1]=\pi_j[x]$ and $\pi_j[x+1]=\pi_i[x]$.

# Variants
Beyond the traditional MAPF approach there have been a multitude of different approaches studied. These can be broken down through the way that they change the problem definition.

A common change to MAPF is the introduction of a **weighted graph**. These graphs include:
- **$2^k$-neighbour grids** are restricted of weight graphs in which every vertex represents a cell in a two-dimensional grid. The move actions of an agent in a cell are all its $2^k$ cells where $k$ is a parameter. Costs are based on Euclidean distance. For example an $8$-neighbour grid has diagonal moves with costs $\sqrt{2}$ and $1$ in cardinal directions.
- **Euclidean space** is a generalization of MAPF where every node in $G$ represents a point $(x,y)$ and edges representing the adjacency.

A **feasibility rule** refers to the requirement of a MAPF solution. Some unique feasibility rules include:
- **Robustness** where rules are designed to ensure a solution considers inadvertent delays in execution. This means that it plans a sufficient buffer of delays of up to $k$ time steps without conflicts.
- **Formation rules** are restrictions to move actions of an agent dependent on the location of other agents not related to collisions. 

**Anonymous MAPF** allows for any agent to end up at any target location in the list. This can also be changed to ensure only one-to-one mappings between agents and targets.

**Coloured MAPF** which agents are grouped into teams with each team having a set of targets. This can be further generalized with agents and targets have multiple teams.

**Online MAPF** also called **lifelong** means that agents exist over a changing set of source and targets. A **partial solution** to a MAPF problem is mapping of agents to paths such that each agent is either not mapped to a path or mapped to a single path starting from it source. This has two classifications that can be used to make hybrid models. These are:
- **Warehouse model** where there is a fixed number of agents that are assigned a new target after fulfilling the last.
- **Intersection model** where new agents may appears with only one task.

# Benchmarks
To benchmark these algorithms many common techniques are used. In general the process involves choosing a map. After which the amount of sources and targets increase until the algorithm can't find a result. 

The maps used for benchmarking usually follow 5 categories. These being:
- **Video game maps** which use data collected from video games. These maps are useful in representing possible locations that may be difficult for pathfinding.
- **Open grids** where the limit is more so the amount of agents that can run without conflicts.
- **Random grids** where obstacles are generated randomly. Effective in finding how good an algorithm is used generally.
- **Warehouse grids** which are inspired by real-world autonomous warehouses.

Generation of sources and targets can be done through:
- **Random generation** where all targets and sources are randomly created. This is the most common approach.
- **Clustered** where agents and targets are randomly placed near current agents and targets. This is used to make problems more difficult.
- **Designated** where a predetermined place is found for all targets and sources.
