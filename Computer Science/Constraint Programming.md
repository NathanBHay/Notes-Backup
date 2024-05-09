Constraint programming is a [[Programming Paradigms|paradigm]] for solving constraint satisfaction problems and [[Combinatorial Algorithms|combinatorial optimization]] problems. This is done through declaratively stating the constraints for a solution which is used to test the feasibility of solutions. Constraint problems are modeled through three main concepts that are used to build **models**. These are:
- **Variables** that represent the decisions, with concrete values being a choice made.
- **Constraints** which rule out incompatible choices for variables within its *scope*. This results in choices being *satisfied* or *violated*.
- **Parameters** that specify problem instances.

Models result in a set of valid choices called a **feasible assignment**. This can be used to derive a solution. Formally a constraint programming language attempts to solve a constraint satisfaction problem. This problem can be defined a 3-tuple $\mathcal{P}=\langle\mathcal{X},\mathcal{D},\mathcal{C}\rangle$, where $\mathcal{X}$ is a set of decision variables $\mathcal{X}=\langle x_1,\dots,x_n\rangle$, a set of domains for each variable $\mathcal{D}=\langle D(x_1),\dots,D(x_n)\rangle$ where $D(x)$ is the finite set of all potential values of $x_i$, and a conjunction of constraints $\mathcal{C}=C_1\land \cdots\land C_m$. A given constraint $C_i=(\mathcal{X}_i,\mathcal{R}_i)$ is defined as a set of variables and a relation $\mathcal{R}_i\subset\mathcal{D}(i_1)\times\dots\times\mathcal{D}(i_k)$. These constraints can be subdivided into three common relation categories:
- **Extensional** constraints enumerate the set of values that satisfy them.
- **Arithmetic** constraints which use conditionals to constraint values.
- **Logical** constraints are defined semantically.

There are a variety of constraint modelling paradigms that determine the type of constraints used as well as the type of solver. These are:
- **Constraint programming** which uses any type of constraint, with a standard CP solver.
- **Boolean Satisfiability** that only has Boolean variables, and uses a B-SAT solver.
- **Linear programming** only has real variables, using linear constraints. These usually don't use a search algorithm.
- **Mixed-Integer programming** has integer variables. It uses a solver that combines linear programming and search algorithms/

# Domains
Many constraint programming languages use domains as a way to define value restrictions upon decision variables. Similar to constraints this restricts the possible values a variable can take before constraint satisfaction is verified. These domains are a subset of the type defined with additional arguments allowing for the tightening of the domain. The most common domains found within constraint programming languages are:
- **Boolean** domains where only true and false values are valid.
- **Integer**/**Rational** domains which only allow numbers.
- **Interval** domains which restrict integers or rational numbers over a certain interval.
- **Linear** domains where linear functions are used for the variables.
- **Finite** domains where a finite set is used as the values.
# Enumerables
Enumerables are a common feature found within constraint programming languages. Enumerables function to provide a variable name to a given integer value. This allows for problems to take a more human readable form.

# Constraint Solving
Constraints programming languages are solved with a separate solver software. These solvers traditionally use a [[Graph Theory#Trees|tree]] search algorithm that [[Algorithmic Paradigms#Backtracking|backtracks]] to possible solutions.
