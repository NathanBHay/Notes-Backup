Decidability is the trait of a given problem to be solvable by algorithms. This demonstrates the limits of computation. Formally a given a language $L$ is decidable if there exists a [[Turing Machine]] $T$ which halts for all inputs. This Turing machine called a **decider** must find all inputs string as existing within the $\text{Accept}(T)=L$, and thus $\text{Reject}(T)=\overline{L}$. This means that the TM always decides within finite time whether or not any input string is in $L$ and thus, $\text{Loop}(T)=\emptyset$. All [[Formal Languages#Regular Languages|regular]] and [[Formal Languages#Context-Free Languages|context-free]] languages are considered decidable.

A language is decidable if and only if it is Turing-recognisable and co-Turing-recognisable.

# Proof for Undecidable Languages 
Before we can find an undecidable language we must first prove that not all languages are Turing recognisable. For a language to be Turing recognisable there must be a valid TM that recognises the given language. First observe that the set of all strings $\Sigma^*$ is countable for any alphabet $\Sigma$. This can be done by writing down all valid combinations from length $0$ to $n$. The set of all TM's is considered countable as every machine $M$ has an encoding into a string $\langle M\rangle$. Adversely the set of all languages isn't countable. To prove this first create an infinite binary sequence used to represent if a given word is accepted or rejected. This sequence of the form $L_i=\{0,1,1,\dots\}$ can be used to represent all languages over $\Sigma^*$. Through the use of the [[Set Theory#Cantor's Diagonal Argument|diagonalization argument]] one can see that by flipping the i-th index for all values from $1$ to $\infty$ you can create a new unique sequence. Thus, the set of all language is uncountable. Therefore, there exists languages which aren't recognisable by a Turing machine.

The next proof attempts to prove the undecidability of $A_{TM}$ which is the language defined by: 
$$A_{TM}=\{\langle M,w\rangle\;|\;M\text{ is a TM and M accepts }w\}$$
Suppose that $H$ is a decider for $A_{TM}$ that follows the algorithm: 
$$H(\langle M,w\rangle)=\begin{cases}accept&\text{if }M\text{ accepts }w\\reject&\text{if }M\text{ does not accept }w\end{cases}$$
Now construct a new TM $D$ with subroutine $H$. The algorithm for $D$ follows run $H$ on input $\langle M,\langle M \rangle\rangle$, and output the opposite of what $H$ outputs. By running $D$ on itself or $D(\langle D\rangle)$ we find that a contradiction appears as if $D$ does not accept $D$ it accepts but if it does then it rejects. Thus, $D$ or $H$ cannot exists.

The diagonalization method is also used within the proof. As if we construct a table of the Cartesian product all Turing machines $M_1,M_2,\dots,D,\dots$ against $\langle M_1\rangle,\langle M_2\rangle,\dots,\langle D\rangle,\dots$ where we run $H$ on all inputs $i,j$ we can see that given $D$ is constructed from the diagonal of all $M$ what happens when we run into the diagonal of $D$. This results in a contradiction. 

# Halting Problem
The halting problem is a an example of a undecidable problem that can be reduced down to the proof that $A_{TM}$ is undecidable. This problem focuses on the problem of determining if a TM halts on a given input. This can be described as the language: 
$$HALT_{TM}=\{\langle M,w\rangle\;|\;M\text{ is a TM and M halts on input }w\}$$
To reduces this, first assume that there exists a decider for $HALT$ which is $R$. This program tests if given a machine and input whether it will halt on a given input. Now construct an algorithm $S$ that first runs $R$ on $M,w$ and if it does halt, therefore accepting it means you can run $M$ on $w$ without fear of an infinite loop. Therefore, rejecting on infinite loops and rejects of $M(x)$, and accepting for accept states for $M(x)$. What this means is if $R$ decides $HALT$ then $S$ decides $A_{TM}$. As this was proven to be false previously we can assume the halting problem is undecidable.

## Proving Undecidability
The halting problem is a useful example of how to go about proving the undecidability of languages. This usually follows a process of reducing a problem down to the problem of whether there exists a decider for $A_{TM}$. This means these proofs attempt to decide for the language of machines $M$ that accepts $w$.

Another example of a undecidable problem is that from the language: 
$$E_{TM}=\{\langle M\rangle\;|\;M\text{ is a TM and }L(M)=\emptyset\}$$
The proof of undecidability for this first constructs a new machine $M_1$ where on input $x$ if $x\neq w$ then reject, and if $x=w$, run $M$ on input $w$ and accept if $M$ does. From this construct the TM $S$ which takes $M$ and $w$ as input, creates $M_1$ and then runs decider $R$ on $M_1$. From this, if $R$ was a decider for $E_{TM}$ then $S$ would be a decider for $A_{TM}$.

# Logical Theory Decidability
A logic system is considered decidable if their exists a decider for the language. First-order logic or [[Predicate Logic|predicate logic]] is an example of a logical language which is undecidable. Extensions upon this logic such as second order logic or type theory are also considered undecidable.