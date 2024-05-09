Yet-another-compiler-compiler is a [[Parsing|parser generator tool]] which creates a LALR parser. YACC can be used to build [[Compilers|compilers]], [[Formal Languages#Context-Free Languages|context-free languages]], and similar technologies. YACC is commonly used with Lex as to avoid the process of parsing the characters. YACC uses a `.y` file type. YACC code is split up into three sections divided with `%%`. These section are definitions, rules and functions.

# Definitions
**Definitions** which include function headers and includes, as well as declaring tokens, and types. Tokens can be declared with `%token <type> TOKEN`. Some additional operations include:
- Left and Right associativity can be declared with `%left "token"`.
- Grammar start can be called with `%start rule`.
- Non-terminals can be declared with `%type <type> rule`.

# Rules
The rules section uses code with a structure similar to [[Formal Languages#Backus-Naur Form|Backus-Naur Form]] to parse the language. In addition to the ability to parse the language code can be executed using the resultant values. While any code can be executed within the associated block `$$=` specifies a return value with `$i` and other numbers specifying which non-terminal and the appropriate combination function. 
```
rule : rule rule  {$$ = $1 + $2}
		| rule2 {}
```
