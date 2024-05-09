Lambda Calculus is a model for computation made in the 1930s by Alonzo Church. Lambda calculus represents a basic form of computation which centers around [[Functions|functions]] and is the basis of [[Functional Programming|functional programming]]. Lambda calculus uses a system of syntax which follows the basic symbol $\lambda$ to denote the start of a functional expression. Then follows a list of parameters. Parameters can only take the values of other lambda functions. Lists of parameters are curried which means that $\lambda xy.xy \equiv \lambda x . \lambda y . xy$. These parameters are then separated by $.$ which denotes the start of the function's body. Variables which appear in the functions body are considered **bound** while those that appear as parameter but not in the body are **free**. These lambda expressions are anonymous.

Lambda expressions have a direct link to mathematics. For example the identity function $\lambda x.x$ can be written as $f(x)=x$, and can be further written with arrow functions as `x=>x` or with [[Python]] lambdas as `lambda x:x`.

# Application
Lambda functions can be applied as to produce, or simplify a result. Some of these rules include:
- **Alpha Equivalence** is the idea that all variables can be renamed as to produce the same results. This is as variables only serve to represent functions.
- Lambda expressions can have variables or functions applied to them. This is done by putting a lambda expression next to a variable. This looks like $(\lambda x.x)y$ where $y$ is the variable which is being applied by the expression. This then gets substituted with the syntax $(\lambda x [x:=y].x)$, where the statement produces $y$. This process of substitution is called **Beta Reduction**.
- **Eta Conversion** states that an expression can be simplified by the rule $\lambda x.Mx = M$.
- **Combinators** can be written as lambda expressions. For example identity can be written as $\lambda x.x$, while k-combinator can be written as $\lambda xy.x$.

When a lambda calculus expression is evaluated it is considered in a beta normal form, or **normal** form.

# Church Encodings
A church encoding is the idea that through these rules of lambda calculus any computable system can be created. Thus, the system is Turing complete. For example some basic operations that can be modeled include:
- **True** which is written as $\lambda xy.x$, this being a k-combinator, and **false** written as $\lambda xy.y$, this being a k-combinator and an identity combinator.
- **IF** can be written as the expression $\lambda btf.b\;t\;f$. Where **if true** the expression returns $t$ and **if false** the expression returns $b$.
- **Boolean Operators** can be written as $AND=\lambda xy. IF\;x\;y\;FALSE$ , $OR=\lambda xy. IF\;x\;TRUE\;y$, and $NOT=\lambda x. IF\;x\;FALSE\;TRUE$.

# Divergence
Divergence happens when a lambda expression cannot be simplified as the expression infinitely reduces without finding a result.

The **Y-Combinator** is an example of divergence which simulates recursion. It can be written as $\lambda f. (\lambda f (x X))(\lambda x . f(xx))$, which can be translated to JS as `f=> (x => f(x(x)))(x => f(x(x)))`.
