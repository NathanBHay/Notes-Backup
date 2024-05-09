A compiler is a tool used to convert a programming language into executable operations or another programming language. This process can be broken into two key processes, these are analysis and synthesis, also commonly called **frontend**, and **backend**. The analysis process takes the code, and converts it into processable data. The synthesis portion creates a program from the previous data. The analysis stage can be broken into:
- **Lexical Analysis** which is the first step where characters are grouped into *lexemes* which are a token name and an attribute value. This is occasionally called scanning.
- **[[Parsing|Syntax Analysis/Parsing]]** is the second phase where the tokens are converted into a tree-like representation. This syntax tree contains nodes which contain the token and the next tree node.
- **Semantic Analysis** uses the syntax tree to ensure that the code is written correctly while also setting the types for the data.
- **Intermediate Code Generation** is an optional step where a representation of the code is generated within a compiler unique language. This allows possible execution onto multiple machines.
- **Code Optimisation** is the process of changing the operations done on the syntax tree to be more efficient. During this process it is important to ensure that the program's meaning is preserved.
- **Code Generation** is the final process where the code is turned into its target language. This usually means a final conversion into assembly.

Through these stages a compiler is able to generate a code in another language. Beyond the process listed above there are other methods of compiling that manipulate the steps in different ways. These alternative compiler methods include:
- **Single-pass** compilers that combine the parsing, analysis, and code generation stage into one as to avoid allocating syntax trees or other intermediate representation. Languages that use this include [[C Language|C]], and pascal.
- **Two-Pass/Multi-Pass** compilers add a backend to the first pass compiler that optimises the code generation.
- **Tree-walk** interpreters that begin execution of the code after parsing it into an abstract syntax tree.
- **Transpilers** generate an intermediate representation in the form of another programming language.
- **Just-in-Time** compilation is a process of executing the code at run-time.

A large part of the binding of values is the idea of names, identifiers, and variables. An **identifier** is a string of characters that is use to identify an entity, such as a data object, procedure, class, or type. All identifiers are names. **Names** denote either identifiers or expressions. An expression can be made up of multiple identifiers. Names can be composite which means they refer to the two identifiers, these are called qualified names. A variable is a particular location of the store. It is common for identifiers to be used multiple times

A **definitions** is used to inform about values, while a **declaration** describes the types of things.
# Lexical Analysis
Lexical Analysis or Lexing is the process of grouping a sequence of characters into a sequence of lexical tokens, similar to a [[Formal Languages|formal grammar]]. Each of these lexical tokens are called **lexeme**. 
