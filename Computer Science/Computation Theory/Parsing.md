Parsing or syntax analysis is the process of analysing a string of symbols as to devise a parse tree which shows the relation of syntactic terms and operations. Parsing uses ideas from [[Formal Languages|formal languages]] and is a key part of [[Compilers|compiler design]]. The process of parsing traditionally starts with lexical analysis which tokenizes meaningful symbols defined by a grammar of [[Formal Languages#Regular Languages|regular expressions]]. After this the tokenized expression is used to generate a parse tree which depicts the relationship between tokens. This is usually done in reference to a context-free grammar. **Semantic parsing** is an optional step which validates the parsed expressions. Parsers can be further sub-classified into top-down and bottom up parsing.

# Parsing Paradigms
There are a variety of common parsing strategies that are used to parse the input of a variety of languages. The two main paradigms are:
- **Top-down parsing** is a strategy which builds the tree from the top and works down through using the rules of the formal grammar. This functions through identifying the leftmost derivation for a given input. 
- **Bottom-up parsing** builds the tree from the lowest level and moves upwards. This uses the rightmost derivation to analyse the given input.

To simulate complex rules parsers commonly follow two approaches. These are a look-ahead and multiple run throughs. **Look-Ahead** parsers are able to look ahead. The other common approach is to run multiple times through.

# LR Parsing
**LR Parsing** is the process of scanning input from left to right as to create a rightmost derivation. This follows a bottom-up approach. These are implemented with [[Automata Theory#Pushdown Automata|deterministic-pushdown automata]].

**Shift-reduce parsers** are a type of LR parser that has a *stack* that stores the terminals and non-terminals that have been processed, and a *buffer* that contains the rest of input strings. This parser follows a process of shifting input letters on to the stack, and when the suffix of the stack equals the body of a production rule reduces the string to a production rule.

# Parser Generators
A parser generator is a toolchain used to create a language which can be parsed. These usually supply their own set of algorithms for parsing while leaving the process of creating a grammar to the user. 
- **[[YACC|YACC]]** is the most popular parser generator. It uses [[C Language|C]] to write a grammar.
- **[[Tree-Sitter]]** is a modern parser generator tool. It uses [[JavaScript|JS]] to write a grammar that compiles to C.