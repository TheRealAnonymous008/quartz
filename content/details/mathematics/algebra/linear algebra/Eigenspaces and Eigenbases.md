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

# Spectral Theorem
* (*Friedberg 6.24*) **Spectral Theorem**. Suppose that $T$ is a linear operator on a finite dimensional [[Inner Product Space|inner product space]] $V$ over $F$. Assume that $T$ is [[Normal Matrix|normal]] if $F=\mathbb{C}$ and $T$ is [[Self-Adjoint Matrix|self-adjoint]] if $F=\mathbb{R}$. 
  
  If $\lambda_1,\dots,\lambda_k$ are the distinct eigenvalues of $T$, let $W_i$ be the eigenspace of $T$ corresponding to eigenvalue $\lambda_i$  and let $T_i$ be the [[Orthogonality and Orthonormality|orthogonal projection]] on $W_i$. Then 
	* $V= W_1\oplus \dots \oplus W_k$
	* If $W_i'$ denotes the [[Vector Sum and Direct Sum|direct sum]] of the subspaces of $W_j$, $j\ne i$, then $W_i^\perp = W_i'$ 
	* $T_iT_j = \delta_{ij}T_i$ for $1\le i,j\le k$
	* $I=T_1 + \dots + T_k$. This decomposition is called the **resolution of the identity operator induced by $T$**
	* $T=\lambda_1 T_1 + \dots + \lambda_k T_k$.  The eigenvalues are called the **spectrum** of $T$. The decomposition of this sum is called the **spectral decomposition**. 
	* *The spectral decomposition is unique*.
	* If $\beta$ is the union of orthonormal bases of the $W_i$s and $m_i=\dim(W_i)$ then
	  $$
	  [T]_\beta = 
	  \begin{bmatrix}
	  \lambda_1 I_{m_1} & O & \cdots & O \\
	  O  & \lambda_2 I_{m_2} & \cdots & O \\
	  \vdots & \vdots & \ddots & \vdots \\
	  O & O & \cdots & \lambda_k I_{m_k}
	  \end{bmatrix}
	  $$
* (*Friedberg 6.24.1*) If $F=\mathbb{C}$ then $T$ is normal if and only if $T^\ast = g(T)$ for some polynomial $G$. 
* (*Friedberg 6.24.2*) If $F=\mathbb{C}$, then $T$ is [[Unitary and Orthogonal Operators|unitary]] if and only if $T$ is normal and $|\lambda|=1$ for every eigenvalue $\lambda$ of $T$
* (*Friedberg 6.24.3*) If $F=\mathbb{C}$ and $T$ is normal, then $T$ is self-adjoint if and only if every eigenvalue of $T$ is real.
* (*Friedberg 6.24.4*) Let $T$ have a spectral decomposition of $T=\lambda_1T_1 + \dots + \lambda_k T_k$. Then each $T_j$ is a polynomial in $T$
* (*Friedberg e6.6.7*) Let $T$ be a normal operator and $U$ a linear operator on a finite dimensional complex inner product space $V$. Let $T=\lambda_1 T_1 + \dots + \lambda_k T_k$ be a spectral decomposition of $T$.
	* If $g$ is a polynomial then 
	  $$
	  g(T) = \sum_{i=1}^k g(\lambda_i) T_i
	  $$
	* If $T^n = T_0$ for some $n$ then $T=T_0$
	* $U$ commutes with $T$ if and only if $U$ commutes with each $T_i$
	* If $U$ is normal and commutes with $T$ then if we have $\mu_1,\dots,\mu_r$ as (not necessarily distinct) eigenvalues of $U$, 
	  $$
	  U =\mu_1 T_1 + \dots + \mu_r T_r
	  $$
	* There exists a normal operator $U$ on $V$ such that $U^2 = T$
	* $T$ is [[Matrix Inversion|invertible]] if $\lambda_i\ne 0$ 
	* $T$ is a projection if and only if every eigenvalue of $T$ is $1$ or $0$.
	* $T=-T^\ast$ if and only if every $\lambda_i$ is an imaginary number. 
# Links
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]] - Ch. 5