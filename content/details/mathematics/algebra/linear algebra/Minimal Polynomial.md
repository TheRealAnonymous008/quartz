* Let $T$ be a [[Linear Transformation|linear operator]] on a vector space $V$. A polynomial $p(t)$ is called a **minimal polynomial** for $T$ if $p(t)$ is a monic polynomial of least positive degree for which 
  $$
  p(T) = T_0
  $$
  Similarly, for matrices this polynomial is the monic polynomial of least degree such that for $A\in M_{n\times n}(F)$ 
  $$
  p(A) = O_n
  $$

* (*Friedberg 7.11*) Let $p(t)$ be a minimal polynomial for a linear operator $T$ on a finite dimensional vector space $V$. 
	* If $g(t)$ is any polynomial for which $g(T)=T_0$, then $p(t)$ [[Factorization of Polynomials|divides]] $g(t)$. In particular $p(t)$ divides the [[Characteristic Polynomial|characteristic polynomial]] of $T$.
	* $p(t)$ is unique.
	* *Intuition*: This immediately follows from applying the division algorithm.
* (*Friedberg 7.12*) Let $T$ be a linear operator on a finite-dimensional vector space $V$ and let $\beta$ be a basis for $V$. Then the minimal polynomial for $T$ is the same as the minimal polynomial for $[T]_\beta$.
	* *Intuition*: Immediately follows from [[Linear Transformation Matrix Isomorphism]]. 

* (*Friedberg 7.12.1*) Let $A\in M_{n\times n}(F)$, the minimal polynomial for $A$ is the same as the minimal polynomial for $L_A$. 

* (*Friedberg 7.13*) Let $T$ be a linear operator on a finite dimensional vector space $V$ and let $p(t)$ be the minimal polynomial for $T$. A scalar $\lambda$ is an [[Matrix Diagonalization|eigenvalue]] of $T$ if and only if $p(\lambda)=0$. 
  
  Hence the characteristic polynomial and the minimal polynomial for $T$ have the same zeros. 

* (*Friedberg 7.13.1*) Let $T$ be a linear operator on a finite dimensional vector space $V$ with minimal polynomial $p(t)$ and characteristic polynomial $f(t)$. Suppose that $f(t)$ factors as 
  $$
  f(t) = (\lambda_1-t)^{m_1} (\lambda_2 -t)^{m_2} \dots (\lambda_k-t)^{m_k}
  $$
  Where $\lambda_1,\dots,\lambda_k$ are distinct eigenvalues of $T$ each with corresponding multiplicities $m_1,\dots,m_k$. 
* (*Friedberg 7.14*) Let $T$ be a linear operator on an $n$-dimensional vector space $V$. If $V$ is a $T$-[[Invariant Subspace|cyclic]] subspace of itself, then the characteristic polynomial $f(t)$ and the minimal polynomial $p(t)$ for $T$ are of the same degree. Hence
  $$
  f(t) = (-1)^n p(t)
  $$
* (*Friedberg 7.15*) Let $T$ be a linear operator on a finite-dimensional vector space $V$. Then $T$ is diagonalizable if and only if the minimal polynomial for $T$ is of the form 
  $$
  p(t) = (t-\lambda_1)(t-\lambda_2)\dots (t-\lambda_kk)
  $$
  Where $\lambda_1,\dots,\lambda_k$ are distinct scalars (eigenvalues)

* (*Friedberg e7.3.12*) Let $T$ be a linear operator on a finite dimensional vector space and suppose that the characteristic polynomial of $T$ splits. Let $\lambda_1,\dots,\lambda_k$ be the distinct eigenvalues of $T$ and for each $i$, let $p_i$ be the order of the largest [[Jordan Canonical Form|Jordan]] block corresponding to $\lambda_i$ in a Jordan canonical form. The minimal polynomial of $T$ is
  $$
  (t -{\lambda_1})^{p_1} (t-\lambda_2)^{p_2} \dots (t-\lambda_k)^{p_k}
  $$

# Annihilators
* Let $T$ be a linear operator on a finite dimensional vector space $V$ and let $x\ne 0$. The polynomial $p(t)$ is called a $T$-**annihilator** of $x$ if  $p(t)$ is monic, of least degree, and 
  $$
  p(T)(x) = 0
  $$
* (*Friedberg e7.3.15*) Let $T$ be a linear operator on a finite dimensional vector space $V$ and let $x\ne 0$.
	* The vector $x$ has a unique $T$-annihilator.
	* The $T$-annihilator of $x$ divides any polynomial $f(t)$ for which $f(T)=T_0$
	* If $[p(t)$ is the $T$-annihilator of $x$ and $W$ is the $T$-cyclic subspace generated by $x$, then $p(t)$ is the minimal polynomial for $T_W$ and
	  $$
	  \dim(W) = \deg(p(t))
	  $$
	* The degree of the $T$-annihilator of $x$ is $1$ if and only if $x$ is an eigenvector of $T$.



# Links
* [[Linear Algebra by Friedberg Insel and Spence]]