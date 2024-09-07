* Let $V$ be a vector space over $F$. A function $K:V\to F$ is called a **quadratic form** if there exists a symmetric [[Bilinear Form|bilinear form]] $H\in\mathcal{B}(V)$ such that 
  $$
  K(x) = H(x,x)
  $$
* (*Friedberg e6.7.15*) If $F$ is a field not of [[Fundamental Constructs of Ring Theory|characteristic]] two, then 
  $$
  H(x,y) = \frac{1}{2}[K(x+y) - K(x) - K(y)]
  $$
* (*Friedberg 6.30.1*) Let $K$ be a quadratic form on a finite dimensional real [[Inner Product Space|inner product space]]. There exists an [[Orthogonality and Orthonormality|orthonormal]] basis $\beta=\set{x_1,\dots,x_n}$ for $V$ and scalars $\lambda_1,\dots,\lambda_n$ such that if $x\in V$ and
  $$
  x=\sum_{i=1}^n s_ix_i
  $$
  for $s_i\in\mathbb{R}$. Then 
  $$
  K(x) = \sum_{i=1}^n \lambda_is_i^2
  $$
  If $H$ is the symmetric bilinear form associated by $K$, then $\beta$ can be chosen to be any orthonormal basis for $V$ for which $\psi_\beta(H)$ is a diagonal matrix.

# Links
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]]