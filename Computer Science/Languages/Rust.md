Rust is a [[Programming Paradigms|multiparadigm]] programming language which focuses on a low-level approach to modern programming languages concepts. It enforces type and memory safety while also following a rule of *zero cost abstractions* for all technology. The main use of Rust is as a systems language.

# Basic Syntax
Rust follows [[C Language|C-like]] syntax, with curly braces and semicolons for new lines. **Function declaration** is done through the `fn` keyword. **For loops** follow a `for ... in ...` pattern, with the `Range` function or `..` used to generate a series of indexes. **Variable declaration** is done with the `let` keyword.

**If-statements** follow a traditional approach however can also be used as a ternary operation given the curly braces only contain a single expression. **Loop** is an expression to call an infinite loop until a break statement is called. It can be used in place of a value where `break val` can be used to return a value.

# Type System
Rust follows a static strongly typed system. Variable declaration uses the `let` keyword and can either uses type inference or a colon to signify a type.
```rust
let var : type = ...
```
There are three types of variables found within Rust. These are:
- **Immutable variables** all variables are considered constant variables unless specified. If a new variable is given the same name it is commonly referred to as **shadowed**.
- **Mutable variables** declared with `let mut` which allocates memory within the heap.
- **Global Constants** declared with `const` signify a heap variable that is static.

Functions types are denoted by `fn(T) -> T`. In addition to this **generic types** can be used during the declaration of functions with `fn func<T>`.

## Primitives
Rust has a 4 main primitive or **scalar** types. These are:
- **Signed Integers** `i8`,`i16`,`i32`,`i64`,`i128`, and **Unsigned integers** `u8`,`u16`,`u32`,`u64`,`u128`. With further subcategorization by decimal, hex, octal, binary, `u8` byte. 32-Signed being the default type.
- **Floating Point numbers** `f32` and `f64`, with 64-bit being the default type.
- **Booleans values** `bool`.
- **Characters** with `char`.

In addition to these types there are compound types which group together multiple values. These are:
- **Tuples** which are called with brackets `(...,...,...)`, and can be unpacked.
- **Arrays** which are called with square braces `[...]`, and must have the same type. There type signature follows `[type; length]` where the length denotes the amount of elements.
- **String Literals** are of type `str` and function as immutable arrays of characters.
- **Slices** are segments of a array, tuple or string. They are called with `val[s..e]`, where `s` is the start index and `e` is the end index. Usually these values need to be a reference to a value as to avoid deletion.

## Collections
Beyond the basic arrays and tuples there are a variety of other [[Data Structures|data structures]] which can be found standard within the prelude library.

#### Vectors
Vectors are dynamically sized arrays. They can be created with `Vec::new()` or the macro `vec![...]`. Vectors can be added to with the `push()` operation and called by index with `get()`. Get returns a some type.

#### Hash Maps
Hash Maps are key value pairs which are created with `HashMap::new()`, and added to with `insert(key,val)`. The `get(key)` returns a some type of a value. The `entry()` keyword is a special keyword that checks if a given value exists and if not returns an entry Enum. This can then be called with a `or_insert()` to insert a value if one doesn't exist.

## Structs/Records
Structures, records or 'and types' are Rust's way of simulating object like entities. These values can be created with `struct` and instantiated with the name. The **spread syntax** `..obj` can be used to copy all fields except ones specified. **Tuple structs** are another method of creating structures without key value pairs. This is done through `struct Name(types)`, where each type signifies a value.

**Empty Structs** can be used for cases where a type has only traits and no values.

## Enums
Enums, or 'or types' are similar to Enums in other languages where Enums function as a set of possible types which may hold a value. This syntax follows:
```rust
enum T {
	T1(...)
}
```

# Ownership
Rust uses a system of ownership to govern memory management. The core of this system is that all values have one owner which once out of the scope will remove the value from the memory. This means all heap variables are restricted to the scope they are declared. Thus, rather than using the `drop` command to remove a variable, it is automatically done.

Like other languages variables are just pointers to a heap allocated variable on the stack. Unlike other languages assignment of a variable to this pointer will result in the previous variable throwing an error if called. This stops a *double free error* and means shallow copies throw an error. Thus, rather than copying it **moves** the value. Stack variables don't follow this rule and thus are able to be **copied**.

When a heap variable is used as an argument that variable's owner becomes the function rather than the current scope. Adversely, when a value is returned its owner becomes the scope the function was called.

