The C programming language is a general-purpose computer programming language created in the 1970s. It has become the basis of many other languages whether in syntax or as a language to be compiled to.

The C language functions through a process where:
1. **Preprocessor** gets libraries.
2. **Compiler** compiles the file.
3. **Linker** combines the file and libraries.
4. **Loader** which gets relative memory and writes it to an absolute address.

C uses the standard primitive [[Datatypes|datatypes]] and has [[Memory|memory management]] features such as *pointers*, and memory allocation.

# C Syntax
[[Memory|Memory Allocation]] in C is done t3hrough the commands *malloc(size)* and *calloc(size)*. This initializes a set of data and returns a pointer to the address, with *calloc* initializing all data to 0's.

# Pre-Processor
The C pre-processor functions to improve programming through the declaration and expansion of macros. The pre-processor is implemented within many C derivatives such as [[C++]] and other languages like Fortran.

*Object-like macros* are macros which are replaced by a fragment of code. These are declare with the `#define` directive. Macros can also have arguments in the case of *function-like macros* .
```C
#define CNAME value
#define CNAME (expression)
```
To *stringize* (tokenise) a macro arguments as a string the `#` operator can be used, allowing for the value to be used within string calls. Concatenation can be done with the `##` operator which allows for a token to be concatenated to a argument.

