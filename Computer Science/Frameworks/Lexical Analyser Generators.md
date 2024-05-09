A [[Compilers#Lexical Analysis|lexical analyser]] generator is a tool for generating lexical analysers. Lexical analysers being a tools that convert characters into tokens. These lexical analyzers can be used in concert with tools such as [[YACC]] as to create [[Compilers|compilers]], [[Formal Languages#Context-Free Languages|context-free languages]], and other similar programs. The approach most lexical analysers use is a [[Automata Theory|deterministic finite automata]] to parse the characters and assign values.

# Lex
Lex is an older lexical analyser generator that is written for C with files ending in the `.l` format. The structure of a lex files follows three sections divided by `%%`. These three sections are:
- **Definitions** which defines the macros and header file imports written in [[C Language|C]].
- **Rules** which associates [[Formal Languages#Regular Languages|regular expression]] patterns with C code. Executing the given code upon finding characters following the regex.
- **Code** where remaining C code can be placed.

An example Lex file follows a basic structure of:
```lex
/* Includes */
%%
rule {
		printf("Example Operation");
	 }
rule2 return TOKEN;
%%
/* Code */
```

# Flex
Fast lexical analyser generator is an alternative to Lex that uses a fast-table representation. Similar to Lex it is written for C language and sections out its code with `%%`. The advantage of flex is the ability to assign regular expressions variable names in the definitions section. This allows for reduced code.
