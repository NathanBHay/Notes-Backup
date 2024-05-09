Connascence is a software quality metric used to describe different types of coupling. It can be described through three different types strength of the coupling, degree of coupling, and locality of coupling. There is a variety of different connascence types which all describe specific types.

# Static Connascence
Static connascence is a type of connascence which happens during the compile time run. It usually involves mistakes made predominantly by the programmer despite input. Static connascence can be further subdivided into the following types:
- **Connascence of Name** happens every time a function is called by a program. This is as all calls to this function need to agree on a name leading to coupling. Connascence of name is common and as such is considered a weak form.
- **Connascence of Type** happens when components must agree on the type of an entity. This is a weak form of connascence however still illustrates coupling.
- **Connascence of Meaning** is when multiple components agree on the on the same value or object. Commonly also called [[Software Antipatterns#Magic Numbers|magic numbers]] this creates a strong coupling that can be improved by moving values to named constants.
- **Connascence of Position** is when multiple entities must agree on the position of values. This commonly happens when using arrays to keep collections of values that are accessed in a particular order. This can be fixed by using objects or types to represent the array. Position issues also happen in function arguments.
- **Connascence of Algorithm** happens as the result of two entities that must manipulate a set of values in the same way. If the algorithm is changed in one place it must be changed in another.

# Dynamic Connascence
Dynamic connascence is the result of coupling during the inputting of values, usually resulting in issues at runtime. This is divided into the types:
- **Connascence of Execution** happens when the order of execution of multiple components is important.
- **Connascence of Value** is when several values must be changed together. An example of this is through an initial state, who's value can be changed. To mitigate possible issues binding initial state to another value separates the values in a way that enables the starting state to be changed without effecting the initial state.
