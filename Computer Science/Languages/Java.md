Java is an [[Object Orientated Programming]] language which compiles to an intermediate representation that is ran by the Java virtual machine or JVM.

Java is a [[C Language|C-like]] in its syntax with curly braces to represent blocked scope.

# Basic Syntax
Java has support for both blocked scoped if statements, as well as ternary statements. These use the forms:
```java
if (cond) {
	...
} else {...}
(cond) ? ... : ...
```
Beyond if-statements switch statements can also be used.

Both while loops and do-while loops are supported. They follow syntax similar to C with:
```java
while (cond) {...}
do {...} while (cond)
```
Java has supports the for loop and the for-each loop. These use the syntax:
```java
for (type var; cond; var++) {...}
for (type var : array) {...}
```

# Datatypes
Java supports the basic datatypes of **integers**, **floats**, **characters**, **Booleans**, and **strings**. These types can further be designated as a **short**, **long** or **double**

**Casting** can be done with two types of syntax. One for cases where the datatype previously used is smaller than the casted type, called **widening casting**. The other case for when the original datatype is larger than the new type, called **narrowing casting**. These use the syntax:
```java
int x = val
float y = x
// to convert back
int x = (float) y
```

# Arrays
Arrays can be declared with the syntax:
```
type[] = {...}
```

Arrays have the following common operations:
- `.concat()` which adds two arrays together.

# Common Classes
The **Math** class can be used to call more complicated math operations. These include basic max or min operations, to random numbers.

# Classes
Classes are declared with the `class` syntax. Additionally they to specify a scope. Classes can be specified as either **public** which means they are accessible by other classes, or **default** which means they are accessible by classes in the same package.

**Inheritance** can be done through the syntax:
```
class x extends y {...}
```
The `super` object can be called within the child class. This allows for attributes from the parent to be shared. A function override can be done with the `@Override` syntax being called before the function. This allows the class to change its parents function definitions.

## Methods
Methods can be declared within a class. During the definition a return type and a scope must be specified. Methods can be overloaded. Methods can be modified to be:
- `public` which means they are accessible by all classes.
- `private` which means they are only accessible within the declared class.
- `default` which means they are only accessible in the same package.
- `protected` which means they are only accessible in the same package and sub classes.

# Packages
Packages can be called with the `import` syntax. This allows for functions or objects to be used from outside packages. The `package` syntax can be used to create and compile a package.
