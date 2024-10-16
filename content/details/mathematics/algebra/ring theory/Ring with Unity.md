* Assuming it exists, $1$ is the multiplicative identity (also called **unity**). *The multiplicative identity need not exist for an arbitrary ring*. If a ring has unity, we refer to it as a ring with unity.

	* The following is immediately true
	  $$
	  (m\cdot 1) (n\cdot 1) = (mn) \cdot 1
	  $$
	* (*Fraleigh 19.15*) Let $R$ be a [[Fundamental Constructs of Ring Theory|ring]] with unity. If $n\cdot 1 \ne 0$ $\forall n\in \mathbb{Z}^+$ then $\text{char}(R) = 0$. 
	  
	  Otherwise, if $\exists n\in\mathbb{Z}^+$ such that $n\cdot 1 = 0$, then the smallest such $n$ is the characteristic of $R$. 
		* We may redefine the characteristic as the number of times we need to add the multiplicative identity to get the additive identity.

* An element $u\in R$ is a **unit** of $R$ if it has a multiplicative inverse. That is $u^{-1}$ is defined so that
  $$
  u\cdot u^{-1} = 1
  $$

* Let $R$ be a ring. The set of units of $R$ is denoted $R^\times$. 
* (*Fraleigh e18.37*) $R^\times$ is a [[Fundamental Constructs of Group Theory|group]]. 
	* The set $G_n$ of nonzero elements of $\mathbb{Z}_n$ that are not $0$ [[Integral Domain|divisors]] forms a group under multiplication modulo $n$.
* (*Fraleigh e18.42*) The multiplicative inverse of a unit is unique.

* (*Fraleigh e19.30*) *Every $R$ can be enlarged to a ring $S$ with unity* having the same characteristic as $R$. We define $S$ as follows. 
  
  $$
  S = \begin{cases}
  R\times \mathbb{Z} & \text{ if } \text{char} (R) = 0 \\
  R\times \mathbb{Z}^n & \text{ if } \text{char}(R) = n
  \end{cases}
  $$
  Addition in $S$ is the same as addition in $R$
  
  Multiplication is defined as
  $$
  (r_1,n_1)(r_2,n_2) = (r_1r_2 + n_1\cdot r_2 + n_2\cdot r_1 + n_1r_)
  $$
  
  We can show the following
	* $S$ is a ring
	* $S$ has unity
	* $\text{char}(R)=\text{char}(S)$
	* $\phi:R\to S$ where $\phi(r)=(r,0)$ gives an isomorphism onto a subring of $S$.

* (*Fraleigh 26.3*) Let $\phi:R\to R'$ be a [[Ring Homomorphism]]. If $R$ has unity $1$, then $\phi(1)$ is unity for $\phi[R]$.
  
  In other words, rings with unity are still rings with unity under homomorphism.

* (*Fraleigh 27.5*) If $R$ is a ring with unity, and $N$ an [[Ideal]] containing a unit, then $N=R$. 

* (*Fraleigh 27.17*) If $R$ is a ring with unity $1$, then the map $\phi:\mathbb{Z}\to R$ given by
  $$
  \phi(n)=n\cdot 1
  $$
  for $n\in\mathbb{Z}$ is a homomorphism.
* (*Fraleigh 27.18*) If $R$ is a ring with unity, then we have two cases:
  If $\text{char}(R)=n>1$, then $R$ contains a subring isomorphic to $\mathbb{Z}_n$.
  If $\text{char}(R)=0$, then $R$ contains a subring isomorphic to $\mathbb{Z}$ 


# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh|Fraleigh]]