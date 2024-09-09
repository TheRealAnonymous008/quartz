* *The Spectral Theorem states that for any normal (in $F=\mathbb{C}$) or self-adjoint (in $F=\mathbb{R}$) linear operator, there exists a simpler canonical form*. The canonical form is obtained by decomposing the linear operator as a series of projections onto orthogonal eigenspaces. 

* (*Friedberg 6.24*) **Spectral Theorem**. Suppose that $T$ is a linear operator on a finite dimensional [[Inner Product Space|inner product space]] $V$ over $F$. Assume that $T$ is [[Normal Matrix|normal]] if $F=\mathbb{C}$ and $T$ is [[Self-Adjoint Matrix|self-adjoint]] if $F=\mathbb{R}$. 
  
  If $\lambda_1,\dots,\lambda_k$ are the distinct [[Matrix Diagonalization|eigenvalues]] of $T$, let $W_i$ be the eigenspace of $T$ corresponding to eigenvalue $\lambda_i$  and let $T_i$ be the [[Orthogonality and Orthonormality|orthogonal projection]] on $W_i$. Then 
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
* (*Friedberg 6.24.1*) If $F=\mathbb{C}$ then $T$ is normal if and only if $T^\ast = g(T)$ for some polynomial $g$. 
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
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]/]