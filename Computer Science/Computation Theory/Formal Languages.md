Formal language theory is a branch of the [[Theory of Computation|theory of computation]] which formalises languages as consisting of words from an alphabet created with a specific set of rules. Formally an **alphabet** is a finite set of symbols denoted by $\Sigma$ containing **letters** or **characters** which are used to make up **words**. A **formal language** over an alphabet is a set of words over $\Sigma$. These languages can be empty $\emptyset$, only made up of an empty character $\varepsilon$, restricted to all words over $\Sigma$ of length $k$ or $\Sigma^k$, or a universal language $\Sigma^*$.  The rules for defining this language are called a **grammar**. 

A grammar is a set of structural constraints that dictate how strings can be created from a language's alphabet. A grammar consists of four main components, these are:
1. A set of **terminal** symbols, sometimes called tokens. These are the most basic form within the language.
2. A set of **non-terminals** which are also called syntactic variables. Each of these represents a set of strings of terminals.
3. A set of **productions** where each production consists of a non-terminal head, an arrow and a sequence of terminals and/or non-terminals called the body.
4. A non-terminal symbol to start the program.

# Chomsky Hierarchy
The Chomsky Hierarchy is a set of grammars with each higher type being a subset of the previous (a containment hierarchy). These four types can be defined as:
- **Type-0** grammars are **recursively enumerable** languages that can be ran on [[Turing Machine]].
- **Type-1** grammars are **context-sensitive** which can be ran on a bounded Turing machine.
- **Type-2** grammars are **context-free** and can be ran on pushdown automatons.
- **Type-3** grammars are **regular** which are ran on [[Automata Theory|finite state automaton]].

All Type-1, Type-2, and Type-3 languages are considered decidable as there exists a Turing machine which is able to compute all these languages in a finite time.

# Regular Languages
Regular languages are defined as a formal language which is defined by **regular expressions**. A word belongs to a regular language if it can be described also called **matched** by a regular expression. These expressions are defined with the following regular operations:
- **Groupings** are defined with parenthesis and denote a specific scope. This enables nested expressions that are able to group together characters. 
- **Alternation** or union describes an *or* operation. It is written as $A\cup B$, and formally is considered $A\cup B = \{x|x\in A \text{ or } x\in B\}$.
- **Concatenation** which adds together characters, and is defined as $A\circ B=\{xy|x\in A \text{ and } y\in B\}$.
- **Star** which means multiple is defined as the repetition of characters, defined as $A^*=\{x_1x_2\dots x_k|k\geq0\text{ and each }x_i\in A\}$. 

An expression $R$ is considered a regular expression if it is equal to $\varepsilon$, $\emptyset$, or $a\in\Sigma$. Additionally a regular expression can also be constructed from $R_1\cup R_2$, $R_1\circ R_2$, $R_1^*$, where $R_1$ and $R_2$ are regular expressions. 

## Closure Properties of Regular Languages
An operation is **closed** on a regular language if under that operation a new regular language can be generated. Closed operations include complement, union, intersection, and concatenation.

**Circuits** are a directed path which starts and ends at the same state. The length of a circuit is defined as the amount of different edges. 

## Regex
A regex processor translates regular expressions into an internal representation that allows for words to be matched from a string being searched within. Regex has a variety of different dialects which differ in syntax. In general the following representations are used, `|` for alternation, `a(b)` for grouping, `*` for star. Additionally letters from `a` to `b` can be represented as `[a-b]`, and `?` is used for optional values. The `+` operator is similar to the star however requires 1 or more occurrences.

## Parse Trees
Regular languages can be modelled with parse trees. These visualised the individual operations which make up the parsing process. The leaf nodes usually are represented with characters in the alphabet or an empty string character.

# Context-Free Languages
Context-free languages are a language which is generated by a context free grammar. Context free grammars follow a series of production rules which can be applied regardless of context. This means that rules of the form $\alpha A\beta\to\alpha\gamma\beta$ where a non-terminal $A$ is used in a context aren't allowed. These production rules functionally replace strings to define a series of tokens which can be parsed. Formally context-free grammars are defined as the 4-tuple of $G=(V,\Sigma,R,S)$ where:
- $V$ is a finite set of non-terminal characters or variables. This allow the division of syntactic categories which function as a sublanguage of the language defined by $G$.
- $\Sigma$ is a finite set of terminals disjoint from $V$ which make up the content of the sentence.
- $R$ is a finite [[Relations|relation]] in $V\times(V\cup\Sigma)^*$ where $^*$ is the Kleene star. The members of $R$ are called the rewrite rules.
- $S$ is the start variable used to represent a whole sentence. It must be within $V$.

