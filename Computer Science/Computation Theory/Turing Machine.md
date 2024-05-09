Turing machines are the most influential model of computation. They commonly define what is computable for modern computer architecture by prescribing a method for general computation. A Turing machine is described as an abstract machine that manipulates symbols on a tape given a set of rules. More formally a Turing machine consists of:
- An **input alphabet** that is a finite set of symbols denoted by $\Sigma$.
- A **tape alphabet** is a finite set of symbols denote by $\Gamma$ such that $\Sigma\subseteq\Gamma$. The tape alphabet additionally includes a special symbol used to represent an empty cell $\Delta$.
- A **tape** which is an infinite sequence single symbol cells from the tape alphabet.
- The **tape head** designates the current tape cell. This head can read, write and move one cell to the left or right.
- The **program** which is a collection of states and transitions. Each transition specifying $(state,\;symbol) \to(next\;state,\;next\;symbol,\;direction)$.

Any [[Formal Languages|language]] which can be recognized by a Turing machine is considered **Turing-recognizable**. The collection of these languages is normally seen as $L(M)$ for a TM $M$. A language can be considered co-Turing-recognizable if its complement $\bar M$ is Turing-recognizable.

From this model we can define computation as a series of discrete time steps where at any time the Turing machine reads a tape cell and follows a transition function to a new state. If this state is an accept state the computation ends and the string is accepted, if it is a reject state the input is rejected and if there is no transition for the current state and symbol the program crashes and the input is rejected. If none of these states occur then the computation can go on forever. From this we can say computation is **deterministic** as at any time the action to take is completely determined.

# Complexity
The [[Algorithms#Asymptotic Complexity|complexity]] of a Turing machine is defined within two categories the time and space complexity. The time complexity is the amount of steps taken by the Turing machine as a factor of the input..

## Space Complexity
The space complexity of a TM is the maximum number of cells that the TM scans given as a factor of the input The space complexity of a TM can be subdivided into deterministic and non-deterministic space complexity. Where the space complexity depends on the type of TM used for the computation. **Savitch's theorem** states that any non-deterministic TM can be made from a deterministic TM such that space complexity of the non-deterministic one is a subset of the deterministic space squared.

# Representations
Turing machines can be described as a graph similar to a finite automata. These can be written with nodes representing states and edges indicating transitions. Each edge has a label which representing a $symbol\to next\;symbol,\;direction$. Accept states can be represented as a square or a circle in a circle.

In addition to the graph format there also exists a table format to represent Turing machines. With every row representing states from and to, as well as the read, write and direction. These machines can be further **encoded** with this scheme representing every state, letter and direction as a series of symbols found within the language. This allows the creation of a encoded Turing machine. 

# Computing Functions
Due to the ability for Turing machines to write cells they can also be used to compute [[Functions|functions]]. This process for a given Turing machine $M$ defines a function as having a domain of $x\in\text{Accept}(M)$, such that the function maps all $x$ to a string on the tape after $M$ halts. A function can be considered computable if a Turing machine exists that can compute it.

# Universal Turing Machines
Universal Turing Machines take as input an encoding Turing Machine $M$ together with an input string $x$ to be used as input to $M$ as to simulate the execution of $M$ on $x$. This process involves reading the input string and marking it and reading the respective instruction. UTM's are important as they give a formal model of a **stored-program** computer. 

# Other Machines
In addition to Turing machines there are other abstract machines which exists to define computability. These usually involve an addition to a previously mentioned machine. Some examples include a queue automaton, a two stack PDA, and a nondeterministic Turing machine. All these examples can be defined as Turing machines and vias versa.

Variation of Turing machines also exist. Some examples include, allowing the tape head to stay still, or modifications to the tape such as two-way infinite, multiple tapes, and different tapes. Similar to the previous machines these are all also equivalent in their computation ability.

# Enumerators
An enumerator is a Turning machine which outputs a sequence of strings never accepting or rejecting. Additionally if the sequence is finite then the enumerator may stop but it's state doesn't matter. A language $L$ is considered enumerated by an enumerator $M$ given:
$$L=\{\text{all strings in the sequence outputted by }M\}$$
An enumerator is used to demonstrate if a language is Turing-recognizable, with one being recognizable if some enumerator enumerates it.

# Recursion Theorem
The recursion theorem is the idea that a Turing machine can obtain a description of itself and use it for computing. Formally let $T$ be a TM that computes a function $t:\Sigma^*\times\Sigma^*\to\Sigma^*$. There is a TM $R$ that computes a function $r:\Sigma^*\to\Sigma^*$, where for every $w$: 
$$r(w)=t(\langle R\rangle,w)$$
This means that a recursive function can be found by creating a Turing machine that computes itself as an input. These machines are not Turing-recognizable.
