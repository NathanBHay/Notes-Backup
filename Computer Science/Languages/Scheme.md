Scheme is a dialect of [[Lisp]] which focuses on simplicity. Scheme bases itself on a linked list structure where code is constructed from list elements. These list elements are called `cons`, and contain two pointers. These pointers are called the `cdr` and `car`. The `car`, or Contents of Address part of Register, stores the first bit of data, while the `cdr`, or Contents of the Decrement part of Register, which stores the next elements. These values can be accessed with their respective functions.

Literals that don't use a cons structure are called **atoms**.

# Special Forms
Scheme has two kind of operators these are **functions**, as mentioned previously, and **special forms**. Special forms rather than evaluating their arguments do special operations which don't match the behaviour of functions. Special forms include **quote,** **lambda**, **define**, **if**, and **set**.

**Quote** can be used to protect tokens from evaluation. This allows for an expression to be parsed to the outer expression instead of evaluating itself first. Quote can be called with `quote` or abbreviated with the `'()` syntax.

## Functions
**Define** can be used to bind a name to a value. It takes a name and a value argument and follows the syntax `(define name val)`. **Lambda** is used to declare functions along with the define operator. Lambda takes a list of arguments as the first parameter and a function body. It follows the syntax:
```scheme
(define name 
  (lambda (arg)
	  (body)))
```

To define local variables use the `(let ((name val) (...)) body)` operation. The let operator can also be used to create local looping operation. This uses recursion to call a local variable. To do this use the syntax:
```scheme
(let loop(args)
  ...
  loop(args))
```

**Letrec** is another way of creating loop structures but allows for a recursive declaration within its definition.

**Do** is another loop syntax which is similar to a for loop. It functions through the syntax:
```scheme
(do ((var initialVal incrementVal))
	(predicate value)
	body)
```

**Set** is another syntax for assigning values. While it's similar to `define` set can change a value in a global scope. This follows the syntax `set!`. The result of a set is an internal state and therefore creates a side effect. `set-car` and `set-cdr` can be used to set the respective parts of the cons cell.

## Control Flow
Another special form which is commonly used is the **if** form. It operates on a basic conditional structure of `(if condition trueVal falseVal`. Conditions can be further constructed using the `and`/`or` forms. One note is that these operations are not in infix notation.

Further branching operations can be done with the **Cond** form. It functions similar to a switch statement, and evaluates based on the syntax:
```scheme
(cond
	 (pred1 clause)
	 (pred2 clause)
	 (predX clause)
	 else clause)
```
The **else** operation allows for a default operation to happen if none of the conditions evaluate to true.

#### Conditions
There are a variety of common functions to construct conditions. The most essential operators are `eq?`, `eqv?`, and `equal?`. These operations follow the rule:
- **Eq** compares the addresses of two items and returns true if they are the same.
- **Eqv** compares the types and values of an two items.
- **Equal** compares sequences of lists or strings.

**Type** checking functions are alternative ways to create conditions based on the type of the atom. These operators are:
- `pair?` which returns if the object contains cons cells.
- `list?` checks if the object is a list. Keep in mind `()` is a list.
- `null?` checks if the object is `()`.
- `symbol?` returns if the object is a symbol
- `char?` and `string?` returns if the object is a character or string.
- `number?`, `complex?`, `real?`, `integer`, and `rational?` all return true if it matches the same datatype.
- `exact` and `inexact` check if the value is a floating point value.

Common comparison functions can be used with the syntax `=`, `<`, `>`, `<=`, `>=`. These operations all compare numbers along with the other useful functions `odd?`, `even?`, `positive?`, `negative?`, and `zero?`.

Character comparison operators are another useful construct. These operators include:
- `char<?` which checks if first character has a lower ascii value. `char>?` does the opposite operation.
- `char=?` checks if characters are the same.

These operations can also be swapped out with the word `string` to do the same operations on strings. An extra function string adds is `string-length`

# Higher Order Functions
Scheme has support for all the basic [[Functional Programming]] list operations. These include **map**, **for-each**, **filter**, **fold**, **sort**, and **apply**. Most of these can take multiple lists. **Sort** is structured differently with the list going first and the comparison operator following it. **Apply** is similar to fold and map.

# IO
Input and output can be done with the following functions:
- `open-input-file` can be used to open a file.
- `read-char` is used to read a character from a file.
- `eof-object?` is used to check if the file is at its end.
- `read` which is used to read expressions.

A safer way to handle files is using functions that parse files as arguments. These functions include:
- `call-input-from-file` which takes a *filename* and a `procedure`. This will then need to be closed with `close-input-port`.
- `with-input-from-file` is similar to the latter however closes automatically.

All these methods can be called with `output` instead of `input` if a file needs to be written. To write a file from an output port use:
- `write` which takes a *object* and a *port* to write to. It writes strings with double quotes and characters with `#\`.
- `display` is similar to write however strings are not enclosed with double quotes.
- `newline` begins a new line.
- `write-char` outputs the character to the port.

# Casting
All basic types can be cast into different types with the syntax `type1->type2`. Some common casting operations include - `string->char`, `num->char`, `symbol->string`, and more.

# Data Structures
There are a few basic data structures which cant be found within scheme. These are lists, and hash tables.

**Lists** are declared with either a linked list of cons elements, or with the `list()` syntax. This creates a linked list which can be accessed through functions.

**Hash Tables** can be create with the `make-eqv-hash-table`, `make-equal-hash-table`, and `make-string-hash-table`. These functions create a hash table with an optional `size` specified. Hash tables can be modified with `hash-table/put!` which takes a *hash-table*, a *key*, and *data* to insert. Hash-table elements can be accessed with `hash-table/get` with it having the same arguments as put but instead of data has a *default* value if nothing is found.

**Vectors** are represented with `'#(...)`, and can have any data type. They have the following common functions:
- `vector?` which checks if the object is a vector,
- `make-vector` which returns a vector with *k* elements, with an optional *fill* argument.
- `vector` which returns a vector consisting of the arguments.
- `vector-length` which gets the length of a vector.
- `vector-ref` which gets the *k* element of the vector.
- `vector-set!` which sets a vector element in position *k*.

# Macros
Macros allow the definition of unique syntax. The binding for these operations are done with `define-syntax`, `let-syntax`, and `letrec-syntax`. These operations bind syntactic keywords to macro transformers instead of binding variables to locations. The `syntax-rules` syntax further expands this to minimize use of the latter special forms. Using syntax rules a macro can be declared with:
```scheme
(define-syntax val
  (syntax-rules ()
	  ((args)
		  (body))))
```

