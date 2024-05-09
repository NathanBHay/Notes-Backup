Linear algebra is a branch of mathematics which deals with fundamental units of **vectors** and **matrices**. While vectors and matrices don't naturally appear within nature like most mathematical concepts, they function as an abstraction which allows for complex calculations. These calculations usually revolve around [[Linear Equations|linear equations]] within multiple dimensions.

**Vectors** are a unit which is an element defined within vector space which is indexed by a column. They are used within computer science as [[Abstract Datatypes|arrays]] and throughout mathematics. Vector variables are written with an arrow above their head and represent a column of unique values. This is written as:
$$\vec{X} = (x_0, \dots, x_n)= \begin{bmatrix}x_0\\ \dots \\x_n \end{bmatrix}$$
Another common way to write vectors is with component variables. Therefore, a basic vector can be written as:
$$\vec X = a \hat i + b \hat j + c \hat k$$
This form uses each of the hatted letters to represent each of the directions of the vector. This definition will be later expanded upon, however in general proves nice form.

**Vectors** are considered to have a **magnitude** and **orientation/direction**. This magnitude in higher dimensional space being the measured quality while the other variables effecting its position. Within **Euclidean space** a vector follows the basic idea of a line drawn from any point within the graph. This can be visualised as:
![[Pasted image 20220508233951.png|#invert|300]]
The **Euclidian norm**, or the value which fines the magnitude, is defined as the length of a vector. This is based on the distance formula and is written as:

$$||v|| = \sqrt {v \cdot v}$$
**Matrices** are a two dimensional variant of a vector. While some operations change for matrices, matrices keep most of the vector operations. They are indexed by row and column. They are written as:
$$X = \begin{bmatrix}x_{1,1} & x_{1,2} & \dots & x_{1,n}\\
x_{2,1} & x_{2,2} & \dots & x_{2,n}\\
\vdots & \vdots & \ddots & \vdots\\
x_{n,1} & x_{n,2} & \dots & x_{n,n}\\
\end{bmatrix}$$
More than just arrays, matrices can be used to represent systems of linear equations, and linear functions.

## Linear Combinations
**Addition** of vectors and matrices is done on ones with matching rows and columns. It adds values indexed the same together. This is written as:
$$\vec A + \vec B = \begin{bmatrix} a\\b\end{bmatrix} + \begin{bmatrix} c\\d\end{bmatrix} = \begin{bmatrix} a+c\\b+d\end{bmatrix}$$
**Vector Addition** can be visualized as one vectors start being the end of another, as to provide the shortest path towards that end point. Another interpretation is the **parallelogram law** where the addition of two vectors forms the top right point of the parallelogram, with the two input vectors being corners of the parallelogram.

**Scalar Multiplication** is the multiplication by a non-vector value. It is visually done by expanding the magnitude of the function, to provide a longer line.

The operations of **addition** and **scalar multiplication** build up to produce a **linear combination**. These are defined as a vector with a constant term added together. This can be defined as:
$$a_1 \vec v_1 + a_2 \vec v_2 + \dots + a_n \vec v_n$$
These linear combinations are all multiplied by a scaling factor $a$. Any vector can be represented by a linear combination of vectors. From these combinations we can defined a **span** which is considered the [[Set Theory|set]] of all possible linear combinations. This span is can be commonly visualised as a plane of values within real coordinate space.

## Unit Vector
The **unit vector** or direction vector is a vector's whose length equals one, meaning $v \cdot v = 1$. These are used within decompositions as to provide a base form of vectors which all terms are multiplied by a direction to indicate the direction. A unit vector that has the same direction as $v$ can be found with the equation:
$$\hat u = \frac {v} {||v||}$$
Common convention leads to $\hat i$ being a move in the $x$ direction, $\hat j$ being a move in the $y$ direction, and $\hat k$ being a move in the $z$ direction.

## Independence & Dependent
A vector is considered **independent** if that vector by adding it to a linear combination produces a new set of results, that are not in the plane already established by the initial terms.

A **dependent** vector is one such that the new vector already exists in the plane established by the other terms. Dependent terms can be commonly removed from a combination as to provide a simpler combination. A set of vectors is linearly dependent if and only if at least one coefficient is non-zero and equal to a zero vector. This means if the sum of other vectors minus a dependent vector, then the result is zero.

## Dot Product
**Dot Product** is the sum of all values within a vector multiplied. Geometrically this is done on a 2-dimensional plane by projecting two vectors onto 1-dimensional space. Therefore, the dot product can be interpreted as a linear transformation. This operation is done on vectors of equal size, and can be written as:
$$a \cdot b = \sum_{i=1}^n{a_ib_i}$$
The **dot product of itself** is represented with differing syntax. This is represented as:
$$||a||^2 = \sum_{i=1}^n{(a_i)^2}$$
The **Manhattan norm** is defined as the length of the vector without jumping diagonally, only travelling in axis directions. This is defined as:
$$||x|| = \sum_{i=1}^n |x_i|$$
**Perpendicular** values are define as those that the dot product is equal to zero. Thus, if $v \cdot w = 0$ then these terms are perpendicular to each other. Perpendicularity can also be defined as the angle between to vectors being equal to $\frac \pi 2$. This perpendicularity is commonly called **orthogonality**.

The dot product can be used to find the angle of a vector. The **cosine formula** illustrates this through the rule:
$$\cos \theta = \frac {v \cdot w} {||v||\; ||w||}$$
**Schwarz Inequality** states that since the unit vector never exceeds one and cosine will never exceed one we find that:
$$|v\cdot w| \leq ||v|| \; ||w|| \text{ and } ||v+w|| \leq ||v|| + ||w||$$
## Projections
A projection is a linear transformation on vector space such that the first result is equal to the second. This can be seen as how a square is a 2-dimensional projection of a 3-dimensional cube. This can be seen as a compression of information onto another dimension such that information isn't lost. The process results usually in a lower dimensional vector space as the result.

A **scalar projection** is simply the shadow case by one vector upon another. This scalar projection is given by:
$$v_w=\frac{v \cdot w}{|w|}$$
A **vector projection** produces a shadow with length equal to the scalar projection. This is given by:

$$v_w=(\frac{v \cdot w}{|w|})w$$
 
## Cross Product
The cross product of two vectors is used to find a new vector in $\mathbb{R}^3$ space. This vector's direction is found through the right hand rule, with the index and middle being in the direction of the input vectors, and the thumb being the new direction. Cross product follows the rule:
$$\vec u \times \vec v = (|\vec u|\;|\vec v|\sin \theta)n$$
A more basic rule for a 3-dimensional vector cross product is defined as:
$$\vec u \times \vec v = \begin{bmatrix} u_y v_z -u_z v_y \\ u_z v_x - u_x v_z \\ u_x v_y - u_y v_x\end{bmatrix}$$
From this definition we see that the cross product is a vector, where $\vec u \times \vec v = -\vec v \times \vec u$, and $\vec u \times \vec u = (\vec u \times \vec v) \vec u=0$. As well as that the cross product is distributive, and $\lambda (\vec u) \times \vec v = \lambda (\vec u \times \vec v)$.
Where $n$ is a unit vector perpendicular to the plane of the two vectors, and $\theta$ is the angle between the two vectors on there plane. Vectors are parallel if and only if $\vec u \times \vec v = 0$. The **magnitude** of a cross product, which can be considered the area of the parallelogram produced by the two vectors. It follows the rule:
$$|\vec u \times \vec v| = |\vec u|\;|\vec v|\sin \theta$$
Geometrically the cross product creates a 3-dimensional parallelogram, called a parallelopiped, as the new vector extends the plane into three dimensions. A good way to remember this is that **dot product** uses the law of **cosine**, while the **cross product** uses the law of **sine**.

## Matrix Multiplication
**Matrix Multiplication** is a process that produces a new matrix given the elements from the previous ones. To do this the **dot product** of the rows and columns of each matrix is done. This operation can only be done on matrices where the columns of the first matrix is equal to the rows of the second. This produces a result of a matrix with the rows of the first and the columns of the second. This can be written:
$$(m \times n) \times (n \times p) = (m \times p)$$
With each term being a matrix of size rows, and columns. A **difference matrix** is a matrix which gives the difference between all the inputs in the matrix. This can be written as:
$$\begin{bmatrix}1 & 0 & 0\\-1 & 1 & 0\\0 & -1 & 1\\\end{bmatrix}
\begin{bmatrix} x_1\\x_2\\x_3\end{bmatrix} = \begin{bmatrix} x_1\\ x_2 - x_1\\ x_3 - x_2\end{bmatrix}$$
Matrix multiplication is associative and distributive.

## Identity Matrix
An identity matrix is matrix that does nothing when multiplied. It is used to verify that a matrix is the same, and in inversion. It can be represented as a matrix with a single diagonal line of ones. This is represented as:
$$I=\begin{bmatrix}1 & 0 & 0\\0 & 1 & 0\\ 0 & 0 & 1
\end{bmatrix}$$
These matrices are always square, have a determinant of 1, and is symmetric.

## Inversion and Transposition
An inversion of a matrix is commonly used within linear algebra to solve linear equations. It is done through the general rule:
$$\begin{bmatrix}a&b\\ c&d \end{bmatrix}^{-1} = \frac 1 {ad-bc} \begin{bmatrix}d & -b\\ -c & a \end{bmatrix}$$
The multiplication of an matrix with its inverse will result in an identity matrix. This follows algebraic mathematics where the result is similarly 1. The first term on the right hand side of the latter equation is referred to as the **determinant**, and will be discussed later.

Matrix transposition is a process of flipping a matrices rows and columns. This is written with a matrix to the power of $T$, for example:
$$\begin{bmatrix}a&b&c\\ c&d&e\\ f&g&h \end{bmatrix}^{T} = \begin{bmatrix}a&d&f\\ b&e&g \\ c&f&h\end{bmatrix}$$
A matrix is considered **symmetric** if a transposition of the matrix is equal to the original matrix.

## Vector Space
Vector spaces are an understanding of where a vector is defined.

**2-Dimensional Real Coordinate Space** is commonly referred to as $\mathbb{R}^2$, is defined on all real two tuples. This gives us a space to place vectors that functions similar to the two dimensional graphs commonly seen. Real coordinate space can also be defined on further dimensions with greater vector sizes, this is written as $\mathbb{R}^n$, with $n$ being the amount of dimensions.

**Column Space** consists of all possible linear combinations of the columns in a matrices. This is important as to solve a linear equation the result has to be in the column space of the transformational matrix.

A vector **subspaces** is when one vector space is contained within another.

## Linear Transformations
When a vector is multiplied by a matrix the result produces a new, transformed vector. Through this matrix vector space is modified to fit this new equation. This includes going from higher and lower dimensional frame. The notation for these linear transformations commonly uses $T(vector)$. Some common linear transformations are: 
- $\begin{bmatrix} c & 0\\ 0 & c\end{bmatrix}$ which stretches all vectors by the constant.
- $\begin{bmatrix} 1 & -1\\ 1 & c\end{bmatrix}$ a $90\degree$ rotation for all vectors.
- $\begin{bmatrix} 0 & 1\\ 1 & 0\end{bmatrix}$ a reflection for all vectors.
- $\begin{bmatrix} 1 & 0\\ 0 & 0\end{bmatrix}$ a project which decreases the dimensional subspace of all vectors.

All linear transformations follow some key rules. These are the origin of vectors can't be changed, as coefficient 0 still produces the same starting position of 0. If two vectors go to the same position, they must still both go there after the transformation. Two transformed vectors should produce the same relative results when interacting.

Through the knowledge of the matrix used to transform multiple vectors, we can find out where any vector lies within the dimensions. Each column of this matrices can be considered a unit vector, which determines all the directions in which the consequential vectors are shaped. This transformation on a 2 dimensional plane has the rule:
$$\begin{bmatrix} a & b\\ c & d\end{bmatrix} \begin{bmatrix} x\\ y\end{bmatrix}= x\begin{bmatrix} a\\ c\end{bmatrix}+y \begin{bmatrix} b\\ d\end{bmatrix} = \begin{bmatrix} ax+by\\ cx+dy\end{bmatrix}$$
Vectors projects that decrease dimensional space happen when the one of the basis vectors is linearly dependent on another. This will lead to a decrease in the dimensionality of all vectors on the plane. The **rank** determines how much a transformation has caused this collapse. The first rank being a line on one-dimensional space, the second being a plane, and so on.

**Composition** of transformations happens when multiple linear transformations are applied to a vector. This composition can be found by using matrix multiplication on multiple transformations, with the rightmost transformation being first.

**Orthonormal** transformations are one such that the unit vectors remain perpendicular. 

**Null space** also know as the **kernel** refers to the set of all solutions where the transformation of a vectors results in its origin. To find this use gaussian elimination and equate the matrices to a vector of zeroes to find the equations which equal null space.

## Determinant
The determinant of a matrices is a number that holds special information about the number. This value can be considered an area scaling value. Where if a shape is defined on vector space a transformation will scale the area by the determinant. Some common properties of a determinant are that it is equal to zero when there is no inverse for a matrix. The determinant also changes the sign when the rows are exchanged.

To compute the determinate of a basic two by two matrix use the equation:
$$det(A)=ad-bc$$
The determinate of a three by three matrix can be found as:
$$det(A)=a(ei-fh)-b(di-fg)+c(dh-eg)$$
To compute the determinate of matrices greater than 3 the method **Laplace Expansion**, also called cofactor expansion. It is found with the rule:
$$det(B)=\sum_{j=1}^n (-1)^{i+j} B_{i,j}M_{i,j}$$
Where $M$ is a new matrix made from removing the rows and columns $i,j$.

## Hadamard Product
The Hadamard product is an element wise multiplication operation. It can be written as:
$$\begin{bmatrix}x_1\\ x_2\end{bmatrix} \odot \begin{bmatrix}y_1\\ y_2\end{bmatrix} = \begin{bmatrix}x_1 \times y_1\\ x_2\times y_1\end{bmatrix}$$

## Trace
The trace is an operation done on the diagonal of a matrices. It is written as:
$$\sum_{i=1}^n A_{i,i}$$
The trace of a matrix can be found as the sum of the [[Matrix Decomposition#Eigenvectors|eigenvalues]].