A string in a context-free language is considered **ambiguous** if it has multiple left-most derivations. A language which only has ambiguous strings is called an **inherently ambiguous**  language.

## Chomsky Normal Form
A context-free grammar is in Chomsky normal form if all productions are in the form of live productions and dead productions:
$$\begin{align}\text{Nonterminal}&\to\text{Nonterminal}\;\text{Nonterminal}\\\text{Nonterminal}&\to\text{terminal}
\end{align}$$
Chomsky normal form is of particular use for use of algorithms such as the CYK algorithm and the pumping lemma. The construction of Chomsky normal form follows five main steps. These are:
1. Eliminate $\varepsilon$-productions of the form $X\to\varepsilon$.
2. Eliminate unit productions of the form $X\to Y$.
3. Give each terminal its own corresponding nonterminal.
4. Use nonterminal to eliminate terminals that don't appear alone.
5. Break down rules with more than two terminals into two terminal rules.

## Nullability Algorithm
The nullability algorithm is used to determine if a given empty-string $\varepsilon$ can be generated by a grammar. It doesn't use Chomsky normal form. The algorithm follows a process of marking all rules of form $X\to\varepsilon$ as nullable. From this it finds all rules of the form $Y\to Y_1Y_2\dots Y_n$ that is able to be produced by only non-terminals that have also been marked as nullable. If $S$ has been marked by the end then accept, else reject.

## CYK Algorithm
Cocke-Younger-Kasami algorithm takes as input a CFG $G$ and a non-empty string $s$ and decides whether the string is generated by the CFG. The algorithm has a complexity of $O(n^3\cdot|G|)$, where $|G|$ is the size of the grammar, and $n$ is the length of the parsed string. The algorithm works by finding all strings of size one within the string $s$ and testing if they have a given production. After this it finds all pairs of adjacent letters that are different in the string and finds if a valid production rule exists to create them. This process then finds all triplets, and the process continues until the whole string can be parsed. Expressed as pseudocode this follows:
```pseudo
	\begin{algorithm}
	\caption{CYK($G,s$)}
	\begin{algorithmic}
		\State $n\gets$ s.length
		\State $P[n,n,G.length] \gets$ \False for all elements
		\State $back[n,n,G.length] \gets \emptyset$\Comment{Backpointing triples}
		\For{$s\gets1$ \to $n$}
			\For{unit production $g_v \to a_s \in G$}
				\State $P[1,s,v]\gets$ \true
			\EndFor
		\EndFor
		\For{$l\gets2$ \to $n$}
			\For{$s\gets1$ \to $n-l+1$}
				\For{$p\gets1$ \to $l-1$}
					\For{production $g_a\to g_b \to g_c$}
						\If{$P[p,s,b]$ \and $P[l-p,s+p,c]$}
							\State $P[l,s,a]\gets$ \true
							\State $back[l,s,a] \gets (p,b,c)$
						\EndIf
					\EndFor
				\EndFor
			\EndFor
		\EndFor
		\If{$P[n,1,1]$}
			\Return $back$ /Comment{Table to construct possible parse trees of string}
		\Else \Return "Not a member of language"
		\EndIf		
	\end{algorithmic}
	\end{algorithm}
```

## Backus-Naur Form
Backus-Naur Form (BNF) is a form of context-free grammar that is used within computer science as to demonstrate the rules of [[Parsing|parsers]]. It represents productions as:
```
<head> := <body> | <body2>
```
The use of the pipe is used to signify an *or* operation.

## Regular CFGs
A regular language can be described by a context-free grammar. For a CFG to be considered regular it must follow the rule that all terminals and non-terminals must be ordered with a terminal first and one non-terminal second. This means productions of the form $X\to xY$ are the only way for linking together terminals and non-terminals. 

# LR(k)
A lookahead grammar is a context free grammar that requires a lookahead of $k$. This can be implemented with pushdown automata that has transition functions that require successive actions of an amount of $k$.

# Recursively Enumerable Languages
A language is recursively enumerable or type-0 if the language will halt given any accepted string. This means it allows for languages that have infinite loops, given the input string isn't within the language. The addition of infinite computations means that recursively enumerable languages are a superset of [[Turing Machine#Decidability|decidable]] languages.
