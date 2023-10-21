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
	* Subgroups are preserved. 
	  $$
	  H\le G\implies \phi(H)\le G'
	  $$
	* Subgroup inverses are preserved 
	  $$
	  K'\le G'\implies \phi^{-1}(K)\le G
	  $$
	  
	* (*Fraleigh 15.16*) Normal groups are preserved.
	  
	  If $N\le G$ and $N'\le G'$ are normal subgroups, then so are $\phi(N)$ and $\phi^{-1}(N')$.

* Let $\phi:G\to G'$ be a homomorphism. The **kernel** of $\phi$, denoted $\text{Ker}(\phi)$  is defined as the subgroup 
  $$
  \text{Ker}(\phi)=\{x\in G\mid \phi(x)=e'\}
  $$
  Where $e'$ is the identity of $G'$.
* (*Fraleigh 13.15*) If $H=\text{Ker}(\phi)$ and $a\in G$, then we have the cosets of $H$ as 
  $$
  aH=Ha= \{x\in G\mid \phi(x)=\phi(a)\}
  $$
  
* (*Fraleigh 13.18*) A homomorphism is one to one if and only if $\text{Ker}(\phi)=\{e\}$
* (*Fraleigh 13.20*) If $\phi:G\to G'$ is a subgroup, then $\text{Ker}(\phi)$ is a normal subgroup of $G$
* (*Fraleigh 14.11*) **The Fundamental Homomorphism Theorem**.  Every factor group gives rise to a natural homomorphism.

  Let $\phi:G\to G'$ be a homomorphism with kernel $H$. 
  
  Then $\phi(G)$ is a group and $\mu:G/H\to \phi(G)$ given by $\mu(gH)=\phi(g)$ is an isomorphism. 
  
  If $\gamma:G\to G/H$ is the homomorphism given by $\gamma(g)=gH$, then $\forall g\in G$
  $$
  \phi(g)=\mu\gamma(g)
  $$
  We refer to $\mu$ and $\gamma$ as the **natural** isomorphism and homomorphism respectively. 
# Links
* [[Normal Group]]
* [[Subgroup]]