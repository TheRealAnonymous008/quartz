* $T:V\to V$ is said to be **diagonalizable** if there exists an ordered [[Linear Combination|basis]] $\beta$ for $V$ such that $[T]_\beta$ is a diagonal [[Matrix]]. 
  
  $A\in M_{n\times n}(F)$ is said to be **diagonalizable** if $A$ is similar to a diagonal matrix.

* (*Friedberg 5.3*) Let $T:V\to V$ and $\beta$ a basis for $V$. Then $T$ is diagonalizable if and only if $[T]_\beta$ is a diagonalizable matrix.
  
  It holds because [[Linear Transformation Matrix Isomorphism|linear transformations have corresponding matrices]].
  
  It immediately follows that (*Friedberg 5.3.1*) A matrix $A$ is diagonalizable if and only if $L_A$ is diagonalizable.

* (*Friedberg 5.4*) $T$ is diagonalizable if and only if there exists a basis $\beta=(x_1,\dots,x_n)$ for $B$ and scalars $\lambda_1,\dots,\lambda_n$ (not necessarily distinct) such that $T(x_j)=\lambda x_j$ such that
  $$
  [T]_\beta = 
  \begin{bmatrix}
  \lambda_1 & 0 & \dots & 0 \\
  0 & \lambda_2 & \dots & 0 \\
  \vdots & \vdots  & \ddots & \vdots \\
  0 & 0 & \dots & \lambda_n
  \end{bmatrix}
  $$

* Let $T$ be a linear operator on $V$. A nonzero element $x\in V$ is called an **eigenvector** of  $T$ if there exists a scalar called the **eigenvalue** $\lambda$ such that 
  $$
  T(x) = \lambda x
  $$

* (*Friedberg 5.7*) A scalar $\lambda\in F$ is an eigenvalue of $T$ if and only if
  $$
  \det(T-\lambda I) = 0
  $$
  See [[Determinant]]
	* (*Friedberg 5.7.1*) Let $A\in M_{n\times n}(F)$. Then $\lambda\in F$ is an eigenvalue of $A$ if and only if $\det(A-\lambda I)=0$
	* (*Friedberg 5.7.2*) Let $T$ be a linear operator on $V$ and $\beta$ a basis for $V$. Then $\lambda$ is an eigenvalue of $T$ if $\lambda$ is an eigenvalue of $[T]_\beta$

* (*Friedberg e5.1.15*) Let $T$ be a linear operator on $V$ and $x$ be an eigenvector of $T$ corresponding to eigenvalue $\lambda$. For any positive integer $m$, $x$ is an eigenvector of $T^m$ corresponding to eigenvalue $\lambda^m$

* (*Friedberg 5.10.1*) Let $T$ be a linear operator on $V$, where $\dim(V)=n$ If $T$ has $n$ distinct eigenvalues then $T$ is diagonalizable

* A linear operator $T$ is diagonalizable if the following hold.
	* The corresponding characteristic polynomial of $T$ splits.
	* The multiplicity of $\lambda$ equals $n-\text{rank}(T-\lambda I)$ for each eigenvalue $\lambda$ of $T$.
* (*Friedberg e7.1.7e*) $T$ is diagonalizable if and only if for each eigenvalue $\lambda$ 
  $$
  \text{rank}(T-\lambda I) = \text{rank}((T-\lambda I)^2 )
  $$


* (*Friedberg e5.2.11*) If $T$ is invertible, then $T$ is diagonalizable if and only if $T^{-1}$ is diagonalizable.
* (*Friedberg e5.2.12*) Let $A\in M_{n\times n}(F)$. Then $A$ is diagonalizable if and only if $A^T$ is diagonalizable.

# Simultaneous Diagonalizability
* Two linear operators $T,U$ on the same finite dimensional vector space $V$ are called **simultaneously diagonalizable** if there exists a basis $\beta$ for $V$ such that both $[T]_\beta$ and $[U]_\beta$ are  diagonal matrices.
  
  Similarly, $A,B\in M_{n\times n}(F)$ are simultaneously diagonalizable if there exists an invertible matrix $Q$ such that both $Q^{-1}AQ$ and $Q^{-1}BQ$ are diagonal.
* (*Friedberg e5.2.16*) If $T$ and $U$ are simultaneously diagonalizable then
  $$
  TU = UT
  $$
  (*Friedberg e5.4.25*) If $T$ and $U$ are diagonalizable linear operators such that $UT=TU$, then $T$ and $U$ are simultaneously diagonalizable. *
* (*Friedberg e5.2.17*) $T$ and $T^m$ are simultaneously diagonalizable for any $m\in \mathbb{Z}^+$.
* (*Friedberg e6.4.14*) Let $V$ be a finite dimensional real inner product space and $U,T$ are [[Self-Adjoint Matrix|self-adjoint]] operators on $V$ such that $UT=TU$. There exists an orthonormal basis for $V$ consisting of vectors that are eigenvectors of both $U$ and $T$.
* (*Friedberg e6.6.10*) If $U,T$ are normal operators such that $UT=TU$, there exists an [[Orthogonality and Orthonormality|orthonormal basis]] for $V$ consisting of vectors that are eigenvectors of both $T$ and $U$.


# Topics
* [[Characteristic Polynomial]]
* [[Eigenspaces and Eigenbases]]
* [[Jordan Canonical Form]]
* [[Rational Canonical Form]]

# Links
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]] - Ch. 5