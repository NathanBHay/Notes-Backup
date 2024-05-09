Genetics algorithms are a method of solving optimization problems considered [[Combinatorial Algorithms|combinatorial]], through a heuristic based on natural selection, and other evolutionary occurrences. In general evolutionary algorithm operate on a population based approach where individuals within the population are optimised with processes such as mutation, selection, recombination, and selection.

Evolutionary algorithm's correctness can be proven by **Hollard's Schema Theorem**, also called 'the fundamental theorem of genetic algorithm' states that schemata with above-average fitness increase exponentially in frequency of successive generations. This theorem is based upon the idea of a infinitely large population and as a result is less expressive in smaller sets.

# Genetic Algorithm
Genetic algorithms in particular use concepts found within genetics as to propose a solution to optimisation problems. Genetic algorithms operate on a population of candidate solutions, where each candidate solution is a part of a generation that is measured against a function. These algorithms are used on data commonly called the **chromosome** which describes how the data is structured and how it will be changed in the next generations. The first generation is created from a random pool of solutions however each successive generation will be formed from the previous. This is done by first ranking members of the generation with an **objective function**. From here a new generation is generated through a set of rules, usually containing one of these three:
- **Selection** which stochastically selects elements called parents and adds them to the next generation.
- **Crossover** which combines two parents together for the next generation.
- **Mutation** which randomly changes a parent to add to the next generation.

Effects from these functions will lead to a selection process which will eventually remove mediocre results as it refines its search. The process of generation continues until a halting condition is reached.
