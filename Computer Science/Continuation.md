A continuations is considered a datatype in programming that contains where a functions continues onto. Within memory this means maintaining a stack and passing it onto the next part of the programs state.

# Continuation-Passing Style
In the [[Functional Programming|functional paradigm]], continuation-passing style or CPS, is a style of programming which uses control passed in the form of a continuation. This is as opposed to the normal direct style of programming. To write in CPS a function must take an extra argument of a continuation function. This means once the function has returned it calls a continuation function with the return value as an argument. This makes procedure returns, intermediate values, and order of evaluation explicit as opposed to implicitly. It also makes all function calls into tail recursions which can lead to optimised performance.

CPS can actually be found in compilers as an intermediate representation for functional languages.

CPS has x main advantages. These are:
- **Optimised**, due to all calls being tail recursion.
- **Easy to Bugfix**, as all intermediate values can be accessed.

CPS is done by passing the return value of a function into another function. This forces the code to be rationalised one at a time in a more sequential manner. An example of this using the identity function:
```js
const id = (x, cont) => cont(x)
```
