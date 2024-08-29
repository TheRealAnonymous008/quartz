* If $A\in M_{n\times n}(F)$, the [[Determinant|polynomial]] $\det(A-tI_n)$ in the [[Polynomial Ring|indeterminate]] $t$ is called the **characteristic polynomial of $A$**
  
  Similarly for linear operators, if we have basis $\beta$ then $f(t)$ is called the **characteristic polynomial** defined as
  $$
  f(t) = \det(A-tI)
  $$

* (*Friedberg 5.8*) The characteristic polynomial of $A\in M_{n\times n}(F)$ is a polynomial of degree $n$ with leading coefficient $(-1)^n$
	* (*Friedberg 5.8.1*) Let $A\in M_{n\times n}(F)$ and $f(t)$ be the characteristic polynomial of $A$. Then
		* A scalar $\lambda$ is an [[Matrix Diagonalization|eigenvalue]] of $A$ if and only if $f(\lambda) = 0$
		* $A$ has at most $n$ distinct eigenvalues.
	* (*Friedberg 5.8.2*) The same results in (*Friedberg 5.8.1*) hold for linear operators as well.

* (*Friedberg 5.9*) Let $T$ be a linear operator on a vector space $V$ and $\lambda$ be an eigenvalue of $T$. A vector $x\in V$ is an eigenvector of $T$ corresponding to $\lambda$ if and only if $x\ne 0$ and $x\in N(T-\lambda I)$. 

* (*Friedberg e5.1.12a*) Similar matrices have the same characteristic polynomial.
* (*Friedberg e5.1.14*) $A$ and $A^T$ have the same characteristic polynomial, and hence the same eigenvalues.

* (*Friedberg e5.1.22*) Let $T$ be a linear operator on $V$ over $F$. If $g(t)\in F[x]$ (see notation in [[Polynomial Ring]]) and $x$ is an eigenvector of $T$ corresponding to $\lambda$, then 
  $$
  g(T)(x) = g(\lambda)x
  $$
* (*Friedberg 5.11*) The characteristic polynomial of any diagonalizable linear operator can be factored into linear factors. We say that the characteristic polynomial in this case **splits**.
 * The **algebraic multiplicity** of an eigenvalue $\lambda$ is the largest $k\in \mathbb{Z}^+$ such that $(t-\lambda)^k$ is a factor of the characteristic polynomial $f(t)$
# Links
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]]