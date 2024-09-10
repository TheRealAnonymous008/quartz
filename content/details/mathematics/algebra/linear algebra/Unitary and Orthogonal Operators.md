* Let $V$ be an [[Inner Product Space|inner product space]] over $F$ and let $T$ be a [[Linear Transformation|linear operator]] on $V$. If 
  $$
  ||T(x)|| = ||x||
  $$
  For all $x\in V$. 
  
  If $F=\mathbb{C}$ we call $T$ a **unitary operator**.
  If $F=\mathbb{R}$ we call $T$ an **orthogonal operator**.
  
  Similarly for matrix $A\in M_{n\times n}(F)$. If 
  $$
  AA^\ast =A^\ast A =I
  $$
  If $F=\mathbb{C}$, we call $A$ a **unitary matrix**
  If $F=\mathbb{R}$, we call $A$ an **orthogonal matrix** 

* In other words *Unitary operators preserve the lengths of vectors in the vector space*.

* (*Friedberg 6.18*) Let $V$ be a finite dimensional inner product space and let $T$ be a linear operator on $V$. Then the following are equivalent
	* $TT^\ast=T^\ast T=I$ (see [[Normal Matrix]])
	* $\braket{T(x),T(y)}=\braket{x,y}$ $\forall x, y\in V$.
	* If $\beta$ is an [[Orthogonality and Orthonormality|orthonormal basis]] for $V$, then $T(\beta)$ is an orthonormal basis for $V$.
	* There exists an orthonormal basis $\beta$ for $V$ such that $T(\beta)$ is an orthonormal basis for $V$.
	* $||T(x)|| = ||x||$ for all $x\in V$.

* (*Friedberg 6.18.1*) Let $T$ be a linear operator on a finite-dimensional real inner product space $V$. $V$ has an orthonormal basis of [[Matrix Diagonalization|eigenvectors]] of $T$ with corresponding eigenvalues of absolute value $1$ if and only if $T$ is both [[Self-Adjoint Matrix|self-adjoint]] and [[Orthogonality and Orthonormality|orthogonal]]. 
  
  Another way to say this is that *all eigenvalues of $T$ lie along the unit circle* 
  $$
  \text{spec}(T) \subset \set{x \mid |x| = 1}
  $$


* (*Friedberg 6.18.2*) Let $T$ be a linear operator on a finite dimensional complex inner product space. Then $V$ has an orthonormal basis of eigenvectors of $T$ with corresponding eigenvalues of absolute value $1$ if and only if $T$ is unitary.
	* If $B$ is orthogonal / unitary, then 
	  $$
	  \det(B) =\pm 1
	  $$

* $A$ and $B$ are **unitarily / orthogonally equivalent** if and only if there exists a unitary / orthogonal matrix $P$ such that
  $$
  A = P^\ast BP
  $$
  This is another form of [[Vector Coordinate System|similarity]] between matrices if we take the fact that
  $$
  P^\ast = P^{-1}
  $$
* (*Friedberg 6.19*) Let $A\in M_{n\times n}(\mathbb{C})$. Then $A$ is normal if and only if $A$ is unitarily equivalent to a diagonal matrix.
* (*Friedberg 6.20*) Let $A\in M_{n\times n}(\mathbb{R})$. Then $A$ is symmetric if and only if $A$ is orthogonally equivalent to a real diagonal matrix. 

* (*Friedberg 6.21*) **Schur's Theorem (Matrix Form)**. Let $A\in M_{n\times n}(F)$ and whose [[Characteristic Polynomial|characteristic polynomial]] splits over $F$
	* If $F=\mathbb{C}$ then $A$ is a unitarily equivalent to a complex upper triangular matrix.
	* If $F=\mathbb{R}$ then $A$ is an orthogonally equivalent to a real upper triangular matrix.

* (*Friedberg e6.5.10*) Let $A$ be a complex normal or real symmetric $n\times n$ matrix with  $\lambda_1,\dots,\lambda_n\in \text{spec}(A)$. We have that
  $$
  \begin{split}
  \text{tr}(A) &= \sum_{i=1}^n \lambda_i \\
  \text{tr}(A^\ast A) &= \sum_{i=1}^n |\lambda_i|^2
  \end{split}
  $$
	* *Proof*: $A$ is unitarily / orthogonally equivalent to a diagonal matrix, that is $A=P^\ast D P$. The diagonal matrix has the eigenvalues as its entries. We have by virtue of $P$ having the same shape as $D$
	  $$
	  \text{tr}(A) = \text{tr}(P^\ast DP) = \text{tr}(PP^\ast D) = \text{tr}(D) = \sum_{i=1}^n \lambda_i
	  $$
	  Similarly, 
	  $$
	  \text{tr}(A^\ast A) = \text{tr}(P^\ast DPP^\ast DP) = \text{tr} (P^\ast D^2 P) = \sum_{i=1}^n |\lambda_i|^2 
	  $$
* (*Friedberg e6.5.12*) Let $A$ be an $n\times n$ real symmetric or complex normal matrix. Let $\lambda_1,\dots,\lambda_n \in \text{spec}(A)$. We have the [[Determinant|determinant]]
  $$
  \det(A) = \prod_{i=1}^n \lambda_i 
  $$
	* *Proof*: $A$ is unitarily / orthogonally equivalent to a diagonal matrix, that is $A=P^\ast D P$. The diagonal matrix has the eigenvalues as its entries. We have
	  $$
	  \det(A) = \det(P^\ast DP) = \det(P^\ast)\det(D)\det(P) = \det(D) = \prod_{i=1}^n \lambda_i
	  $$
# Links
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]]