## Lifetime Annotations
When functions accept arguments the compiler can usually infer the lifetimes of specific variables. This inference is called **lifetime elision**. While elision works for three specific cases, these are functions that don't return a reference, one reference input parameters, and functions with a self as first parameter. In cases where this doesn't happen explicit lifetimes annotations must be used.

Lifetime annotations are parametrized with `'` in front of them. For example `fn func<'a, 'b>(x:&'a i32, y:&'a i32)` would create two values which are guaranteed to have a lifetime longer than the function's call.

## References
**References** are variables which hold a pointer to a stack variable. This variables can be used within functions as to not drop the original variable as it does not own the original stack variable. This is called **borrowing**. References are immutable and can't be modified. 

**Mutable references** are created with the `&mut` and allow for a reference to be called as a way to edit a heap variable. The main restriction is that if a mutable reference exists in a scope no other references can exist. This avoids race conditions or possible other errors.

# OOP
Rust's uses an alternative object-orientated approach with types and interfaces rather than objects. To follow this standard implementations and traits become the main operations done to achieve this.

## Implementation
Methods for Enums, and structs are defined within a `impl` block. This contains a list of associated functions with the respective objects. It follows a syntax of:
```rust
impl T {
	fn func(&self) { ... }
}
```
Where `&self` is shorthand for `self:&Self`. Additionally these methods can be called on a reference or dereference.

## Traits
A trait is similar to an [[Object Orientated Programming#Interfaces|interface]] found within other object-orientated languages. They are declared with the trait keyword and offer the ability to implement the functions for specific types. Traits can have a default implementation defined within the trait body. To implement a trait use the `for` keyword along with the respective type the functions are implemented for.
```rust
trait Trait {
	fn func(&self) { ... }
}
impl Trait for Type { ... }
```
Traits can be taken as parameters by simply calling `t: &impl Trait` for simple traits and `<T: Trait>(t: &T)` for cases where multiple traits are required. Multiple traits can be specified through the plus syntax `+`. The `where` syntax is another approach to defining obvious types. This follows:
```rust
fn func<T,U>(t: &T, u: &U)
where 
	T: T1 + T2,
	U: T2 + T3
{ ... }
```
Traits can also be returned simply with `-> impl Trait`.

# Pattern Matching
Pattern matching is the process of testing a value for a certain structure. This can be as basic as a traditional switch case, or can follow more complex patterns. Multiple patterns can be done through the `|` syntax. When testing for Enums the common approach is to use the namespace of the Enum for the specific type. Value ranges can also be matched through the `..=` operator.
```rust
match x {
	1..=2 | -1 => ...    // Or Match
	E::t1 => ...         // Enum Match
	S {s1: 0, s2} => ... // Struct Match
	_ => ...             // Rest of the Cases
}
```
Destructuring is a common approach where match assigns specific variables to subfields. This is done through calling the constructor and matching specific values

**If-let** is a new syntax option for if statements that functions similar to a match case with two values. It allows for values to be destructured. It follows:
```rust
if let X {a,b} = x { ... } 
else { ... }
```

# Packages
Packages and imports are handled through crates. These function as modules and sub modules which are created with `mod name` and allow for a namespace to be defined. These modules and functions within the module can be classified as public with `pub`. This enables files that call a `use` to be able to call the respective functions.

# Option & Result
The option and result types are common Enums that are found within Rust. They allow for two types of ways for returning given a failure, with option being a passive version and error being a more active type.

**Option** is a type used for optionally returning a value `Option<T>`. The type is made up of `None` or `Some(T)`. Options are usually used for values which may or may not return an input.

**Error handling** is done through the `Result<T,E>` for errors that can be handled and `panic!` for execution to be force stopped. Result has the Enums `Ok(T)` and `Err(E)` which signify if the program throws and error or a success. The `?` keyword can also be used with the result type to return the error before other actions are called.

# Closures
Closures are an alternative syntax for functions that capture certain arguments to create functions.
```rust
let func = |x: i32| -> i32 { ... } // With Types
let func = |x| { ... }             // With No Types
```
**Iterators** are a pattern that allows for operations to be done sequences of items. They are lazy evaluated and can be used with traditional map, filter, and reduce operations.  

# Unsafe
Unsafe rust is a paradigm within Rust which enables the writing of code which is considered unsafe through calling of `unsafe{...}` blocks. This allows the writing of code whose safety relies on invariants the compiler can't check. This means the unsafe block is an assertion that the code within the block follows the rules of Rust, meaning the process of borrow checking falls upon the programmer rather than the compiler. This can be used for hardware devices, when calling external code, writing concurrency primitives, and in performance optimizations. 
