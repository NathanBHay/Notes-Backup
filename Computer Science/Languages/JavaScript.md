JavaScript is one of the most popular web programming languages. JS can be considered the programming language used in conjunction with [[HTML]] and [[CSS]]. First created for Net scape as an attempt to unify a web language that could be run within the browser. From these roots Java Script has evolved to be a multi [[Programming Paradigms|paradigm]] language. Thus, JS is a [[Programming Paradigms#Static or Dynamic Typing|dynamically typed]], [[Object Orientated Programming|object orientated programming language]], with [[Functional Programming|declarative]] paradigms. JS has gone through many iterations; the current one is **ES6**. **ES6** is a superset of the previous **ES5** and has many extra features.

# Basic Syntax
Java script uses dynamic variables that are declared with the `let` keyword for mutable variables, while immutable variables are declared with `const`.

Java script has a **ternary operator** which functions as a one-line if statement. This is written with the syntax:
```
<condition> ? <true result> : <false result>
```

**Functions** are declared with the `function` keyword, followed by brackets for arguments, and curly brackets for the scope.

# Classes
A class follows paradigms set within [[Object Orientated Programming]] and as such is used to encapsulate functions and variables. The body of a class has a **constructor** which is called upon instantiation of a class. The `super` keyword is used as to call the constructor of inherited classes. The `class` keyword is used to create a class.

Within JS a new object can be created with the keyword `new`. In many cases an object can be constructed and populated with multiple data fields. It can be considered a collection of properties indexed by a hash table. Therefore, an object is **immutable** but the data inside an object is **mutable**. **Functions** in java script can also be considered objects, this allows easy closure.

The `object.create(clonedObj,newObj)`, follows a [[Design Patterns#Prototype|prototype]] pattern where a new object can be created by adding additional fields or methods from a clone. To find this prototype use the `Object.getPrototypeOf(obj)`.

# Arrow Functions
Arrow functions are a compact notation for [[Functional Programming#Anonymous Functions|anonymous function]] that follow the structure:
```
<parameter> => <operation of parameter>
```
These anonymous functions can also have their own scope if curly brackets are used. Arrow operators can be used in conjunction with [[Functional Programming#Pure Array Methods|pure array methods]] as to modify arrays. The main pure array methods being:
```js
array.map(f: Elem=>Out)
array.filter(f: Elem=>Out)
array.reduce(f: (Accum,Elem)=>Out)
array.foreach(f: U=>Void)
```

These arrow functions can be **curried** through the stringing of arrow operators together as to make multiple arguments for the function.
