# Factorizations
## LU Decomposition
* The **LU Decomposition** factors a matrix as the product of a lower triangular matrix $L$ and an upper triangular matrix $U$. 
  $$
  A =LU
  $$
* We use the LU decomposition in solving linear equations. In particular, it is a matrix form of [[Elementary Matrix Operations|Gaussian Elimination]]. 
	* We do this as follows. Start with $A$.  The goal is to use Row Elementary Operations (using Elementary Matrices) to obtain $U$.
	* The Elementary Matrices we use to do this are lower triangular matrices. 

* Not all matrices have a LU decomposition. However, we can obtain a proper one if we allow for either partial pivoting or full pivoting.
  
  **LU Decomposition with Partial Pivoting** involves using a permutation matrix $P$
  $$
  PA = LU
  $$
  **LU Decomposition with Full Pivoting** involves both row and column permutations. We have permutation matrices $P$ and $Q$
  $$
  PAQ = LU
  $$

* We can also obtain a **Lower-Diagonal-Upper (LDU)** decomposition of the form
  $$
  A= LDU
  $$
  Where $D$ is diagonal, and $L$ and $U$ are lower and upper triangular matrices with the diagonal entries set to $1$. 

* Consider the system $Ax=b$ expressed as $LUx = b$. 
	* The vector $Ly=b$ is easily solved using forward substitution. Start with the first entry, substitute the corresponding value in $b$ and repeat   
	* Observe that $Ux=y$ can be solved easily using back substitution. Start with the last entry, substitute the value in $b$ and repeat. 

## QR Decomposition
* The **QR Decomposition** factors a matrix into the product of  orthonormal matrix $Q$ and upper triangular matrix $R$
  $$A = QR
  $$
* One way to compute this is to use the [[Orthogonality and Orthonormality|Gram-Schmidt process]]. Let $e_i$ be the $i$-th basis vector obtained from the Gram-Schmidt process and $a_i$ the $i$-th column. Then
  $$
  \begin{split}
  Q &= \begin{bmatrix}
  e_1 & \dots & e_n  
  \end{bmatrix} \\
  
  R &= \begin{bmatrix}
  \braket{e_1, a_1} & \braket{e_1, a_2} & \dots  & \braket{e_1, a_n} \\ 
  0 & \braket{e_2, a_2} & \dots & \braket{e_2, a_n} \\
  \vdots  & \vdots & \ddots & \vdots  \\
  0 & 0 & \dots & \braket{e_n, a_n}
  \end{bmatrix}
  \end{split}
  $$
	* Note however, that the Gram-Scmidt process is numerically unstable. 


* The rationale for this is that a solution to the system $Ax=b$ written as $QRx=b$, we can solve this as follows
	* Solve $Qy =b$ by observing that $y=Q^Tb$.
	* Solve $Rx=y$ using back substitution.

# Eigenvalues 
## Power Method
* The **Power Method** allows us to find the dominant eigenvector and eigenvalue of a matrix, that is, the eigenvalue with the largest absolute value and its associated normalized eigenvector.
* Suppose that the matrix is [[Matrix Diagonalization|diagonalizable]] with eigenbasis $v_1,\dots,v_n$.  First, it can be shown that if $x=\sum_{i} c_iv_i$, that 
  $$
  \begin{split}
  A^kx &= \sum c_i\lambda_i^k v_i \\ 
  A^kx &= \lambda_1^k \sum c_i\left(\frac{\lambda_i}{\lambda_1}\right)^k v_i
  \end{split}
  $$
  
  Where $\lambda_1$ is the unique largest eigenvalue. 
  
  Consider what happens at the [[Matrix Limit|limit]]. We have
  $$
  \lim_{k \to \infty} \frac{A^kx}{\lambda_1} = c_1
  $$


* The algorithm proceeds as follows.
	* Start with an approximation $b_0$ for the dominant eigenvector.
	* Proceed by computing
	  $$
	  b_{k+1} = \frac{Ab_k}{||Ab_k||}
	  $$
* To get the associated eigenvalue, use the [[Rayleigh Quotient]] computed as follows
  $$
  \mu_k = \frac{b_k^\ast Ab_k}{b_k^\ast b_k}
  $$

# Miscellaneous
* (*Sullivan 4.3*) If $Ax=b$ is an overdetermined system (that is, $A$ has more rows than columns), then we can opt to instead solve the system
  $$
  (A^TA)x = A^Tb
  $$
  The answer to this system is interpreted as the vector $x$ which solves exactly for the projection of $b$ onto the column space of $A$. 
  
  We call this the **Normal Equation**.

# Links
* [[Numerical Methods -- An Inquiry Based Approach with Python by Sullivan]]
* [[Linear Algebra]]
	* [[Matrix]]