Haskell is a [[Functional Programming|functional programming language]] which attempts to distance itself from traditional programming language with a focus on functional declarations.

Due to Haskell's functional paradigms all variables are considered immutable, and functions are generic. Haskell does have an **IO** system however, attempts to restrict it to a certain case within the code. This allows most functions to be effectful until operations such as printing need to be done.

# REPL
The Read Eval Print Loop works by creating a stack on the GHCI for the file. From this Haskell requests you what libraries should be loaded into the current scope. This **prelude** is the default library which includes most basic operators. The REPL can have variables and basic operations locally declared within it. It also has a set of non-Haskell commands such as:
- **:l** which loads a Haskell file.
- **:r** which reloads a Haskell file after an edit.
- **:h** which asks for help.
- **:q** quits environment.
- **:i** shows information about defined methods available.
- **:t** gets type of the function

# Basic Syntax
Haskell shares traditional logic operators such as equal to == , and &&, and or ||. The exception is **not** which uses **/=**. Haskell uses an if-then-else expression similar to a ternary in [[JavaScript]], and very similar to [[Python]]'s ternary. It can be written as:
```
if <cond> then <true operation> else <false operation>
```
The **print** function can be used to show basic printed values, converting inputs into a string.

The **dollar sign** $ can be used to signify brackets around an expression to the right of it. This allows more visually apparent chaining of functions. This can be considered to delay function application. **Dot** **.** feels similar to dollar sign except functions as a [[Functions#Composition|composition]] of two functions.

**Indentation** is used within Haskell to declare scope. For example within a function scope is commonly used in conjunction with the where keyword. **Where** is a keyword which creates multiple function definitions which are visible within the scope of the parent function. Similar to the **where** keyword you can also use **let** and **in** which creates a variable declaration, in a function body.

**Do** is a keyword used to sequence actions. While do isn't strictly needed it provides a more readable code structure. Code written in a do block can be considered effectful.

Since all basic operations within Haskell are functions, an infix operation form can be used. This takes the form `(+) x y` which evaluates to `x+y`. Infix can be done through parenthesis and can also be closured. For example `(+x) y` is the same as the previous two expressions. Order can also be used for operations such as divisions where `(/x) y` and `(x/) y` evaluate differently.

**Guards** within Haskell are a way to specify multiple conditions over the span of multiple lines. This creates unique cases for multiple scenarios. It can be written as:
```
<Function>
	| <cond1> = <return1
	| <cond2> = <return2>
```

# Haskell Programming Levels
There are seven programming levels found within Haskell. These levels are where the name spaces are located. These levels are:
- **Functional** which is where all functions are located.
- **Term-Level** which is where all functional body expressions are located.
- **Data Constructors** which is where all functions declare their data types,
- **Type Variables** where all variables have static analysis and verification ran.
- **Type Constructor** where types are constructed.
- **Type Classes** where types are made up of other types.
- **Modules** where multiple files share the previous six levels.

# Pattern Matching
Pattern matching is the process of using the **type declarations** as a way to return a value given the type. This is similar to a case statement.

# Lambda Functions
Lambda functions in Haskell are inspired by [[Lambda Calculus]] declarations. They can be written as:
```haskell
\x -> x
```
This is equivalent to $\lambda x.x$, or `x => x` in [[JavaScript]]. Lambda functions prove very useful when used in conjunction with folds or maps.

# Lazy Evaluation
Haskell uses a [[Functional Programming#Lazy Evaluation|lazy]] approach by default when evaluating expressions. This means it defers evaluation until it must produce a value. This allows certain operations to be more efficient, especially infinite sequences, and opens up possibilities for many compiler optimisations. It can be hard on run-time performance and may lead to hig
her [[Algorithms#Computational Complexity|complexity]] if strict and lazy evaluation is mixed up.

# Typing
Haskell operates on the basic set of [[Datatypes|types]] found within programming. These types are declared in a **data declaration** where a **type constructor** reads the name of the type signature as to set the types. Types can be combined with a **sum type** or logical disjunction as to merge types. The pipe operator **|** can be used to specify a data type that can be of value or type. All types fall under a **type class** which is the set of operations defined with a respect to polymorphic types.

The operator **=>** serves to denote a type class constraint. This means that the type signature needs to be limited by the condition on the left side. Another symbol found within Haskell is the type constructor **->**. This states the arguments and its resultant type. To format is used during the creation of functions in the form:
```
<func name> :: <constraint> => <type> -> <type after function>
```

**Custom types** can be declared with the keyword `data`. A **type alias** is just another way to refer to a type constructor or constraint. It can be done with the syntax `type <NewName> = <OldName>`. This is used for brevity.

Haskell has variable conventions that should be remembered. Type variables should be alphabetical characters that go alphabetically. Functions can be used as arguments with the type variable $f$. These functions might have a number added to the end. The $f'$ prime syntax is used to denote a helper function to $f$.

Haskell uses polymorphism to give type variables the ability to implement expressions that can accept arguments and return results of different types. Polymorphic type signatures can be split into three types: concrete, constrained polymorphic, or parametric polymorphic. Most polymorphism in Haskell is constrained or ad-hoc polymorphism.

**Instance** is used to tell the compiler how to check for the type classes given a custom datatype. This allows custom data types to be enumerated, checked for equality, and more.

**Deriving** is used to automatically write your own mechanism to derive a value. This is as opposed to instance which offers a custom mechanism. For example deriving equality can lead to a method of comparing all the values from an ordinal perspective.

**Class** is a keyword to declare a protocols for using an object rather than defining an object itself. Its similar to a java script interface.

**New Type** is similar to the **data** constructor. Except it provides a more anonymous definition where it isn't declared at a type constructor level. This means no additional overhead is required. In general the reason you use a new type is as a wrapper for a single value. This means it can be used as the format for bigger values, such as sum or product types. It also allows the creation of different type class instances such as product or sum.

**Product Type** is a form of type that is similar to structures in C like languages. It means a type has both traits of a type. **Records** are a product type that has the names of each type explicitly defined. This is as opposed to having a set of data like `<name> <type> ... <type>`. A record follows the structure:
```
data <name> = 
<name> {
<name1>::<type>
...
<nameN>::<type>
}
```

## Type Classes
Haskell has additional type classes that allow for greater generalisation. The basic ones include:
- **Num** which is defined as the superset of all the basic number types [[Datatypes#Integer|integer]], [[Datatypes#Float|float]], as well as **rational** which is a fractional value, and **scientific**.
- **Ord** is the type class of all things that can be ordered. This includes numeric, string, character, values.
- **Eq** is the type class for all values that can be compared and determined to be equal in value.
- **Enum** is the type class of values that can be enumerated.
- **Bounded**
- **Read** is the 
- **Show** is a type class that provides the creation of human readable string representations. Values within the show data type are the only ones that can be effectful within the program
- **List** is a type class that has multiple values.
- **Tuple** is a type class that has a set number of values.

# Nothing, Just, Maybe
Within Haskell a **Maybe** functions as a value which is unsure. It can either be a return value, or a **nothing**. **Nothing** is a datatype that signifies there is no input, or empty. The **Either** datatype functions as a way to note that a value is included in either type. As a part of either the **left** and **right** are the values found within the either.

**Higher-Kinded Types** are any type which is considered a type constructor rather than a type constant. Some examples of these are:
- **Maybe** which is defined as `* -> *`
- **[]** which is defined as `* -> *`
- **Either** which is defined as `* -> *`
- **(->)** which is defined as `* -> * -> *`

These don't need a real type to be included.

# Lists
All Haskell's lists are Cons Lists. These linked list like format have their own syntax. They can be defined with `[<item>,<item>]`. The use of the `<lower>..<upper>` can be used to creates lists of a certain range. The `++` can be used to concatenate lists together. An item can be added to the start of a cons list through the `:` syntax. This can be chained. These tools make up the main operations however you can also:
- **Head** which gets the first item.
- **Tail** which gets everything that isn't the first item.
- **Take** returns the specified number of elements from the list starting from the list.
- **Drop** returns the remainder of the list after a specified number of elements has been pushed.
- **!!** returns a value indexed at that position.
- **Map** which maps a function over a list.
- **Fold** which reduces a function, by using an accumulator variable.
- **SplitAt** splits the list in two from a point.
- **Take While** checks a condition and takes while the condition is false.

**Tuples** are list like collections that don't need the same type.

List comprehension is a process of creating a list based on conditions. List comprehension is done through the syntax `[<Output> | <var> <- <Input List>, <Optional Cond>]`. Multiple input lists can be used as to generate lists based on multiple variables.

# Foldable
Foldable is a type class that allows data structures to be folded into a summary value. These folds are done along the lines of a monoidal operation. The fold operation is therefore considered a type of monoid that can be used in conjunction with monoid operations as to allow for the creation of a value based upon a context, such as a list.

# Monoid
A monoid is a binary associative operation with an identity. Simply a monoid is a function that takes two inputs, that can be in any order, and their exists cases where only on value is returned. In general a monoidal operation usually is an operation that combines two values. For example the monoid of two lists is a concatenate operation. Integers prove a special case as the monoidal operation needs to be specified by a sum or product context.

Monoids contain three main key words. These are:
- **Mempty** which is what can be passed when an argument is blank in a monoid.
- **Mappend** or **<>** which is used as the main operation between two types.
- **Mconcat** which functions as a fold onto multiple types in a list.
- **Getters** which function to get a value out of its monoid context. This is used in cases such as **get sum** to get the result of a monoid done on sums.

Monoids prove useful as monoidal patterns appear all throughout programming. The main reason this is useful is due to the identity pattern. Which allows values to ignore the monoid operation with the Mempty keyword.

**Semi-groups** are another type class similar to monoids but without the identity operation. Semi-groups use the term **Non Empty** instead of **Mempty**. While they are found within base they aren't in prelude, meaning they need to be imported. If you want to remove the associativity of the semi-group as to just get a binary operation you can create a type class called a **magma**. This proves to be overall pretty useless.

# Functors
A functor provides a method that allows the application of a function without altering the structure of that value. A functor generalises this idea as to allow values to be manipulated while keeping the type class of the value. The main operation for a functor is the **fmap** or **<$>**. While done on lists these are identical to a normal map, when done on values such as a just, or maybe there functionality is seen. For example if you want to add a value to a just, a fmap can be used in the form `fmap (+1) just 1`. When using functors the phrase lifting is used as to mean the lifting of the functor into a new context.

Functors follow two important laws, those are the law of identity, and composition. This means `fmap id == id` and `fmap (f.g) == (fmap f) . (fmap g)`.

# Applicative
An applicative is a monoidal functor, which lifts the context of both values into the same context as to combine. This is done through the the symbol **<\*>** pronounced **apply** which is an infix operator. Simply an applicative maps a function in some structure over a value in some function.

Applicatives follow three laws, those being the law of identity, composition, interchange and homomorphism. Homomorphism is the idea that `pure f <*> pure x == pure (f x)`, which means that an applicative needs to be equal to a composition of the same function in their contexts. Interchange is defined as `u <*> pure y = pure ($y) <*> u`.

# Monad
A monad is an applicative functor that allows for the sequencing of actions as to feed one value into the next function. Therefore, monads are used when monadic values depend on each other to produce a result. Monads therefore produce structure through applying functions. Commonly monads are misunderstood, people see them as impure imperative code. Monads have three main operations:
- **Bind** **>>=** is used to do an action on the left that is passed as the argument of the right action.
- **Sequencing operator** **>>** or **\*>**, which puts operations within a sequence, doing the left operation, and discarding it to allow for the next operation to be done given the previous codes effects.
- **Return** which is the same as the applicative **pure**, as they both put a value into a context. Similarly **lift** operations also exist that can be ignored due to the presence in applicatives.
- **Do** provides syntactic sugar for a sequence operator. It is used to express that every line in the do block ends with a **sequencing operator**. One aspect of do code is the ability to assign variables with the **<-** operator. This creates a variable that can be used, this functions similar to bind.

The maybe monad is a type of monad which enables previous calculations to return nothing. As to provide a final result based upon previous nothings, while the maybe applicative sees these values independent of each other.

Monads follow 2 laws, those being identity, and associativity. Identity is declared as `m >>= return = m`, and `return x >>= f = fx`. Associativity is declared as `(m >>= f) >>= g = m >>= (\x->f x >>= g)`

# Traversable
A traversable allows the transformation of elements inside a structure like a functor, producing multiple applicative effects. Simply a traversable moves left from right, evaluating actions and collecting the result.

Traversable follow the law of identity, composition, and naturality. Composition defined as `traverse (Compose . fmap g . f) = Compose . fmap (traverse g) . traverse f`, this used to demonstrate that traversable data can be composed to combine syntax. Naturality is defined as `t.traverse f = traverse (t.f)`, which tells us that function composition allows a traverse to move over the structure generated by composition.

# Reader
A reader is a way of composing two functions before a value has been given, therefore creating a functor of functions.

# Parser Combinators
The core idea of parsing is to accept serialized input and turn it into a structured datatype. Similarly a parser combinator is a higher order function that takes parsers as input, and returns a new parser as output. A parser works by moving through a parser input through a sequencing operator. The parser moves the 'cursor' by taking the input and reading what has been sequenced in the function. This results in an output tuple with whatever is left of the cursor, and right. The left side structured in the desired way.
