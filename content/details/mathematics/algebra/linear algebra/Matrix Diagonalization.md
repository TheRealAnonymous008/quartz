* $T:V\to V$ is said to be **diagonalizable** if there exists an ordered [[Linear Combination|basis]] $\beta$ for $V$ such that $[T]_\beta$ is a diagonal [[Matrix]]. 
  
  $A\in M_{n\times n}(F)$ is said to be **diagonaliziable** if $A$ is similar to a diagonal matrix.

* (*Friedberg 5.3*) Let $T:V\to V$ and $\beta$ a basis for $V$. Then $T$ is diagonalizable if and only if $[T]_\beta$ is a diagonalizable matrix.
  
  It holds because [[Linear Transformation Matrix Isomorphism|linear transformations have corresponding matrices]].
  
  It immediately follows that (*Friedberg 5.3.1*) A matrix $A$ is diagonalizable if and only if $L_A$ is diagonalizable.

* (*Friedberg 5.4*) $T$ is diagonalizable if and only if there exists a basis $\beta=(x_1,\dots,x_n)$ for $B$and scalars $\lambda_1,\dots,\lambda_n$ (not necessarily distinct) such that $T(x_j)=\lambda x_j$ such that
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
* (*Friedberg e5.1.22*) Let $T$ be a linear operator on $V$ over $F$. If $g(t))\in F[x]$ (see notation in [[Polynomial Ring]]) and $x$ is an eigenvector of $T$ corresponding to $\lambda$, then 
  $$
  g(T)(x) = g(\lambda)x
  $$
# Characteristic Polynomial
* If $A\in M_{n\times n}(F)$, the polynomial $\det(A-tI_n)$ in the [[Polynomial Ring|indeterminate]] $t$ is called the **characteristic polynomial of $A$**
  
  Similarly for linear operators, if we have basis $\beta$ then $f(t)$ is called the **characteristic polynomial** defined as
  $$
  f(t) = \det(A-tI)
  $$

* (*Friedberg 5.8*) The characteristic polynomial of $A\in M_{n\times n}(F)$ is a polynomial of degree $n$ with leading coefficient $(-1)^n$
	* (*Friedberg 5.8.1*) Let $A\in M_{n\times n}(F)$ and $f(t)$ be the characteristic polynomial of $A$. Then
		* A scalar $\lambda$ is an eigenvalue of $A$ if and only if $f(\lambda) = 0$
		* $A$ has at most $n$ distinct eigenvalues.
	* (*Friedberg 5.8.2*) The same results in (*Friedberg 5.8.1*) hold for linear operators as well.

* (*Friedberg 5.9*) Let $T$ be a linear operator on a vector space $V$ and $\lambda$ be an eigenvalue of $T$. A vector $x\in V$ is an eigenvector of $T$ corresponding to $\lambda$ if and only if $x\ne 0$ and $x\in N(T-\lambda I)$. 

* (*Friedberg e5.1.12a*) Similar matrices have the same characteristic polynomial.
* (*Friedberg e5.1.14*) $A$ and $A^T$ have the same characteristic polynomial, and hence the same eigenvalues..

# Links
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]] - Ch. 5