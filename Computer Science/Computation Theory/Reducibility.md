A reduction is a way of reducing one problem to another problem such that the solution to the second problem can be used as the solution to the first problem. There are a variety of techniques 

# Undecidable Reductions
Reductions to undecidable problems such as the [[Decidability#Halting Problem|halting problem]] or $A_{TM}$ are a common approach to proving the undecidability of languages. This is usually done through constructing a [[Proofs#Proof by Contradiction|proof by contradiction]] which states the problem has a decider. After the construction of a new TM that runs on the problem you attempt to find a case where a decider is ran on an example of a undecidable problem, thus mapping the problem to another. Therefore, proving undecidability. 

This means that given two languages $A$ and $B$ where $A$ is undecidable then if $A\leq_MB$ then $B$ is also undecidable. Inversely if $A$ is decidable then $B$ is as well.

# Mapping Reductions
Mapping reductions are the process of mapping one decision problem to another using a computable function $f(w)$. Suppose two languages $K$ and $L$ over the alphabet $\Sigma^*$. A mapping reduction from language $K$ to $L$ is a computable function $F:\;\Sigma^*\to\Sigma^*$ such that for every $x\in\Sigma^*$, $x\in K$ if and only if $f(x)\in L$. The notation for this is given as $K\leq_mL$ which means that there exists a mapping reduction from $K$ to $L$.

Informally to find a mapping reduction from one language to another find a function $f(x)$ such that the output maps the first language to elements within the second. For example in a language of odd numbers and a language of positive numbers you can map with the function $f(x)=x\%2$ as to turn all odd numbers into $1$ which is positive and thus true, and $0$ which isn't positive and results in false.
