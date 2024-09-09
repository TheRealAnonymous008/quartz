* Let $V$ be an [[Inner Product Space|inner product space]] and let $T$ be a linear operator on $V$. $T$ is **self-adjoint** if 
  $$
  T^\ast = T
  $$
  Similarly, a matrix $A\in M_{n\times n}(F)$ is self-[[Matrix Conjugate and Adjoint|adjoint]] if 
  $$
  A^\ast = A
  $$

* An important example of such a matrix is a **symmetric matrix** where $F=\mathbb{R}$. 

* (*Friedberg Lem.6.17.1*) Let $T$ be a self-adjoint operator on a finite-dimensional inner product space $V$. Then
	* Every [[Matrix Diagonalization|eigenvalue]] of $T$ is real.
	* The [[Characteristic Polynomial|character polynomial]]l of $T$ splits.
* (*Friedberg 6.17*) Let $T$ be a linear operator on a finite dimensional real inner product space $V$. Then $T$ is adjoint if and only if there exists an [[Orthogonality and Orthonormality|orthonormal]] basis $\beta$ of eigenvectors of $T$. 

* Let $A\in M_{n\times n}(\mathbb{R})$. $A$ is a **Gramian matrix** if there exists a real square matrix $B$ such that
  
  $$
  A = B^TB
  $$
  

* (*Friedberg e6.4.12*) $A$ is a Gramian matrix If and only if $A$ is symmetric and all its eigenvalues are nonnegative. 

* Let $T$ be a self-adjoint operator on an $n$-dimensional inner product space $V$ and $A=[T]_\beta$  where $\beta$ is an orthonormal basis for $V$. Then $T$ is **positive definite** if $\braket{T(x),x}>0$ $\forall x\ne 0$. 
  
  $T$ is **positive semidefinite** if $\forall x \braket{T(x),x}\ge 0$ 
	* (*Friedberg e6.4.13a*) $T$ is positive definite if and only if all the eigenvalues are positive
	  
	  $T$ is positive semidefinite if and only if all the eigenvalues are nonnegative.
	* (*Friedberg e6.4.13b*) $T$ is positive definite if and only if $L_A$ is also.
	  
	  $T$ is positive semidefinite if and only if $L_A$ is also.
	* (*Friedberg e6.4.13c*) $T$ is positive definite if and only if
	  $$
	  \sum_{i,j} A_{ij}a_i\overline{a}_j > 0
	  $$
	  For all nonzero $n$-tuples $(a_1,\dots,a_n)$. 
	* (*Friedberg e6.4.13d*) $T$ is positive semidefinite if and only if $A$ is a Gramian matrix.

* (*Friedberg e6.4.16*) Let $T$ and $U$ be positive definite on an inner product space $V$.
	* $T+U$ is positive definite.
	* If $c>0$, then $cT$ is positive definite.
	* $T^{-1}$ is positive definite.


* (*Friedberg Lem.6.18*) Let $V$ be a finite dimensional inner product space and let $U$ be a self adjoint operator on $V$. If $\braket{x,U(x)}=0$ $\forall x\in V$ then $U=T_0$.

# Rayleigh Conditioning
* Let $B\in M_{n\times n}(F)$ be a self-adjoint matrix. The **Rayleigh quotient** for $x\ne 0$ is defined as the scalar
  $$
  R(x) = \frac{\braket{Bx,x}}{||x||^2}
  $$

* (*Friedberg 6.36*) For a self adjoint matrix $B$, $\max_{x\ne 0} R(x)$ is the largest eigenvalue of $B$. Similarly, $\min_{x\ne 0} R(x)$ is the smallest eigenvalue of $B$. 
	* *Proof*. Choose an orthonormal basis consisting of eigenvectors of $B$. Represent 
	  $$
	  x= \sum_{i=1}^n a_ix_i
	  $$
	  Assume that the eigenvalues are sorted  $\lambda_1\le \dots\le \lambda_n$. 
	  
	  Computing $R(x)$, we have
	  $$
	  R(x)=\frac{\braket{\sum_{i=1}^n a_i\lambda_ix_i, \sum_{i=1}^n a_ix_i}}{||x||^2} =\frac{\sum_{i=1}^n \lambda_i |a_i|^2}{||x||^2}
	  $$
	  We can clearly bound this as 
	  $$
	  \lambda_1\le R(x) \le \lambda_n
	  $$


# Link
* [[Linear Algebra by Friedberg Insel and Spence]]