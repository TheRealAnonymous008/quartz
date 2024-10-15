* Let $B\in M_{n\times n}(F)$ be a [[Self-Adjoint Matrix|self-adjoint]] matrix. The **Rayleigh quotient** for $x\ne 0$ is defined as the scalar
  $$
  R(x) = \frac{\braket{Bx,x}}{||x||^2} = \frac{x^\ast Bx}{x^\ast x}
  $$

* (*Friedberg 6.36*) For a self adjoint matrix $B$, $\max_{x\ne 0} R(x)$ is the largest [[Matrix Diagonalization|eigenvalue]] of $B$. Similarly, $\min_{x\ne 0} R(x)$ is the smallest eigenvalue of $B$. 
	* *Proof*. Choose an [[Orthogonality and Orthonormality|orthonormal basis]] consisting of eigenvectors of $B$. Represent 
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


# Links
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]]