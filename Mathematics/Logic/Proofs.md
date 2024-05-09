A mathematical proof is a inferential argument for a mathematical statement. This states that through logical assumptions a statement can be proved to be true. These are [[Propositional Logic||logically]] proved by **theorems** or **axioms** . There are many techniques to prove a statement but the most common are:
- Induction
- Contradiction

Proofs can be done on either mathematical [[Relations|relations]] as to prove the logic of a relation or on an algorithm. Proofs on relations usually attempt to break a key axiom of mathematics as to demonstrate a proof. Proofs on algorithms attempt to demonstrate the program always terminates, and with the correct result.
# General Advice
During the writing of proofs their are many common patterns to the structure and method can be found. For statements 

The usual structure to prove a subset relation $A\subseteq B$ follows:
1. Take a general member of a set (in general the smaller set) and give it a name $x\in A$
2. Uses the definition of $A$ to say something about $x$.
3. Follow through with this logic and show how $x\in B$ satisfies the problem.

Another common problem is the proof of set equality $A=B$. This is a simple process which attempts to prove both $A\subseteq B$ and $A\supseteq B$. For numerical equivalence simply use algebra to transform $a=b$. If not prove $a\leq b$ and $a \geq b$.

# Floyd-Hoare Logic
Floyd-Hoare logic attempts to prove correctness of algorithms through the use of loop invariants. To process uses the idea that the loop invariant should be true before the loop starts, during each iteration, and after the loop terminates. This process commonly uses other proofing techniques as to demonstrate that the value is true at all these stages.

# Proof by Construction
Proof by construction or proof by example attempts to use a specific case to prove a theorem. This process is commonly used to assert existence of an object with a specific property. As a result to prove by construction you demonstrate the object has the property through an example. Construction can only be used in specific cases and thus, is difficult to apply to many problems.

# Proof by Exhaustion
Proof by exhaustion attempts to prove all cases of a given theorem. This follows a process of identifying all cases (cases may overlap), and then using another proving technique to prove each case. This method works best for situations where the amount of cases are finite. 

# Proof by Contradiction
Contradiction assumes the negation of a statement that is being proved. Thus, to prove the statement you follow the logic of the negation until a contradiction appears which breaks the [[Hypothesis Testing|null hypothesis]]. 

# Proof by Induction
An inductive proof is a statement that says given a *base case* the statement can be proved if all natural numbers hold true. This is done through the steps:
1. **Base Case** which states that $P(0)$ is true.
2. **Inductive Step** which states that as $P(k)$ is true, and $P(k+1)$ is true, then the statement is true for all $k \in \mathbb{N}$.
This **base case** can be initialized to be any value and can also be multiple statements.

**Strong Inductive Step** is done by showing everything up to $P(k+1)$ is true. This creates a stronger proof.

**Proof by Descent** is similar to induction however proves a *descending sequence* and how the **base case** stops this.

