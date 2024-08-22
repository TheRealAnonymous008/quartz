* Let $(G,\ast)$ and $(H,\circ)$ be binary algebraic structures. A mapping $\phi: G\to H$ is a **homomorphism** if $\forall g_1,g_2,\in G$ 
  $$
  \phi(g_1\ast g_2)=\phi(g_1)\circ \phi(g_2)
  $$
  
	* The homomorphism property says that the product of the maps is equal to the map of the products.

* (*Fraleigh e13.49*) The composition of homomorphisms is a homomorphism.
* (*Fraleigh 13.12*) Let $\phi:G\to G'$ be a homomorphism.
	* The identity is preserved. If $e$ is the identity of $G$, then $\phi(e)$ is the identity of $G'$
	* The inverse is preserved. 
	  $$
	  a\in G\implies \phi(a^{-1})=\phi(a)^{-1}
	  $$
	* [[Subgroup|Subgroups]] are preserved. 
	  $$
	  H\le G\implies \phi(H)\le G'
	  $$
	* Subgroup inverses are preserved 
	  $$
	  K'\le G'\implies \phi^{-1}(K)\le G
	  $$
	  
	* (*Fraleigh 15.16*) [[Normal Group|Normal]] groups are preserved.
	  $$
	  \begin{split}
	  N \unlhd G &\implies \phi(N) \unlhd \phi(G) \\
	  N'\unlhd \phi(G) &\implies \phi^{-1}(N') \unlhd G
	  \end{split}
	  $$

* Let $\phi:G\to G'$ be a homomorphism. The **kernel** of $\phi$, denoted $\text{Ker}(\phi)$  is defined as the subgroup 
  $$
  \text{Ker}(\phi)=\{x\in G\mid \phi(x)=e'\}
  $$
  Where $e'$ is the identity of $G'$.
	* We may think of this as the set of points which the homomorphism maps to a singularity $e'\in G'$

* (*Fraleigh 13.15*) If $H=\text{Ker}(\phi)$ and $a\in G$, then we have the cosets of $H$ as 
  $$
  aH=Ha= \{x\in G\mid \phi(x)=\phi(a)\} = \phi^{-1}[\{\phi(a)\}]
  $$
  It follows that the partition of $G$ into cosets is the same.
  
* (*Fraleigh 13.18*) A homomorphism is one to one if and only if $\text{Ker}(\phi)=\{e\}$. 

* (*Fraleigh 14.11*) **The Fundamental Homomorphism Theorem**.  Every [[Factor Group]] gives rise to a natural homomorphism.

  Let $\phi:G\to G'$ be a homomorphism with kernel $H$. 
  
  (*Fraleigh 13.20*) $\text{Ker}(\phi)$ is a [[Normal Group|normal subgroup]] subgroup of $G$
  
  Then $\phi(G)$ is a group and $\mu:G/H\to \phi(G)$ given by $\mu(gH)=\phi(g)$ is an isomorphism. In other words 
  $$
  G/\text{Ker}(\phi) \cong \phi(G)
  $$
  If $\phi$ is onto, then  the isomorphism changes to 
  $$
  G/\text{Ker}(\phi) \cong G'
  $$
  
  If $\gamma:G\to G/H$ is the homomorphism given by $\gamma(g)=gH$, then $\forall g\in G$
  $$
  \phi(g)=\mu\gamma(g)
  $$
  We refer to $\mu$ and $\gamma$ as the **natural isomorphism** and **natural homomorphism** respectively. 

* An [[Group Isomorphism|isomorphism]] is a homomorphism that is bijective.
* An **endomorphism** is a homomorphism from $G$ to itself.
# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh]]