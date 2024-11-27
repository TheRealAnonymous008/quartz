*  $N\le G$ is **normal** if its left and right [[Cosets, Group Indices|cosets]] coincide i.e.
  $$
  gN=Ng
  $$
  $\forall g\in G$. We denote this with $N\unlhd G$.

* A group is a **simple group** if it is nontrivial and has no proper nontrivial normal [[Subgroup|subgroups]]. 
	* That is, it does not have a factor group that is not the trivial subgroup or the group itself.

* (*Fraleigh 14.13*) The following are equivalent conditions for $H\le G$ to be normal. $\forall g \in G$ and $\forall h\in H$, the following holds
	* $ghg^{-1}\in H$
	* $gHg^{-1}=H$
	* $gH=Hg$ 
	* $H$ is invariant under all inner [[Group Isomorphism|automorphisms]] of $G$. That is $\forall g \in H \ \ \  H \le G$ 
	  $$
	  i_g[H]=H
	  $$

* (*Fraleigh e14.31*) Let $N_1,N_2 \unlhd G$, then the intersection is also normal
  $$
  N_1\cap N_2 \unlhd G
  $$ 
* (*Fraleigh e14.34*) If $G$ has exactly one subgroup $N$ of a given order, then $N$ is a normal subgroup of $H$. 

* A **maximal normal subgroup** of a group $G$ is a normal subgroup $M\ne G$ such that there is no proper normal subgroup $M< N\unlhd G$
* (*Fraleigh 15.18*) $M$ is the maximal normal [[Subgroup]] of $G$ if and only if $G/M$ is simple.

* (*Fraleigh 34.4*) If $N\unlhd G$ and $H\le G$, then 
  $$
  H\vee  N = NH = HN
  $$
  Also if $H$ is also normal in $G$, then $HN$ is also normal in $G$. 
	* *Idea*: To show the theorem, show that $NH$ is a subgroup of $G$. Since $H\vee N$ is the smallest subgroup containing $NH$, clearly if $NH$ is a subgroup $H\vee N = NH$. 

* Let $H,K\unlhd G$ and $K\le H$.  Then 
  $$
  H/K \unlhd G/K
  $$



* (*Fraleigh 35.10*) **Zassenhaus Lemma / Butterfly Lemma**. Let $H,K\le G$ and $H^\ast \unlhd H$ and $K^\ast \unlhd K$. Then
	* $H^\ast (H\cap K^\ast) \unlhd H^\ast (H\cap K)$ 
	* $K^\ast (H^\ast \cap K) \unlhd K^\ast (H\cap K)$
	* $(H^\ast \cap K) (H\cap K^\ast) \unlhd H\cap K$
	* 
	  $$
	  \begin{split}
	  H^\ast(H\cap K) / H^\ast(H\cap K^\ast) &\cong K^\ast(H\cap H)/K^\ast(H^\ast \cap K) \\ 
	  & \cong (H\cap K)/[(H^\ast \cap K)(H\cap K^\ast)]
	  \end{split}
	  $$
	* *Proof*: Let $H,K$ and $H^\ast, K^\ast$ be defined as the theorem. Clearly all products involved are groups by (*Fraleigh 34.4*).  To show the normal subgroup relation, we must show that $(H\cap K^\ast)\unlhd (H\cap K)$ and similarly $(H^\ast \cap K)\unlhd (H\cap K)$. All normal subgroup relations in the theorem then follow immediately from (*Fraleigh 34.4*). 
	  
	  Let $L=(H^\ast \cap K)(H\cap K^\ast)$
	  
	  To show the isomorphism, define the [[Group Homomorphism|homomorphism]] $\phi: H^\ast (H\cap K) \to (H\cap K)/L$ such that for $h\in H^\ast$ and $x\in H\cap K$, we have
	  $$
	  \phi(hx) = xL
	  $$
	  It is easy to show that $\phi$ is a well-defined homomorphism.  It is also onto.  Thus 
	  $$
	  \phi(Hx) = xL = L \iff x\in L \vee hx\in H^\ast L=H^\ast (H\cap K^\ast)
	  $$
	  Therefore $\text{Ker}(\phi) = H^\ast (H\cap K^\ast)$. The First Isomorphism Theorem guarantees the isomorphism.

![[Butterfly Lemma.png|500]]
<figcaption> Butterfly Lemma. Bold Lines indicate Normal Subgroup relations. The quotient groups formed from these relations are isomorphic. Image taken from Fraleigh</figcaption>


# Misc
* [[Subgroup Series]]

# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh]]