Python is a multi-paradigm programming language

# Lists, Tuples, Etc
Python lists can be constructed with `[...]`, syntax. Python lists are mutable, and can be edited from any position. **Tuples** are the same as lists except they are immutable. **Dictionaries** are similar to lists except they are separated by keys, and value pairs.

# Common Libraries
## Function Tools
The library `functools` is a library which adds increased support for higher-order functions. Some of the extra features it adds are:
- **Memoization** decorator called with `@cache`.
- **Functional Overloads** where the initial function is decorated with `@singledispatch`, and the respective overloads are decorated with `@fnName.register` for code with type hints or `@fnName.register(type)` for code without.
- **Reduce**, statement that can be called with `reduce(fn,iter)`.
