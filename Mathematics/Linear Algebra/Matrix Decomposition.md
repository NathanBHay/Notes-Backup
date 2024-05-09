Matrix decomposition is branch of [[Linear Algebra|linear algebra]] that deals with modifying matrices as to solve particular problems. Usually is reduces a matrix to the required parts to solve the problem leading to less computational cost.

# Eigenvectors
Eigenvectors are a type of vector which isn't rotated or sheared which during a linear [[Linear Algebra#Linear Transformations|transformations]]. This means that after a matrix $A$ is applied to $\vec x$ there exists vectors which are only stretched but stay on the same line. These vectors have an **eigenvalue** which represents the factor it was stretched or squished by. From this we know that every matrix $A$ can be represented as the eigenvector multiplied by a eigenvalue. 
$$A \vec x = \lambda \vec x$$
Where $\lambda$ is the scalar eigenvalue defined as $\lambda \in \mathbb{R}^{n \times n}$. Simply this equation says that matrix-vector multiplication is the same as scaling the vector. This eigenvalue is found through substituting an [[Linear Algebra#Identity Matrix|identity matrix]] into the right side $\vec x$, and from there solving for the eigenvalue by finding the determinant: 
$$(A-\lambda I)\vec{x}$$
From the use of eigenvalues we can further find the eigenvectors. Some linear transformations lack eigenvectors.

To represent a matrix you can decompose a matrix to be a matrix of its eigenvectors $S$ and a identity matrix of its eigenvalues $\Lambda$. This allows us to find the decomposition:
$$A=S\Lambda S^{-1}$$
From this equation we can find an approach to solving matrix exponentiation. This uses the rule: 
$$A^n=S(\Lambda^n)S^{-1}$$

# Lower-Upper Decomposition
Lower-upper (LU) decomposition or factorisation factors a matrix as the product of a lower triangular matrix and an upper triangular matrix. This can be visualised as:
$$\begin{bmatrix}a_{1,1} & a_{1,2} & a_{1,3} \\ a_{2,1} & a_{2,2} & a_{2,3}\\ a_{3,1} & a_{3,2} & a_{3,3} \end{bmatrix} = \begin{bmatrix}\ell_{1,1} & \ell_{1,2} & \ell_{1,3} \\ 0 & \ell_{2,2} & \ell_{2,3}\\ 0 & 0 & \ell_{3,3} \end{bmatrix}\begin{bmatrix} \mathscr{u}_{1,1} & 0 & 0 \\ \mathscr{u}_{2,1} & \mathscr{u}_{2,2} & 0\\ \mathscr{u}_{3,1} & \mathscr{u}_{3,2} & \mathscr{u}_{3,3} \end{bmatrix}$$
This matrix can also be represented as $A=\ell \mathscr{u}$.

# QR Decomposition
QR decomposition or QR factorisation is a method of solving linear equations easier. It is founds as a orthogonal matrix and an upper triangular matrix. The equation which represents this is $A=QR$ .

# Cholesky
Cholesky Decomposition offers a square-root equivalent operation for symmetric positive definite matrices. Simply it only works on square symmetric matrices where all eigenvalues are greater than zero. It also provides a faster way to solve linear equations. It is found as a lower triangular matrix and its conjugate transpose.

# Singular Value Decomposition
Single Value Decomposition (SVD) generalises eigen decomposition of square matrices to work on non-square matrices. It can be applied onto all matrices despite the dimensions. It takes the form $A=U\Sigma V^T$ where $\Sigma$ is a rectangular diagonal matrix that transforms the scale of the matrix, $U$ is a complex unitary matrix that changes the codomain that can be represented as a rotation, and $V^T$ is a square complex matrix that performs a basis change in the domain aligning to the canonical basis. On symmetric matrices the SVD is found to be the same as the eigen decomposition. Another interpretation can be represented as:
$$M=\sum_{i=1}^r u_i\sigma_iv^*_i$$
As SVD is the product of three rank one matrices it allows a low rank matrix approximation. This approximation follows the equation:
$$A \approx u_k\sigma_kv^*_k$$
Where $k$ is the highest rank it approximates. Where $\sigma_k$ is the set of first $k$ rows and columns corresponding to the largest value of $k$. $u_k$ is equal to the first columns of $k$, and $v_k$ is the first rows of k.
