* Let $T$ be a [[Self-Adjoint Matrix|self-adjoint]] operator on an $n$-dimensional [[Inner Product Space|inner product space]] $V$ and $A=[T]_\beta$  where $\beta$ is an [[Orthogonality and Orthonormality|orthonormal]] for $V$. Then $T$ is **positive definite** if $\braket{T(x),x}>0$ $\forall x\ne 0$. 
  
  $T$ is **positive semidefinite** if $\forall x \braket{T(x),x}\ge 0$ 
  
  A similar definition applies for matrices.
  
	* In other words, *A positive definite matrix is one that defines an inner product*. In particular we have the [[Quadratic Form]]
	  
	  $$
	  \forall x \ne 0,  x^T Ax > 0 
	  $$
	* For positive semidefinite matrices, the criteria is weakened to be 
	  $$
	  \forall x, x^TA x \ge 0
	  $$


* (*Friedberg e6.4.13a*) $T$ is positive definite if and only if all the [[Matrix Diagonalization|eigenvalues]] are positive
  
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

# Links
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]]
