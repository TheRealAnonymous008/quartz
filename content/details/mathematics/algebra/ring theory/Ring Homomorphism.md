* Let $R,R'$ be [[Fundamental Constructs of Ring Theory|ring]]. A map $\phi:R\to R'$ is a **ring homomorphism** if $\forall a,b\in R$, the following hold
	* $\phi(a+b)=\phi(a)+\phi(b)$
	* $\phi(ab)=\phi(a)\phi(b)$

* The **Kernel** $\text{Ker}(\phi)$ is the set defined as
  $$
  \text{Ker}(\phi) = \{a\in R\mid \phi(a)=0'\}
  $$
  Where $0'$ is the additive element of $R'$

* Ring homomorphisms are a generalization of [[Group Homomorphism|group homomorphisms]]. All results concerning group homomorphisms are valid for the additive structure of rings
	* $\phi$ is one-to-one if and only if $\text{Ker}(\phi) = \{0\}$

* Let $F$ be the ring of all functions mapping $R\to\mathbb{R}$. The **evaluation homomorphism** is defined for each $a\in R$. as $\phi_a:F\to\mathbb{R}$ where 
  $$
  \phi_a(f) = f(a)
  $$
  For $f\in F$ and $\forall a\in R$.  

* A **Ring [[Group Isomorphism|isomorphism]]** $\phi:R\to R'$ is a one-to-one and onto homomorphism. We say that rings $R,R'$ are isomorphic denoted $R\cong R'$ 
# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh|Fraleigh]]