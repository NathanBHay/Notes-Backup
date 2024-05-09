A proposition in maths is a statement that is either *True* or *False*. This type of logic is commonly used within [[Computer Architecture#Logic Gates|Logic Gates]] within computer architecture. These statements use [[Datatypes#Boolean|Boolean]] variables and **Connectives** to formulate reasoning. The basic connectives are:

| Operation   | Word | Math Symbol | CS Symbol             | Note          |
| ----------- | ---- | ----------- | --------------------- | ------------- |
| Conjunction | and  | $\land$     | && / +                | Both True     |
| Disjunction | or   | $\lor$      | \|\| / $\times$       | One True      |
| Negation    | not  | $\lnot$     | ! / $\overline {var}$ | True if False |

# Further Connectives
Some further connectives found within Computer Science which are considered **universal gates** as they can build all other gates are:
- **NAND** which is Not And.
- **NOR** which is Not Or.
- **XOR** which is exclusive-or and represented with $\veebar$ or ^.

Some further connectives found within Mathematics are:
- **Implies** or **conditional** written with the symbol $\to$ or $\Rightarrow$ and is always true except if the left side is true, and the right is false.
- **If and Only If** (IFF) or **equivalence** written with the symbol $\leftrightarrow$ or $\Leftrightarrow$ and is true if both are True or False.

# Tautologies & Contradictions
A **Tautology** is a propositional statement which is true under all circumstances. While a **Contradiction** is false under all circumstances

# Logical Equivalence
Logically Equivalent statements happen when two statements provide the same result. This equivalency can be used to simplify logical equations. Some common equivalence laws include:

| Law                      | Equivalence                                                                                                           |
| ------------------------ | --------------------------------------------------------------------------------------------------------------------- |
| Equivalence              | $p \leftrightarrow q \equiv (p \to q) \land (q \to p)$                                                                |
| Implication              | $p \to q \equiv \lnot p \lor q$                                                                                       |
| Double Negation          | $p \equiv \lnot \lnot p$                                                                                              |
| Idempotent               | $p \equiv p \land p \equiv p \lor p$                                                                                  |
| Commutative              | $p \lor q \equiv q \lor p$ <br> $p \land q \equiv q \land p$                                                          |
| Associative              | $p \land (q \land r) \equiv q \land (p \land r)$ <br> $p \lor (q \lor r) \equiv q \lor (p \lor r)$                    |
| Distributive             | $p \land (q \lor r) \equiv (p \land q) \lor (p \land r)$ <br> $p \lor (q \land r) \equiv (p \lor q) \land (p \lor r)$ |
| De Morgan                | $\lnot (p \land q) \equiv \lnot p \lor \lnot q$ <br> $\lnot (p \lor q) \equiv \lnot p \land \lnot q$                  |
| Identity                 | $p \equiv p \land T$ <br> $p \equiv p \lor F$                                                                         |
| Annihilation             | $T \equiv p \lor T$ <br> $F \equiv p \land F$                                                                         |
| Inverse                  | $F \equiv p \land \lnot p$ <br> $T \equiv p \lor \lnot p$                                                             |
| Absorption               | $p \equiv p \land (p \lor q)$ <br> $p \equiv p \lor (p \land q)$                                                      |
| Simplification Consensus | $p \lor (\lnot p \land q) \equiv p \lor q$                                                                            |

In general use *Commutative* to rearrange terms, *Associative* to remove brackets, and *Distributive* to expand.

# Normal Form
A normal form is a form of proposition where all logical connectives are using the same logical connective. There are two main forms used which are:
- **Disjunctive Normal Form**, uses disjunctives to build up propositions ie: $(A\land B)\lor(A\land C)$
- **Conjunctive Normal Form**, uses conjunctives to build up propositions ie: $(A\lor B)\land(A\lor C)$

# Min & Max Terms
An expression is considered a **min-term** if it is only the conjunction of two or more Boolean terms. The opposite of this is a **max-term** which is when only disjunctives are used.

# Truth Table
A truth table is a table of all possible inputs and the results from them. This can be written as a long continuous equation with each possibility represented by an equation of *Or*'s with each input. This equation however is long and requires simplification through logical equivalences or Karnaugh maps.

# Karnaugh Maps
A Karnaugh map is another method to simplify terms. It works by laying out all terms within a truth table in a term by term Karnaugh map. After this you need to find groups after which you find a smaller set of equation to provide a result.
![[Karnaugh Example.png|#invert|250]]
These groups have a set of rules:
- Groups must be of greatest size
- Group size must be a power of 2
- Must contain only 1's or 0's with all being contained in a group.
- Groups can overlap and wrap around.
From these we can remove redundancy through the general rule:
$$AB + A \overline B \equiv A(B + \overline B) \equiv A$$
This rule means that given the case where $A$ is true regardless of $B$, you can reduce the expression to only be $A$.

# Rules of Inference
A rule of inference is a logical form of a function which takes a **premise** and then returns a **conclusion**. They are commonly written in the form:
$$\frac{\text{Premise \#n}}{\text{Conclusion}}$$
Some common inferential rules include:
- **Contrapositive** which means the exactly the same in a different way. For example a double negation of a statement.
- **Logical Consequence** means that one is the same as the other but the other isn't the same.
