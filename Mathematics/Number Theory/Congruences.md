A congruent relation is a [[Relations#Equivalence Relation|equivalence relation]]. A value is considered **congruent** if:
$$ a \equiv b\;\bmod n$$
Where $n$ divides $a-b$ or $a=kn +b$ for some integer $k$. This translates simply to both numbers having the same remainder when divided by integer $n$.

Congruences can be substituted with the rule $a_1 \equiv a_2 \;(\bmod n)$ and $b_1 \equiv b_2 \;(\bmod n)$ is equivalent to $a_1+b_1 \equiv a_2+b_2 \;(\bmod n)$ and $a_1b_1 \equiv a_2b_2 \;(\bmod n)$. This is due to congruences being transitive. They can also be fully divided by a single term resulting in the same result.

# Linear Congruences
An equation in the form of $ax \equiv b\;(\bmod n)$ is called a linear congruency. Where $x$ is the result that usually contains an entire congruence class, thus infinitely many solutions. This equation can be found as linear and written in the form:
$$ax-yn=b$$
This is considered a **Linear Diophantine Equation** where the solution can be found as:
$$ d = \gcd (a,n) $$
Where if $d = 1$ then for integers $x'$ and $y'$ such that $ax' - ny' = b$:
$$x = x'\;(\bmod d)$$
If $d>1$ and $d/b$ then:
$$\frac a d x \equiv \frac b d \; (\bmod \frac n d)$$
Then use the above method to solve. However, if $d\not/b$ then there is no solution.

## Modular Inverse

A modular multiplicative inverse is an integer x such that:
$$ax \equiv 1 \; (\bmod n)$$
These inverses can be found using the extended [[Number Theory|Euclidean algorithm]].
