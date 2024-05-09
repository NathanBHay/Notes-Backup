Clojure is a dialect of [[Lisp]] that is written within the [[Java|JVM]]. Due to the reliance on Java it has interoperability with Java libraries. Clojure recognizes two kinds of structures - **literal representations** (datatypes), **operations**. Literals are separated by white space.

# Expressions
Clojure has basic Boolean expressions of `true` and `false`. Its null literal is written as `nil` and is considered a false value. To test for a null value use the `nil?` operation.

Boolean connectives are written in word form with `or`, `and`, and `not`. Equality is represented with `=`, with the rest of the comparison operations.

A value can be bound with the `def` syntax. It follows a structure of:
```clojure
(def value "Words")
```

Values can be locally bound with the `let` keyword. This follows the syntax:
```clojure
(let [var val] expr)
```

**Keywords** are values similar to strings however have lower memory overhead. These values are commonly used as keys for maps. They can be declared with a colon in the form of `:value`

# Primitives
Clojure has majority of the basic datatypes other functional languages have. These include the datatypes:
- **Numbers** which can be floating point, fractional or integer values.
- **Strings** which are declared with double quotation marks.

# Data Structures
Clojure's has many different data structures that allow for unique operations.

**Vector**s can be declared with square brackets. This follows the syntax:
```clojure
[item1 item2 ... itemX]
```

**Maps** are similar to hash tables or dictionaries and are declared with curly braces. They have a keyword and an associated pair:
```clojure
{:key "Value"
 :key2 "Value2"}
```
Map values can be grabbed with the `get` keyword. This follows the syntax:
```clojure
(get {:key "Val" :key2 "Val2"} :keyX)
```

**List** are similar to vectors except that they're linear collections. This means they can be only accessed from the bottom and top. They are declared with:
```clojure
'(val1 val2 val3)'
```
To retrieve an element from a list use the `nth` keyword.

**Sets** are collections of unique values. There are two types of sets **hash-sets** and **sorted-sets**. A hash set is declared with:
```clojure
#{val1 val2}
(hash-set val1 val2)
```
A sorted set is the same as a set however forces a sort upon initialization. It can be declared with the syntax:
```clojure
(sorted-set val1 val2 val3)
```

# Control Flow
There are three basic control structures, these are `if`, `do` and `when`.

**If** statements follow a simple structure of:
```clojure
(if condition
	then
	*else)
```

**Do** statements allow the combination of multiple operations ran in successive order. This follows a structure of:
```clojure
(do operation1
	...
	operationX)
```

**When** statements are a combination of *if* and *do* without a false condition. It follows the syntax:
```clojure
(when condition
	operation1
	...
	operationX)
```

# Functions
Functions can be defined with the `defn` syntax. They have a function name, an optional docstring, parameters, and a body. This follows the syntax:
```clojure
(defn funcName
	"Doctring"
	[param1 param2]
	body)
```
These functions can be overloaded by specifying a different parameter amount and body. Furthermore a rest parameter can be used with with the syntax `&`.

**Anonymous** functions or lambda functions are similar to normal functions except they are declared with the `fn` syntax an lack a name. This syntax looks like:
```clojure
(fn [params]
	body)
```
These functions can be declared with even less syntax. This follows the structure of:
```clojure
#(operator % val)
```
This syntax uses the `%` to represent a parameter. Multiple parameters can be called by using a number preceding the sign. It can also be used with ampersand like `%&` to represent all parameters

## Recursion
Recursion can be done with the normal method of calling a function. It can also be done through the alternative loop method. This uses a loop which has a variable array and a body. This body contains a recur operation which resets back to the start of the loop clause. The syntax for this follows:
```clojure
(loop [var val]
	body
	(recur (var)))
```
