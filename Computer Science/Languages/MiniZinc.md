MiniZinc is a [[Constraint Programming|constraint programming]] language developed at Monash University. It follows a declarative [[Functional Programming|functional]] style of syntax that enables the definition of variables, constraints and common types. MiniZinc's main advantage is its compilation to FlatZinc, a [[Compilers|intermediate representation]] that allows for a variety of different constraint solvers to be used. MiniZinc also has a more complex type system that other constraint languages like [[Ampl]].

# Variables
There are two kind of variables within MiniZinc, **parameter variables**, and **decision variables**. Parameter variables are similar to standard variables and allocate a value for the variable to be assigned to. Opposingly decision variables are assigned a type and a choice of possible options called the **domain**. These values aren't assigned until run-time. Parameters can be with the `par` keyword or omitting it for simplicity. This follows:
```MiniZinc
<type> : <var-name>;
par <type> : <var-name>;
```
Decision variables are declared with `var` keywords. They are declared as:
```MiniZinc
var <type> : <var-name>;
```
Variable declaration is done through the `var` keyword. This allows the specification of a variable with a given type. Assignment is handled similar to most other languages.
```MiniZinc
var type: varName = ...;
```

# Conditionals
Conditionals are used similar to ternary, or conditionals in functional languages. They follow a syntax of:
```MiniZinc
if <cond> then <trueResult else <falseResult> endif;
```

# Constraints
**Constraints** are created with the constraint keyword. This allows the specification of a condition. [[Propositional Logic|Logical connectives]] follow a look similar to mathematics with the *and* keyword being called with `/\`, and `or` called with `\/`. In addition to these connectives there is also IFF called with `<->` and implies `->`. Not is kept standard and is called with `not`. 
# Solve
**Solve** indicates the type of problem and the arguments to solve it. These problem types can optionally take parameters. Some of these problem types are:
- **Satisfaction** problems called with `satisfy` find all possible solutions that satisfy all constraints.
- **Maximize/Minimize** problems called with `maximize`/`minizmize` take an equation which is used to find the largest or smallest solution.

# Output
**Output** functions as the print statement of the language. It is able to specify a list of strings which are printed with the `\(<var>)` allowing for a formatted string. In addition to the formatted strings non-string types can also be displayed with `show(intval)` for integers, `show_float(numChars,floatVal)`

# Types
The basic types found within Ampl are integers (`int`), floating-point numbers (`float`), Booleans (`bool`), and strings (`string`). These types can be coerced through `<type1>2<type2>` such as `int2float`. 

## Arrays
**Arrays** are created with square brackets and have a specified index set in type hint. This index set can be as simple as `[1..n]` or use enumerables or strings to index the elements. Arrays and sets can hold decision variables along with standard variables. These declarations follow:
```MiniZinc
array [1..n] of type: <varName>; % For Parameters Vars
array [1..n] of var type: <varName>; % For Decision Vars
```
The array access can be accessed with `<varName>[i]`. Multidimensional arrays are handled with `array [1..n,1..n]`. This allows the declaration of multidimensional arrays with creation of a literal array following `[|1..n|1..n|]`. Where the pipes represent a nested set of brackets. An alternative syntax for array declaration takes the required dimensions and then converts a flat array to a nested one. This follow:
```MiniZinc
array<n>d(<indexSet1>,<indexSetn>,<flatArray>);
```
**Concatenation** is a common array operation that is called with `++` that combines multiple arrays together.

The index set of an array can be found with `index_set(arr)`. This can be done on multidimensional arrays with `index_set<x>of<n>`.

**List comprehensions** can be used on both sets and arrays. They follow a structure of declaring a for generator statement with an optional `where` clause which restricts variables. They can also be done with multiple variables with a comma. These look like:
```MiniZinc
[i + j | i, j in 1..n where i<j];
```

#### Aggregate Functions
**Aggregate functions** are used to compile array results. These include:
- **Maximum & Minimum** (`min`/`max`) which find the largest or smallest element.
- **Sum** (`sum`) which finds the sum of all elements.
- **Product** (`product`) which finds the product of all elements.

Some additional aggregate functions are those which follow [[Predicate Logic|predicate quantifiers]] within logic. They are:
- **For All** (`forall)` ensures all constraints hold and returns a value for it. It follows the syntax `forall <list> <cond>`.
- **Exists** (`exists`) ensures that at least one constraint holds.
- **XOR All** ensures the odd number of constraints hold.
- **If & only If All** (`iffall`) ensures the even number of constraints hold.

The two syntaxes for these functions 
```MiniZinc
aggFunc (<generator>) (<cond>);
aggFunc ([<cond> | <generator>]);
```

Using the `include` statement extra constraints can be used. This include statement can also be converted to `include globals.mzn` as to add all global constraints. Some of these are:
-  **All different** (`alldifferent`) which ensures all elements are different.
- **Cumulative** (`cumalative`)
- **Table** (`table`)
- **Regular** (`regular`)

## Sets
**Sets** are created with curly brackets and have an unspecified length as well as containing no duplicates. They are declared similar and accessed in the same way. They follow a syntax of:
```MiniZinc
set of <type>: <varName>;
set of var <type>: <varName>;
```
Standard **set operations** are provided to allow for manipulation of sets. These are:
- **In** (`in`) which checks for an item in a set.
- **Subset** (`subset`) which checks if a set is within another.
- **Superset** (`superset`) which checks if a set is contained within another.
- **Union** (`union`) which combines two sets together.
- **Intersection** (`intersect`) which gets the elements in both sets.
- **Set difference** (`diff`) which finds the difference between the sets.
- **Symmetric-Set Difference** (`symdiff`) which finds elements not in both sets.
- **Cardinality** (`card`) which gets the amount of elements in the set.

## Enumerables
**Enumerable** types are an *or-type* which is used for defining variable classes. They are done with:
```MiniZinc
enum Enumerable;
enum Enumerable = [Enum1, Enum2, ...,EnumN];
```
These can be used within arrays or variables to allow for decision's with respective variable bindings. The `card` and `min`/`max` operations can also be used on enumerables. Unique operations on enumerables include `enum_next(X,x)`, and `enum_prev(X,x)` which gets the previous or next element of `X` within enumerable `x`. The `to_enum(X,i)` maps an integer expression to an enumerable. This allows for ordering operations to be done. **Anonymous** enumerated types are created with `anon_enum(x)` where `x` is a fixed integer expression defining the size of the enumerated type.

# Functions & Predicates
**Functions** are similar to other languages. They are declared with the `function` keyword and require a return type. They can take parameters or decision variables as arguments. Their syntax follows:
```MiniZinc
function <type>: <funcName>(<type>: <argName>) = ...;
```
**Predicates** are similar to functions however have a return type of Boolean values. There syntax is exactly like functions except with the `predicate` keyword.

**Local variables** are declared with the `let {...} in ...`. This allows a series of variables to be declared that are used within a block of code. **Local constraints** can be declared to

# Option Types
Option types are an abstraction which allows for decision variables that represent a possibility of a value or nothing. With nothing or *absent* being equal to `<>`. 
```MiniZinc
var opt <type> : <name>
```

# Datafiles
Datafiles are a way of indicating a set of variables that can be used within a model. They have the file extension `.dzn` and can be used by calling `minizinc file.mzn file2.dzn`. **Assertions** are a type of constraint that upon failure throws an error. They are commonly used along with datafiles to ensure data follows the correct shape. Assertions follow a structure:
```MiniZinc
constraint assert(<bool-cond>,"Error Message",<return-true>);
```
The last argument is an optional argument to specify what happens if a value passes the condition. 

