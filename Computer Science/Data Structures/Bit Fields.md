A bit field is a [[Data Structures|data structure]] which uses individual bits to store data rather than a type or an object. This allows certain structures to be stored in a compressed fashion without the overhead of traditional data-structures. Support for bit fields depends on the programming language. Systems languages such as [[C Language|C]] & [[C++]] allow for easy manipulation of bit fields. In languages which lack support for this the usual approach is to use values sized at word length and modify them with bit masks.

A **bit mask** is a way of manipulating individual bits within a bit field. This is done through creating a string of binary similar to the bit-field and then running a [[Propositional Logic|logical operation]] to change the bit field. This allows quick editing of specific bits.

A common paradigm within [[C Language|C]] is the use of flags which are bit fields. These flags are constructed by creating a binary digit of the necessary length where the place of the true digit depends on what flag is present. This allows for multiple flags to be set. A common approach to this involves defining these flags as enumerables. This allows or-operations to include multiple flags.

Bit packing grids is a way of creating a [[Pathfinding|pathfinding]] grid more efficient by packing it into a grid. This results in a grid implementation which stores obstacles as 0's on a grid

