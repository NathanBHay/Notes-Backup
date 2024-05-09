In the [[Theory of Computation]] a complexity class is defined as a set of computational problems with related complexity. This complexity is categorized by classes which relate to the [[Complexity Analysis|time complexity]] of the given algorithm. 

# Class P
A [[Turing Machine]] $M$ has a polynomial time complexity if its time complexity is $t_M(n)=O(n^k)$ for some fixed $k$. This means there is a constant such that for all significantly large $n$ that $t_M(n)\leq\cdot n^k$. This can be symbolically written as: 
$$\exists c\exists N\forall n:n>N\Longrightarrow t_M(n)\leq c\cdot n^k$$
A language is **polynomial time decidable** if it can be decided by a polynomial time Turing machine. The class of all languages decidable in polynomial time is called P. These problems are considered efficiently solvable. 

A property of Class P is that if there exists two different Turing Machines, as long as machine two can simulate machine one in polynomial time then both are within P.

## Polynomial-Time Reductions
A polynomial-time reduction is a [[Reducibility#Undecidable Reductions|undecidable]] that maps from one language $K$ to another $L$. Such that both problems are proved to be within P time. This relation can be written as $K\leq_P L$. Some properties of these reductions is that they are reflexive $L\leq_PL$ and is also transitive $K\leq_PL$, and $L\leq_PM$, then $K\leq_PM$

# Class NP
A polynomial-time decider for a language $L$ determines in polynomial time if a string $x$ belongs to the language. 

A **verifier** for a language $L$ is a Turing machine that takes as input two strings $x$ and $y$ such that it always halts. Where if $x$ is in $L$ there exists a $y$ such that the TM accepts and if $x$ isn't in $l$ every $y$ makes the machine reject. The string $y$ is called a **certificate**. A polynomial-time verifier is a verifier with time complexity polynomial in $n$ where $n=|x|$.

Non-deterministic Polynomial time or NP is the set of languages for which there is a polynomial time verifier. To show a language is in NP you need to specify a certificate, give a polynomial-time verifier, and prove it. This certificate is normally a function that converts the problem into one the verifier can be ran on.

Another way to prove a language is in NP is if there exists some polynomial-time Non-deterministic Turing machine decider for $L$.

# NP-Completeness
A language is $L$ is considered NP-complete if $L$ is in NP and every language in NP is polynomial-time reducible to $L$. Symbolically this is written as: 
$$\forall K\in\text{NP}:K\leq_PL$$
Not all languages are NP complete, this is due to the language not being NP or not having a valid reduction to all $K$ in the NP class. The process of proving NP-completeness usually follows 

## NP-Complete Reductions
The first NP-complete language is the language of satisfiable Boolean expressions in CNF. This is proved by the **Cook-Levin theorem**. Reducing to a NP-complete problem in general can be done by reducing to satisfiability. This is done through introducing Boolean variables to describe the parts of the certificate, and then translating the rules of the language into CNF.

# P-Space
Polynomial space complexity is found as all algorithms which are decidable in polynomial space. This can be viewed as: 
$$\text{PSPACE}=\bigcup_k\text{SPACE}(n^k)$$
The non-deterministic form of polynomial space **NP-Space** is considered equivalent to P-Space by [[Turing Machine#Space Complexity|Savitch's theorem]]. This means that $\text{P}\subseteq\text{NP}\subseteq\text{PSPACE}=\text{NPSPACE}\subseteq\text{EXPTIME}$. This relation happens as a machine that runs in P-time can't explore more than P-nodes in a Turing machine and thus is a subset.

# P-Space-complete
A language $B$ is considered P-Space-complete if it is in P-space and every $A$ in the space is polynomial time reducible to $B$. If a language only satisfies the second condition then it is **P-Space-bard**. Due to the relation shown in P-Space proving that the language is time reducible provides a methods of proving space reducibility.

# Class L & NL
Class L is the class of languages that are decidable in logarithmic space on a deterministic Turing machine. This means $\text{L}=\text{SPACE}(\log n)$. Class NL is similar but uses a non-deterministic Turing machine. Meaning $\text{NL}=\text{SPACE}(\log n)$. The idea behind these classes is based upon the use of a two tape TM where one tape is used for reading and the other for writing. In this case sublinear algorithms allow the TM to manipulate data without storing all of it in its storage. Sublinear algorithms are interesting due to their ability to provide bounds for a variety of common algorithms.

A **log-space transducer** is a TM that allows problems to be found as log space reducible to each other. This TM has a read tape, a write tape, and a working tape. The write tape's head can only move left. The working tape has a maximum of $O(\log n)$ symbols. The transducer computes the function $f:\Sigma^*\to\Sigma^*$, where $f(w)$ is the string remaining on the output tape after it halts. A language is log space reducible if $A\leq_L B$ by means of $f$. A language is **NL-Complete** if every $A$ in NL is log space reducible to $B$.

Interestingly $\text{NL}=\text{coNL}$ which means that all NL languages are equal to the complement of all NL languages.

# Exp-Space-complete
A language $B$ is EXPSPACE-complete if it is within EXPSPACE, and every $A$ in EXPSPACE is polynomial time reducible to $B$. 
