* Let $H\le G$. 
  
  The **left coset** of $H$ containing $a$ is defined as 
  $$
  aH=\{ah \mid h\in H\}
  $$
  and the **right coset** of $H$ containing $a$ is defined as 
  $$
  Ha=\{ha\mid h\in H\}
  $$
  
* The cosets partition a group into [[Relation|equivalence classes]].
	* More specifically the left coset expresses the equivalence relation 
	  $$
	  a\sim b\iff a^{-1}b\in H
	  $$
	  
	* The right coset expresses 
	  $$
	  a\sim b\iff ab^{-1}\in H
	  $$
	  
* Every coset of a subgroup $H\le G$ has the same number of elements as $H$.
* Let $H,K\le G$. 
  
  The **double coset** is the set defined as 
  $$
  HxK=\{hxh\mid h\in H, k\in K\}
  $$
  
	* This forms an equivalence class where $x\sim y$ if and only if there exists $h\in H$ and $k\in K$ such that $hxk=y$.

# Group Index
* Let $H\le G$, the number of left cosets of $H$ in $G$ is called the **index** of $H$ and $G$. This is denoted $(G:H)$. 
* (*Fraleigh 10.14*) Let $H,K\le G$ such that $K\le H\le G$ and suppose $(H:K)$ and $(G:H)$ are both finite. Then $(G:K)$ is finite and 
  $$
  (G:K)=(G:H)(H:K)
  $$
# Normal Groups
*  $H\le G$ is **normal** if its left and right cosets coincide $\forall g\in G$ 
  $$
  gH=Hg
  $$
* A group is **simple** if it is nontrivial and has no proper nontrivial normal subgroups. 
	* That is, it does not have a factor group that is not the trivial subgroup or the group itself.

* (*Fraleigh 14.13*) The following are equivalent conditions for $H\le G$ to be normal. $\forall g \in G$ and $\forall h\in H$, the following holds
	* $ghg^{-1}\in H$
	* $gHg^{-1}=H$
	* $gH=Hg$ 
	* $H$ is invariant under all inner automorphisms of $G$.
* A **maximal normal subgroup** of a group $G$ is a normal subgroup $M\ne G$ such that there is no proper normal subgroup $M< N\le G$
* (*Fraleigh 15.18*) $M$ is the maximal normal [[subgroup]] of $G$ if and only if $G/M$ is simple.

# Links
* [[Subgroup]]