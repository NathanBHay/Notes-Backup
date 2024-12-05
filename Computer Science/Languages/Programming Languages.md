A programming language is the tool which is used to write computer programs. A programming language functions as an abstraction upon the underlying machine code. These **higher level languages** provide an interface with complex operations and [[Data Structures|data structures]] that allow for programmers to create more advanced models. This is as opposed to lower-level languages such as [[Assembly|assembly]].

# Programming Language Aspects
## Static/Dynamic
During the construction of a language certain design choices can be described as static or dynamic. A **static** policy is an issue where the decision of how to handle something is made at *compile-time*, while a **dynamic** policy is handled at *run-time*.

## Environment & State
During language construction another important aspect is how changes to variables or data elements change the computers understanding of the variables. This results in either the values inside a variable to change or the name to change. To this extent the two approaches found are either the environment or state. The **environment** is a mapping from names to locations in the store. The **state** is a mapping from locations in the store to their values. In general both the state and environment are dynamic. Cases where the binding of names are static are for global variables. Locations are statically bound for constant expressions.

## Scope
Most languages use a **static scope**. A static scope implicitly determines what appears in a program or function's body. Languages with **block scope** use keywords such as *public*, *private*, and *protected* to declare what can be accessed by functions. In general all scopes can be view from a block level where each scope is seen as separate parts of the program.

## Parameter Passing
There are two types of function parameters **actual parameters** which are used to call the procedure, and **formal parameters** which are those called in the procedure definition. Languages have three methods of calling function parameters. These are:
- **Call-by-reference**, causes the address of the actual parameter to be passed to the callee of the corresponding formal parameter. This means the formal parameter uses a pointer to get the actual values. If the actual is an expression it is first evaluated. Reference is used in *ref* parameters in [[C++]].
- **Call-by-name**, is an old paradigm where the actual parameters are used as though they were formal parameters.
- **Call-by-value**, allows the actual parameter to be evaluated if it is an expression or copied if a variable. The value is placed in the corresponding formal parameters. It is common within [[C Language]] and [[Java]]. This process allows the actual parameters to be immutable while the formal ones aren't.

## Aliasing
Aliasing is a process that happens within languages that use call-by-reference as there is the possibility of two formal parameters that can refer to the same location. Values like this can be referred to as aliases of each other as they both refer to the same value. Beyond this any local variable that is equal to the formal parameter is also considered an alias.

## Classes Vs Prototypes
Within [[Object Orientated Programming]] there are two approaches to objects, these are classes and prototypes. **Classes** based languages are the more common method, and function on two core concepts: instances and classes. Instances store the state for each object and have a reference to the instance's class. When a method is called the instance calls the class to get the classes' method. **Prototype** based languages merge these concepts into only objects. Each individual object may contain state and methods,

# Domain Specific Language
A domain specific language (**DSL**) is a programming language which is made primarily to fulfil a certain need. These languages can be [[Turing Machine|Turing complete]] although many aren't. There main purpose is to allow for developers to interface with a program. This contrasts a **general purpose language** which are complete and allow for a broader application.