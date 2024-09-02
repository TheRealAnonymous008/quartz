* (*Friedberg Lem.6.4.1*) Let $T$ be a [[Linear Transformation|linear operator]] on a finite dimensional [[Inner Product Space|inner product space]] $V$. If $T$ has an [[Matrix Diagonalization|eigenvector]], then so does $T^\ast$. 
	* *Intuition*: If $\lambda$ is eigenvalue of $T$ then $\overline\lambda$ is an eigenvalue of $T^\ast$. 
* (*Friedberg 6.14*) **Schur's Theorem** Let $T$ be a linear operator on a finite dimensional inner product space $V$. Suppose that the [[Characteristic Polynomial|characteristic polynomial]] of $T$ splits. Then there exists an orthonormal basis $\beta$ such that the matrix $[T]_\beta$ is upper triangular. 
	* *Intuition*: $T^\ast$ will have an eigenvalue  since $T$ splits. Let $x$ be the corresponding eigenvalue. Consider $W=\text{span}(\set{z})$. It can be shown that $W^\perp$ is $T$-[[Invariant Subspace|invariant]] and therefore (*Friedberg 5.26*) applies to the characteristic polynomial of $T^\ast$. Induction can then be used to prove the rest of the details.
* Let $V$ be an inner product space and $T$ a linear operator on $V$. $T$ is **normal** if 
  $$
  TT^\ast = T^\ast T
  $$
  Similarly $A\in M_{n\times n}(F)$ is normal if
  $$
  AA^\ast = A^\ast A
  $$
* (*Friedberg 6.15*) Let $V$ be an inner product space, and let $T$ be a normal operator on $V$. Then
	* $||T(x)||=||T^\ast(x)||$ for all $x\in V$
	* $T-cI$ is normal for every $c\in F$
	* If $x$ is an [[Matrix Diagonalization|eigenvector]] of $T$ then $x$ is also an eigenvector of $T^\ast$. In fact
	  $$
	  T(x) = \lambda x \implies T^\ast (x) =\overline{\lambda} x
	  $$
	* If $\lambda_1$ and $\lambda_2$ are distinct eigenvalues of $T$ with corresponding eigenvectors $x_1$ and $x_2$. Then $x_1$ and $x_2$ are orthogonal.
* (*Friedberg 6.16*) Let $T$ be a linear operator on a finite-dimensional complex inner product space $V$. Then $T$ is normal if and only if there exists an [[Orthogonality and Orthonormality|orthonormal]] basis of eigenvectors of $T$.

# Links
* [[Linear Algebra by Friedberg Insel and Spence]]
* [[Matrix Conjugate and Adjoint]]