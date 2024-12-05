GNU Compiler Collection (GCC) is GNU project's free and open source compiler. It has multiple frontends for [[C Language|C]], [[C++]], Fortran, etc and with targets for a variety of hardware.

# Parsing Pass
The first pass is the *parsing pass* which converts the text into an intermediate tree representation. These trees are constructed of generic trees and language specific tree types. During this phase function definitions and top level declarations are sent to the middle-end so they can be used in other files.

Originally the parser used was a [[Parsing#Parser Generators|LALR parser]] created in Bison, however most current frontends use a custom recursive descent parser.

## Tree
A tree is a data structure in GCC that represents internal code? These trees contain two fields, *tree chain* a pointer to other trees in a singly [[Data Structures#Linked List|linked list]] and a *tree type*. A tree can be walked through, a fact which is used during the passes.

An *identifier node* are used to encode characters. They contain a pointer to a string, its length, whether this operator is overloaded, and whether the identifier converts into another identifier.

The base implementation of trees are considered *GENERIC*. These expand the initial tree implementation to allow for functions. Any tree which is considered generic can easily be converted into later compiler stages with ones that are being language specific trees. These language specific trees require an additional conversion stage.

# Gimplification
**GIMPLE** is an intermediate representation which simplifies GENERIC by breaking it down into tuples of less than 3 operands. This differs from [[LLVM]] IR as it's less flexible.

Gimplification is the second pass and converts GENERIC to GIMPLE through recursion.

Language specific trees require their own implementation of a function to convert themselves into GIMPLE. Alternatively a conversion to GENERIC can be implemented to improve the simplicity of the conversion by using a language-independent glimpifier