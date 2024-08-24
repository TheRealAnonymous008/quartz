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

# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh]]