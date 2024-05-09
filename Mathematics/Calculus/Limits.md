A limit is the value that a [[Relations|relation]] or [[Functions|function]] approaches as the variable comes closer to a given point. It makes a core component of calculus used of the definition of [[Differentiation|derivatives]]. The definition of a limit can be written as:
$$\lim_{x \to c}f(x)=L$$
Where $L$ is the result of the value, $x$ going closer to $c$. Limits have a further definition in the **delta-epsilon definition** which shows that for value every positive value $\epsilon$ from $L$ there exists a pair $\delta$. Thus, if $x$ is closer than $\delta$ to $a$ then $f(x)$ is closer than $\epsilon$ to $L$. This can be written as:
$$\text{if } 0<|x-a| < \delta, \text{ then } |f(x)-L| < \epsilon$$
This formal definition is used to prove the existence of limits, and to be used within logical theorems.

Some limits don't have a limit which can be approached from both sides. These are called **one sided limits** and are approached from the left and right sides. If approached from the **right side** it can be written as:
$$\lim_{x \to c^+}$$
While the limit approached from the **left side** can be written as:
$$\lim_{x \to c^-}$$
From this we find that a limit approachable from both sides exists if the left and right side are equal.

Limits with **infinity** are found with a few basic ideas. With any asymptote being found as the result of the limit. In cases of a vertical asymptote the result depends on the direction of approach.

# Continuity
A function can be considered **continuous** if a function is connected at all points. This can be defined as at any point $c$ there is the rule:
$$\lim_{x \to c}f(x)=f(c)$$
If a function isn't continuous then the function is considered **discontinuous**. These can be considered in the types:
- **Removable** if you can calculate a value that exists for it.
- **Jump** if it jumps from one points to another.
- **Infinite** if it tends towards a point infinity.
- **Oscillating** if it oscillates to much to have a concrete limit.

# L'Hôpital's Rule
L'Hôpital's rule is a theorem used to evaluate limits of indeterminate forms. This mainly being those which contain infinities and zeroes. It can be written as:
$$\lim_{x \to a} \frac {f(x)} {g(x)} = \lim_{x \to a} \frac {f'(x)} {g'(x)}$$
This equation must be differentiable from either side of the equation. Furthermore, the limit on the right must exist. This equation can be used continuously until a form different from $x=a$ is found.

# Limit Theorems
Finding the limits of a value has a set of common rules. These fundamental rules, where $\lim{f(x)} = L$ and $\lim g(x) = M$, are:

| Rule     | Note                                              |
| -------- | ------------------------------------------------- |
| Sum      | 
$$\lim_{x\to c}(f(x) \pm g(x)) = L\pm M$$
         |
| Product  | 
$$\lim_{x\to c}(f(x) \times g(x)) = L \times M$$
  |
| Quotient | 
$$\lim_{x\to c} \frac {f(x)} {g(x)} = \frac L M$$
 |
| Power    | 
$$\lim_{x\to c}(f(x))^n = L^n$$
    |
| Root     | 
$$\lim_{x \to c} \sqrt[n] {f(x)} = \sqrt[n] L$$
   |

The **limits of polynomials** can be found easily through the general rule:
$$\lim_{x \to c}=P(c)=a_n c^n + a_{n-1} c^{n-1} + \dots + a_0$$
A **rational function** can be found through the general rule:
$$\lim_{x \to c} \frac {P(x)} {Q(x)} = \frac {P(c)} {Q(c)}$$
# Vector Function Limits
A [[Functions#Vector Functions|vector-valued function]] has a unique limit which is defined by the rule:
$$\lim_{t \to t_0} r(t)=L$$
Where $r(t)=f(t) \hat i + g(t) \hat j + h(t) \hat k$. Vectors also have a delta-epsilon definition however, we'll ignore that for now.
