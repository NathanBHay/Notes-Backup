A number system is a set of numbers used to represent an increasing sequence. A number being a object used to quantify an amount. These number systems consist of digits that after being combined in an ordered list form a number. Thus each number can be broken up as:
$$ (n+k)\dots(n+1)n = (n+k) \times base + \dots + (n+1) \times base + n \times base$$
The base of a numbering system determines the amount of characters within the system. There are many different number systems which are commonly used however the most popular include:
- **Decimal** (Base-10) the standard counting system.
- **[[Number Systems#Binary|Binary]]** (Base-2) used within computers.
- **Hexadecimal** (Base-16) used to shorten most representations.
- **Octal** (Base-8) used to shorten other representations.

Number systems commonly used a subscripted number to denote the base it is in.

# Binary
Binary is a Base-2 numbering system that uses 0 and 1 to represent all numbers. This allows for representations of *False* and *True* within mathematics or *Off* and *On* for transistors. This makes binary pivotal within current computers. It is also commonly associated with the [[Datatypes#Boolean|Boolean]] datatype.

To represent negative numbers in binary there are three possible representations that build upon each other:
- **Signed Representation** uses 0 to represent positive and 1 to represent negative. However, this causes the issue of a positive and negative 0 while also being unable to add negative numbers.
- **1's Compliment** reverses all bits within a negative number to enable addition of positive and negative numbers.
- **2's Compliment** adds 1 to the number as to create easier overflow detection as two numbers of the same magnitudes should never produce a result of an opposing one. While also removing negative 0.

**Hex** to binary has 1 Hex digit to 4 binary. While **Octal** has 1 Octal digit to 3 binary. While Binary requires a normal conversion method.
