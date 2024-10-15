* Let $V$ be an [[Inner Product Space|inner product space]] and let $T$ be a linear operator on $V$. $T$ is **self-adjoint** if 
  $$
  T^\ast = T
  $$
  Similarly, a matrix $A\in M_{n\times n}(F)$ is self-[[Matrix Conjugate and Adjoint|adjoint]] if 
  $$
  A^\ast = A
  $$
  We also call these matrices **Hermitian Matrices**

* An important example of such a matrix is a **symmetric matrix** where $F=\mathbb{R}$. 

* (*Friedberg Lem.6.17.1*) Let $T$ be a self-adjoint operator on a finite-dimensional inner product space $V$. Then
	* *Every [[Matrix Diagonalization|eigenvalue]] of $T$ is real.* That is 
	  $$
	  \text{spec}(T) \subset \mathbb{R}
	  $$
	* The [[Characteristic Polynomial|characteristic polynomial]] of $T$ splits.

* (*Friedberg 6.17*) Let $T$ be a linear operator on a finite dimensional real inner product space $V$. Then $T$ is self-adjoint if and only if there exists an [[Orthogonality and Orthonormality|orthonormal]] basis $\beta$ of eigenvectors of $T$. 

* A similar class of matrices is the **skew-adjoint** matrices. Defined such that
  $$
  T= -T^\ast 
  $$
	* An important example of such a matrix is a **skew-symmetric matrix** where $F=\mathbb{R}$
	* Let $T$ be a skew-adjoint operator on a finite-dimensional inner product space $V$ on $F=\mathbb{C}$. Then
		* *Every eigenvalue is pure imaginary*. That is
		  $$
		  \text{spec}(T) \subset \mathbb{R} i 
		  $$
		* The characteristic polynomial splits.

* Let $A\in M_{n\times n}(\mathbb{R})$. $A$ is a **Gramian matrix** if there exists a real square matrix $B$ such that
  
  $$
  A = B^TB
  $$
  

* (*Friedberg e6.4.12*) $A$ is a Gramian matrix If and only if $A$ is symmetric and all its eigenvalues are nonnegative. 

* (*Friedberg Lem.6.18*) Let $V$ be a finite dimensional inner product space and let $U$ be a self adjoint operator on $V$. If $\braket{x,U(x)}=0$ $\forall x\in V$ then $U=T_0$.



# Link
* [[Linear Algebra by Friedberg Insel and Spence]]