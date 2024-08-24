* Let $R,R'$ be [[Fundamental Constructs of Ring Theory|ring]]. A map $\phi:R\to R'$ is a **ring homomorphism** if $\forall a,b\in R$, the following hold
	* $\phi(a+b)=\phi(a)+\phi(b)$
	* $\phi(ab)=\phi(a)\phi(b)$

* The **Kernel** $\text{Ker}(\phi)$ is the set defined as
  $$
  \text{Ker}(\phi) = \{a\in R\mid \phi(a)=0'\}
  $$
  Where $0'$ is the additive element of $R'$

* A **Ring [[Group Isomorphism|isomorphism]]** $\phi:R\to R'$ is a one-to-one and onto homomorphism. We say that rings $R,R'$ are isomorphic denoted $R\cong R'$ 

* Ring homomorphisms are a generalization of [[Group Homomorphism|group homomorphisms]]. All results concerning group homomorphisms are valid for the additive structure of rings
	* (*Fraleigh 26.3*) Ring homomorphisms preserve subring structures (i.ee., subrings correspond to subrings under homomorphisms) in the same way that group homomorphisms preserve subgroup structure.

	* (*Fraleigh 26.5*) If $H=\text{Ker}(\phi)$ and $a\in R$, then $\phi^{-1}[\phi(a)]=a+H=H+a$ where $a+H$ is the [[Cosets, Group Indices|Coset]] containing $a$ of the commutative additive group $(H,+)$

	* (*Fraleigh 26.6*) $\phi$ is one-to-one if and only if $\text{Ker}(\phi) = \{0\}$
	* (*Fraleigh e26.21*) If $\phi:R\to R'$ be a ring homomorphism such that $\phi(R)\ne \{0'\}$, If $R$ has unity $1$ and $R'$ has no $0$ divisors, then $\phi(1)$ is unity for $R'$ 

* (*Fraleigh 26.7*) Let $\phi:R\to R'$ be a [[ring homomorphism]] with $H=\text{Ker}(\phi)$. Then the additive [[Cosets, Group Indices|cosets]] of $H$ form a ring $R/H$ whose binary operations are defined by choosing representatives. That is
  $$
  \begin{split}
  (a+H) + (b+H) &= (a+b) + H \\
  (a+H) \cdot (b+H) &= (ab) + H
  \end{split}
  $$
  Also the map $\mu:R/H\to \phi[R]$ defined by 
  $$
  \mu(a+H)=\phi(a)
  $$
  Is an isomorphism.



* (*Fraleigh 26.16*) **The Fundamental Homomorphism Theorem** **The Fundamental Homomorphism Theorem**.  Every [[Factor Ring]] gives rise to a natural homomorphism.

  Let $\phi:R\to R'$ be a homomorphism with $N=\text{Ker}(\phi)$. 
  
  Then $\phi(R)$ is a ring and $\mu:G/N\to \phi(G)$ given by $\mu(x+N)=\phi(x)$ is an isomorphism. In other words 
  $$
  R/\text{Ker}(\phi) \cong \phi(R)
  $$
  If $\phi$ is onto, then  the isomorphism changes to 
  $$
  R/\text{Ker}(\phi) \cong R'
  $$
  
  If $\gamma:R\to R/N$ is the homomorphism given by $\gamma(x)=x+N$, then $\forall x\in R$
  $$
  \phi(x)=\mu\gamma(x)
  $$
  We refer to $\mu$ and $\gamma$ as the **natural isomorphism** and **natural homomorphism** respectively. 
# Special Examples
* Let $F$ be the ring of all functions mapping $R\to\mathbb{R}$. The **evaluation homomorphism** is defined for each $a\in R$. as $\phi_a:F\to\mathbb{R}$ where 
  $$
  \phi_a(f) = f(a)
  $$
  For $f\in F$ and $\forall a\in R$.  

* Let $R_1,\dots, R_n$ be rings. For each $i$, the map $\pi:R_1\times R_2\times\dots\times R_n\to R_i$ defined by
  $$
  \pi(r_1,\dots,r_n)=r_i
  $$
  is the **projection homomorphism**

* The **Frobenius homomorphism** is a map $\phi_p:R\to R$ for a [[Commutative Ring]] with [[Ring with Unity|unity]] $R$ where $\text{char}(R)=p$ for prime $p$. It is defined as $\phi_p(a)=a^p$ 

# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh|Fraleigh]]