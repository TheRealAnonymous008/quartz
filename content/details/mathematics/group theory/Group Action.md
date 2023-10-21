* Let $X$ be a set and $G$ a group. An **action** of $G$ on $X$ is a map $\ast:G\times X\to X$  such that $\forall x\in X$ and $\forall g_1,g_2\in g$
	* $ex=x$
	* $(g_1g_2)x = g_1(g_2x)$ 
* $X$ in the above is called the $G$-**set**.
* (*Fraleigh 16.3*) Let $X$ be a $G$-set. For each $g\in G$, the function $\sigma_g:X\to X$. defined $\forall x\in X$ as 
  $$
  \sigma_g(x)=gx
  $$
  is a permutation of $X$.
  
  Also, the map $\phi: G\to S_X$ defined by $\phi(g)=\sigma_g$ is a homomorphism with the property that 
  $$
  \phi(g)(x)=gx
  $$
  
* $G$ **acts faithfully** on $X$ if only the identity element leaves every $x\in X$ fixed.
* $G$ is **transitive** on $G$-set $X$ if and only if $\phi(G)$ is transitive.
* Two $G$-sets $X,Y$ are **isomorphic** if there exists a bijective mapping $\phi:X\to Y$ such that $\forall x\in X, g\in G$ 
  $$
  g\phi(x)=\phi(gx)
  $$
   
* Let $X$ be a $G$-set and $x\in X$. The subgroup $\text{Stab}(x)$ is the **isotropy subgroup** or **stabilizer** of $x$ defined as 
  $$
  \text{Stab}_G(x) =\{g\in G\mid gx=x\}
  $$
  See (*Fraleigh 16.12*) for why it is a subgroup. 

* The **orbit** of $x\in X$ under $G$ is defined as the partition of the equivalence relation defined where: 
  $$
  x_1\equiv x_2\iff \exists g\in G, gx_1=x_2
  $$
  We denote the orbit as $\text{Orb}_G(x)$.
	* In other words, the orbit is the set of all elements in $X$ reached by repeatedly applying the group action to $x$.
  
  
  See (*Fraleigh 16.14*) for why it is an equivalence relation.

* **Orbit-Stabilizer Theorem** (*Fraleigh 16.16*) Let $X$ be a $G$-set and $x\in X$. Then 
  $$
  |\text{Orb}_G(x)|=(G : \text{Stab}_G(x))
  $$
  Also if $|G|$ is finite, 
  $$
  |G|=|\text{Orb}_G(x)| \ |\text{Stab}_G(x)|
  $$
  
* (*Fraleigh e16.16*) Every $G$-set is isomorphic to a disjoint union of left-coset $G$-sets.
* **Burnside's Lemma**. Let $G$ be a finite group and $X$ a finite $G$-set. Then the number of orbits $|X/G|$ is calculated as 
  $$
  |X/G|=\frac{1}{|G|}\sum_{g\in G}|X^g|
  $$
  Where $X^g$ denotes the elements of $X$ fixed by $g$. $$X^g=\{x\in X\mid gx=x\}$$In other words *the number of orbits, equals the average number of fixed points*.
# Links
* [[Group]]
* [[Group Index]]
* [[Group Homomorphism]]
* [[Permutations and Orbits]]