Functional Programming is a [[Programming Paradigms|programming paradigm]] which rather than traditional imperative, [[Object Orientated Programming|object orientated programming]], focuses on the creation of a series of functions that take and return each other as parameters. It views the creation of programs as a combinations of expressions, that once combined can be reduced or evaluated. Functions are considered to able to be taken as input, or outputs to create more complex functions. It is technically a subtype of [[Programming Paradigms#Declarative|declarative]] programming which focuses on a more precise mathematical definition of [[Functions|functions]] and stresses the importance of composition and [[Recursion|recursion]]. Functional programming has the advantage of minimising loops which are error prone due as loops need correctness during instantiation, iteration and termination.

# Purity
The main concept of functional programming is **Purity** which is the idea of a function that has no side effects to the overall execution of a program. Thus, a **pure** function is one such that only the code within the scope is affected by the operations within the function. This means that the function could just as easily be a constant that provides the result of the equation, and therefore it has **referential transparency**.

# Types
One of the main differences in most functional languages is the idea of types rather than objects. Where objects or classes group together a form of data and its associated behaviors', types in functional languages simply represent the set of all data that exists for the structure. This splitting of

# Lazy Vs Strict Evaluation
Most programming languages can be categorised through either strict or lazy evaluation. In strict languages the arguments are evaluated before the body of a function. This is as opposed to lazy evaluation where the arguments are evaluated when they are needed. This is further expanded for arrays and other data structures. Furthermore, once a given argument is evaluated it is also commonly cached. Languages with strict evaluation can have lazy evaluation implemented through a primitive that delays and forces evaluation. Some languages use $-notation to represent a delay function that allows for values to be lazily evaluated.

Computational complexity is modified by lazy evaluation as languages where only lazy evaluation is preset result in the worst case being equal to the amortized complexity.

## Stream
A stream is a lazily evaluated list where every node is delayed such that it is only used upon evaluation. This enables the list items to be only evaluated when required whereupon the rest of the nodes are suspended. This is occasionally called *incremental* evaluation. Streams are found within functional languages such as [[Haskell]] and object orientated languages such as [[Java]].

# Tail Recursion Optimisation
Recursion is an important paradigm within the functional programming style, as it has a more **pure** definition. Tail recursion is the result of when there are no more calculations after the recursive value is called. This is commonly optimized to delete the old stack frame before opening another. This avoids generating extra stack frames at the cost of making debugging harder as stack redouts aren't available.
# Anonymous Functions
Within programming a **named function** is a set of code that can called upon to deliver a result given an input. These functions are usually put within different files as to point out their role as a function which will be called upon multiple times. An **anonymous function** differs from this as it is only located **inline** within the file it has been called. Therefore, it enables flexibility as it is only associated with the values that it calculates. These anonymous functions are usually done with different syntax to named functions with [[JavaScript]] using arrow functions, while [[Python]] uses lambda functions.

# Pure Array Methods
Arrays have a subset of pure anonymous functions which are commonly used on them. These pure array methods are:
- **Slice** which copies a segment of the array based upon the indexes provided.
- **Concatenate** which combines two list segments to form a list combined at the ends of each other.
- **Map** which does an anonymous function on all values of the array.
- **Filter** which removes values which don't confine to the provided function.
- **Reduce** which accumulates all the variables under a given function.
- **For Each** which does an operation given all the variables in the array.

# Curried Functions
A curried function is one which takes a certain parameter and returns another function. This can be done by chaining function declarations inside each other. This allows a variable to be kept for later use.

# Closure
A closure is a function which has been nested as to capture a variable inside a function, that can be used for later use. For example a function which adds to variables can be declared with one of the parameters fulfilled. This leads to a new function being created which adds by the given argument.

# Combinators
A combinator is a higher-order function that which performs a pure operations on their arguments as to perform a result. These functions have no free variables and only exist to combine given parameters. Some common combinators are:
- **Compose** which applies one functions to the results of another function. This is similar to mathematical [[Functions#Composition|composition]]. This can be written as `f => g => x => f(g(x))`
- **Identity** which returns a same value as it was given. This combinator is useful in testing, reading data structures with a map, or composition. This can be written as `x => x`.
- **K-Combinator** ignores the second parameter and returns the first. This can be written as `x => y => x` .
 - **Alternation** (Or-Combinator) attempts to apply the first function on a variable, and if that fails applies another. This can be written as `f => g => x => f(x) || g(x)`.
 - **Fork Join** joins to functions together and returns both.

# Binary Vs Unary
A function can be considered unary if it has only one parameter. While a binary function has two parameters. Most curried functions are usually unary functions. In general this argument shows the value of curried functions as they prove to be more principled in support for future applications.
