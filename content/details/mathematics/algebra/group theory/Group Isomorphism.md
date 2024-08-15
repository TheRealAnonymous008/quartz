* Let $(G,\ast)$ and $(H,\circ)$ be binary algebraic structures. A bijection $\phi: G\to H$ is an **isomorphism** if $\forall g_1,g_2,\in G$ 
  $$
  \phi(g_1\ast g_2)=\phi(g_1)\circ \phi(g_2)
  $$
  We say $G\cong H$ (i.e., the groups are **isomorphic**.
	* It is a [[Relation|bijective]] [[Group Homomorphism]]

* A **structural property** is a property that is preserved under isomorphism.

* (*Fraleigh 8.15*) Let $G$ and $G'$ be groups and $\phi:G\to G'$ be a one-to-one function such that $\phi(xy) = \phi(x)\phi(y)$ $\forall x, y\in G$. Then the image $\phi[G]$ is a [[Subgroup]] of $G'$ and $\phi$ provides an isomorphism of $G$ with $\phi[G]$. In other words
  
  $$
  \{\phi(x) \mid x\in G\} \le G'
  $$

* An **automorphism** is an isomorphism of a group to itself (i.e., $\phi: G\to G$)
	* The **inner automorphism** of $G$ by $g$ is defined as 
	  $$
	  i_g(x)=gxg^{-1}
	  $$
	  Performing it is called the **conjugation** of $x$ by $g$
	*  A **conjugate subgroup** of $H$ is given by
	  $$
	  K=i_g(H)
	  $$

* As a corollary to (*[[Group Homomorphism|Fraleigh 13.18]]*) a mapping $\phi:G\to G'$ can be shown to be an Isomorphism by showing the following
	* $\phi$ is a homomorphism
	* $\text{Ker}(\phi) = \{e\}$
	* $\phi$ is onto.
# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh]]
* [[Fundamental Constructs of Group Theory]]