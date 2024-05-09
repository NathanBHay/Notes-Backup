A type system is a syntactic method of classifying data through the absence of certain behaviours. Type systems are usually classified through either static or dynamic systems. Where dynamic systems check types upon run time while static methods vary in their implementation. Some systems such as [[Haskell]] or ML exhibit a strong definition which follows lambda calculus while many [[C Language|C]] inspired languages use more loose compile-time checks. Type checkers have the main advantages of:
- **Detecting errors** is the most obvious benefit where early errors are detected before run-time. This greatly benefits writing and maintenance of code.
- **Abstraction** is helped by type systems that enforce structures such as classes or interfaces which themselves are a form of type.
- **Documentation** is benefited by the removal of the need to document parameters.
- **Language Safety** is achieved through the type system enforcing integrity of abstractions and data. Avoiding data leaks and other common issues.
- **Efficiency** computation of data is improved through use of types.

# Untyped Systems
Untyped systems are systems which lack a type system beyond their foundational logic.

## Untyped Arithmetic Expression
Untyped arithmetic expressions in general can be rigorously defined through [[Proofs#Induction|inductive]] logic and [[Propositional Logic#Rules of Inference|rules of inference]]. For a basic language with only a few operations the inductive logic can be defined as - the set of terms is the smallest set $\mathcal{T}$ such that:
1. $\{\text{True,False,}0\}\subseteq\mathcal{T}$
2. $\text{if }t_1\in\mathcal{T},\text{ then }\{\text{succ }t_1,\text{pred }t_1,\text{iszero }t_1\}\subseteq\mathcal{T}$
3. $\text{if }t_1\in\mathcal{T},t_2\in\mathcal{T},t_e\in\mathcal{T}\text{ then }\text{if }t_1\text{ then }t_2\text{else }t_3\in\mathcal{T}$

Alternatively another approach is through rules of inference, or **rule schemas** as meta variables are used. Theses set of terms can be defined as:$$\begin{aligned}
\text{false}\in\mathcal{T}&\quad\text{true}\in\mathcal{T}\quad0\in\mathcal{T}\\
\frac{t_1\in\mathcal{T}}{\text{succ }t_1\in\mathcal{T}}&\quad
\frac{t_1\in\mathcal{T}}{\text{pred }t_1\in\mathcal{T}}\quad
\frac{t_1\in\mathcal{T}}{\text{iszero }t_1\in\mathcal{T}}\quad\\
&\frac{t_1\in\mathcal{T}\quad t_2\in\mathcal{T}\quad t_3\in\mathcal{T}}{\text{if }t_1\text{ then }t_2\text{ else }t_3\in\mathcal{T}}
	\end{aligned}$$Formally the schema above represents a series of **axioms** for the first three schemas which lack a conclusion and **proper rules** for the ones that do. From this an infinite series of **concrete rules** can be generated. Explicit characterization of the terms follows a process similar to pattern matching where all all functions require a definition. For example $size(\text{true | false | 0})=1$ while the rest have a definition of $size(\dots)=1+size(t_1)$. 
