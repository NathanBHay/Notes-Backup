A datatype is a classification of a type of data, and all the operations, rules and implementations that are associated with it. Datatypes can be built up to create [[Abstract Datatypes]]. **Primitive** (Built-in) datatypes are ones which are defined within the language by default. Datatypes can also be **simple** or **complex** with complex datatypes having multiple fields.

# Word
A word is the natural unit used by a processor. This natural unit is a fixed sized datum that is handled by a computer's instruction set.

# Character
A character (char) is a single letter, number or symbol. It is commonly 1 byte within a 64 bit system. The limits of what is considered a character is dependent on the [[Text Representation]] being used.

# String
A string is a set of [[Datatypes#Character|Characters]] that are used to make up readable sentences and words. It is usually implemented as an array which sizes depends on the amount of characters used.

# Boolean
A Boolean value is a single [[Number Systems#Binary|Binary]] digit with a size of 1 bit. Represented as a single [[Computer Architecture#Transistors|transistor]] it is usually used for [[Propositional Logic|Boolean Logic]] operations or as a return value.

# Integer
An integer is a single whole number that can be **signed** or **unsigned**. It's size is dependent on the size of a [[Datatypes#Word|word]] on the processor. An integer can also be **short** if it is half the integer size, and **long** if it is double the integer size. These integers are stored as either **Big Endian** where the greatest integer is stored first in the memory, or **Small Endian** where the smallest integer is stored first. Some architectures support Bi-Endianness which allows for the switching of endian.

[[Floating Point Numbers]]

# Pointer
A pointer is a hexadecimal number that stores a [[Memory|memory]] address. Most pointers point to a variable's memory address, which can be called by **dereferencing** the pointer. Pointers are commonly used for **indirect addressing** and allocation of blank sets of memory.

