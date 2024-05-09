Within computer science the rules of a language are governed by a set of core **paradigms** which determine how the language is written. This includes a difference in how code is written, **syntax**, and how the code is interpreted, structed and managed, called the **semantics**. Many languages share similar semantics, based on the [[C Language|C]] language's design.

Most languages follow a basic imperative, procedural, object-orientated approach. However there are many different designs which aren't based on the traditional [[Computer Architecture|Von Neumann]], Turing machine paradigms.

# Imperative
Imperative programming is a paradigm which focuses on a set of central instructions that change a programs state. Thus, a program in imperative languages focuses on how each line changes the output of the program as it is built up.

# Procedural
Procedural programming is a form of imperative programming that has procedures or subroutines. These procedures have parametrized variables which are effected by the procedure, usually to effect the overall state of the program. They are used in places where repetitive code is required.

# Object-Orientated
[[Object Orientated Programming|Object-orientation]] is built around the concept of **objects** which bind state with behaviour through storing a structure of the state and functions to manipulate this state. Object orientation usually relies upon structure called **classes** which function as templates which create objects. These objects exist as entities which are able to interact with the program. Object orientation's main benefit is its ability to model data in a way that resembles entities in the world. Creating abstractions upon concepts which can then be combined together to make up larger entities.

# Declarative
[[Functional Programming|Declarative]] languages focus on the declaration of what a function should do, rather than how to do it. HTML and SQL are both examples of this as they perform an operation without explanation of how. This overall paradigm takes notes from more traditional mathematics to use precise definitions.

# Functional
Functional languages are built around the idea of applying and composing functions to create programs. It stresses the idea of purity where functions only modify their own state and therefore could be replaced with constants. This is furthered through the use of higher ordered functions that are able to be returned and taken as arguments therefore following the rules of Lambda calculus. Functional programming has the advantage of being less error prone due to the minimization of state which allows for a quicker debugging process.

# Constraint
[[Constraint Programming]] languages are built on the idea of using constraints to solve optimization problems. This paradigm traditionally uses a declarative syntax of notation to construct problems that can be solved usually with a constraint programming solver. They are usually very specific to optimization problems and thus have little adoption in traditional languages.

# Static or Dynamic Typing
Static typing requires the compiler to be aware of the types of all variables upon compilation of the program. While dynamic typing means that variables aren't associated with variables upon compilation. This doesn't mean errors won't happen if data is the wrong type.
