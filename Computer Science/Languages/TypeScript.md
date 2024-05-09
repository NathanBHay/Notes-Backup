TypeScript is a superset of instructions for [[JavaScript]] that adds type features to JS, as to create a statically typed environment. This splits the typescript files into a JS file, and another file that controls the typed namespace. Typescript provides an advantage in error avoidance, as the declaration of types allows avoidance of common errors.

# Types
Typescript has its own primitive types which are **number**, **string**, **Boolean**. These are declared through the format:
```
<var> : <type>
```
These types are further expanded by **union types** which are declared with a *bitwise or* symbol as to declare either of the types. This is written as:
```
<var> : <type 1> | <type 2>
```
With the type **any** being a union type of all three primitives.

To get the return type of a function call the return type command. To get the types of its parameters call the parameter type command. This uses the syntax:
```
ReturnType<typeof fn>
Parameters<typeof fn>[argNum]
```
This can be further expanded with `Awaited` for functions that use promises.

# Interfaces/Records
An interface is a way to create an object which follows the rules of a series of type. This is declared with the `interface` or `type` keyword and functions similar to an object. It also allows for declaration of the return type of a function within an object.

When objects are created the `as const` syntax can be applied to the end as to ensure the immutability of fields within the object.

## Optional Fields
TS allows the declaration of objects with a field that is optional to the codes execution. This is declared as `<var>? : <type>?` where the question mark signifies an ignoring of the field if not given.

# Generic Types
Generic Types are a type which is yet to be inferred by the compiler, however shares a set of operations throughout the code. This is declared though arrows which define a **type parameter**. These follow the syntax:
```
function funcName<Type,Type2>(arg: Type, arg2: Type2):Type2
```
These types are usually single letters capitalised. Generic Types are useful as they allow internal consistency within the code.

# Decorations
A decorator is a special kind of declaration that can be attached to a class declaration, method, accessor, property, or parameter. Decorators follow the syntax of `@expression` where the expression is evaluated to a function. The way a decorator is applied can be modified is through a decorator factory. This is a function that returns the expression called by the decorator at runtime. Multiple decorators can be applied on the same line.

A **class decorator** is applied to the constructor class and can be used to modify or replace class definitions.
