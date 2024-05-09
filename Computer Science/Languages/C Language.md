The C programming language is a general-purpose computer programming language created in the 1970s. It has become the basis of many other languages whether in syntax or as a language to be compiled to.

The C language functions through a process where:
1. **Preprocessor** gets libraries.
2. **Compiler** compiles the file.
3. **Linker** combines the file and libraries.
4. **Loader** which gets relative memory and writes it to an absolute address.

C uses the standard primitive [[Datatypes|datatypes]] and has [[Memory|memory management]] features such as *pointers*, and memory allocation.

# C Syntax
[[Memory|Memory Allocation]] in C is done through the commands *malloc(size)* and *calloc(size)*. This initializes a set of data and returns a pointer to the address, with *calloc* initializing all data to 0's.

# Macro Directives
The `#define` compiler directive allows the declaration of macros. These values are decided upon compile-time and as such need to be constant. 
```C
#define CNAME value
#define CNAME (expression)
```
