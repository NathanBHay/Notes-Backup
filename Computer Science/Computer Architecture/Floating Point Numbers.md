A floating-point number is a representation of numbers that have either a magnitude or decimal place. This is done through each number being represented as a **signed** bit, a **mantissa** (significand), and a **base** with an **exponent**: 
$$\pm a\cdot b^e$$
From this we are able to view a floating point with digits $d_i$ where $i\in[0,p-1]$ and $d\in[0, b-1]$ as a number found as: 
$$x=\pm \Big(\frac{d_0}{b_0}+\frac{d_1}{b_1}+\cdots+\frac{d_{p-1}}{b_{p-1}}\Big)b^E$$
Where $b$ is the base, $p$ is the precision, and $E$ is the exponent $[L,U]$. 

The **IEEE-754** standard is a standardised way of computing floating point numbers. It encodes the value as 1 bit for the sign, 8 bits for the exponent, and 23 bits for the mantissa. This means that the $E$ is $[-127,127]$, the precision is $24$ and $2$ is the base. 

A **single floating point** number is usually represented with 1 word, while a **Double** floating point number uses double the amount of words.

# Error
Not all numbers can be represented with floating point. Therefore to approximate a floating point number one must either truncate, or round. The **machine epsilon** functions as the upper bound on the relative approximation error. This can be calculated as: 
$$\Big|\frac{fl(x)-x}{x}\Big|\leq\varepsilon_{\text{mach}}$$

# Operations
Floating point numbers require different methods of implementing basic mathematical operations. 

**Addition** follows a process of first normalisation the mantissa as to make the exponent the same for both numbers. After this the mantissas can be added together before you can normalise to the new base.

**Multiplication** starts through adding the exponents together to find the correct exponent of the value. After this the mantissa is multiplied, after this normalisation can be done.
