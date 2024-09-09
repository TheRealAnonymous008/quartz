* (*Friedberg 5.10*) Let $T$ be a linear operator on $V$ and let $\lambda_1,\dots,\lambda_k$ be distinct eigenvalues of $T$. If $x_1,\dots,x_k$ are the corresponding eigenvectors then $\{x_1,x_2,\dots,x_k\}$ are [[Linear Combination|linearly independent]].

* Let $\lambda$ be an eigenvalue of $T$, a linear operator over $V$.  The set
  $$
  E_\lambda = \set{x\in V \mid T(x) = \lambda x} = N(T-\lambda I_V)
  $$
  is called the **Eigenspace** of $T$ corresponding to [[Matrix Diagonalization|eigenvalue]] $\lambda$. 
  
  For a matrix $A$, the eigenspace of $A$ is the eigenspace of $L_A$ .
  
  The eigenspace is a [[Vector Subspace|subspace]] of $V$.

* (*Friedberg 5.12*) Let $T$ be a linear operator on a finite dimensional vector space $V$. If $\lambda$ is an eigenvalue of $T$ with multiplicity $m$, then $1\le \dim(E_\lambda) \le m$. 
* (*Friedberg Lem.5.13*) Let $T$ be a linear operator on $V$ and $\lambda_1,\dots,\lambda_k$ be distinct eigenvalues of $T$. For each $i=1,\dots,k$ let $x_i\in E_{\lambda_i}$. If
  $$
  x_1+\dots +x_k = 0
  $$
  Then $\forall i, x_i=0$
	* *Proof*: The $x_i$'s form a linearly independent set. Therefore, the only non-trivial way to get $0$ is to set all $x_i=0$. 

* (*Friedberg 5.13*) Let $T$ be a linear operator on $V$ and $\lambda_1,\dots,\lambda_k$ be distinct eigenvalues of $T$. Let $S_i$ be a finite linearly independent subset of $E_{\lambda_i}$. Then 
  $$
  S= S_1\cup S_2\cup\dots\cup S_k 
  $$
  is a linearly independent subset of $V$
* (*Friedberg 5.14*) Let $T$ be a linear operator on a finite vector space $V$ such that the  [[Characteristic Polynomial|characteristic polynomial]] of $T$ splits. Let $\lambda_1,\dots,\lambda_k$ be distinct eigenvalues of $T$. Then 
	* $T$ is diagonalizable if and only if the multiplicity of $\lambda_i$ is equal to $\dim(E_i)$ for all $i$.
	* If $T$ is diagonalizable and $S_i$ is a basis for $E_{\lambda_i}$ then 
	  $$
	  \beta = S_1\cup \dots \cup S_k
	  $$
	  forms a basis for $V$ called the **eigenbasis**. It contains eigenvectors of $T$.


* (*Friedberg 5.16*) Let $T$ be a linear operator on a finite dimensional vector space $V$. $T$ is diagonalizable if and only if $V$ is the [[Vector Sum and Direct Sum|direct sum]] of the eigenspaces of $T$.
	* Suppose $T$ is diagonalizable.  Each eigenspace $E_{\lambda_i}$ is $T$-[[Invariant Subspace|invariant]] with characteristic polynomial $(\lambda_i-t)$. Which means by (*Friedberg 5.29*) The characteristic polynomial of $T$ is the product
	  $$
	  f(t) = (\lambda_1-t)^{m_1}\dots (\lambda_k-t)^{m_k}
	  $$
	  Where $m_i$ is the algebraic multiplicity of each eigenvalue, equal to the dimension of the corresponding eigenspace.

# [[Spectral Theorem]]

# Links
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]] - Ch. 5