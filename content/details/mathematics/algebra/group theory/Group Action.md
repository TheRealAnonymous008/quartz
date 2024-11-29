* Let $X$ be a set and $G$ a group. An **action** of $G$ on $X$ is a map $\ast:G\times X\to X$  such that $\forall x\in X$ and $\forall g_1,g_2\in g$
	* $ex=x$
	* $(g_1g_2)x = g_1(g_2x)$ 
* $X$ in the above is called the $G$-**set**.

* (*Fraleigh 16.3*) Let $X$ be a $G$-set. 
  
  For each $g\in G$, the function $\sigma_g:X\to X$. defined $\forall x\in X$ as 
  $$
  \sigma_g(x)=gx
  $$
  is a [[Permutations and Orbits|permutation]] of $X$.
  
  Also, the map $\phi: G\to S_X$ defined by $\phi(g)=\sigma_g$ is a [[Group Homomorphism]] with the property that 
  $$
  \phi(g)(x)=gx
  $$
	* *Intuition*: We establish that $\sigma_g$ is a one-to-one map of $X$ onto itself, which proves that it is a permutation, which follows from the two properties of the group action.
	  
	  The homomorphism follows by showing that $\phi(g_1 g_2)$ maps $x$ to the same element as $\phi(g_1)\phi(g_2)$ satisfying the homomorphism property. This immediately follows from the composition of permutations.
	* $G$ is **transitive** on $G$-set $X$ if and only if $\phi(G)$ is transitive.

* The subset of $G$ leaving every element of $X$ fixed is a [[Normal Group]] $N\unlhd G$.
* $G$ **acts faithfully** on $X$ if only the identity element leaves every $x\in X$ fixed.
* Two $G$-sets $X,Y$ are **isomorphic** if there exists a bijective mapping $\phi:X\to Y$ such that $\forall x\in X, g\in G$ 
  $$
  g\phi(x)=\phi(gx)
  $$
   
* Let $X$ be a $G$-set and $x\in X$. The subgroup $\text{Stab}(x)$ is the **isotropy subgroup** or **stabilizer** of $x$ defined as 
  $$
  \text{Stab}_G(x) =\{g\in G\mid gx=x\}
  $$
  See (*Fraleigh 16.12*) for why it is a [[Subgroup]]. 

* The **orbit** of $x\in X$ under $G$ is defined as the partition of the equivalence relation defined where: 
  $$
  x_1\equiv x_2\iff \exists g\in G, gx_1=x_2
  $$
  We denote the orbit as 
  $$
  \text{Orb}_G(x)=\{g\ast x \mid g \in G \}
  $$
	* In other words, the orbit is the set of all elements in $X$ reached by repeatedly applying the group action to $x$.
	* See (*Fraleigh 16.14*) for why it is an equivalence [[Relation]]. 
	* (*Fraleigh e16.6*) Every $G$-set is the union of its orbits. Also, the union of $G$-sets is a $G$-set.

* (*Fraleigh 16.16*) **Orbit-Stabilizer Theorem**  Let $X$ be a $G$-set and $x\in X$. Then 
  $$
  |\text{Orb}_G(x)|=(G : \text{Stab}_G(x))
  $$
  Also if $|G|$ is finite, 
  $$
  |G|=|\text{Orb}_G(x)| \ |\text{Stab}_G(x)|
  $$
	* *Intuition*: We can establish a one-to-one map from $\text{Orb}_G(x)$ to the collection of left cosets of $\text{Stab}_G(x)$ which gives the first relation. The second relation follows immediately from the definition of the group index.
	* *Intuition* A second way to view this is with the lens of the [[Group Homomorphism|fundamental homomorphism theorem]]. Define a homomorphism $\phi:G\to G$ in the obvious way using the group operation on $G$. The elements of $G$ form a $G$-set. 
	  It can then be shown that $\text{Stab}_G(e)=\text{ker}(\phi)$ and $\text{Orb}_G(e) =\phi(G)$. The Orbit-Stabilizer theorem immediately follows.  

* (*Fraleigh e16.16*) Every $G$-set is isomorphic to a disjoint union of left coset $G$-sets.

* (*Fraleigh 17.1*) **Burnside's Lemma**. Let $G$ be a finite group and $X$ a finite $G$-set. Then the number of orbits $|X/G|$ is calculated as 
  $$
  |X/G|=\frac{1}{|G|}\sum_{g\in G}|X^g|
  $$
  Where $X^g$ denotes the elements of $X$ fixed by $g$. $$X^g=\{x\in X\mid gx=x\}$$In other words *the number of orbits, equals the average number of fixed points*.
	* *Proof*: The lemma follows by counting two ways in the following equation
	  $$
	  |G| \cdot |X/G| = \sum_{g\in G}|X^g| 
	  $$
	  Both sides count how many total fixed points are possible. That is, the number of $(g,x)$ pairs where $gx=x$. 
	  
	  The RHS counts this on $g$, counting the fixed points for each element$g$
	  
	  The LHS counts this on $x$ can be better expressed as follows. The number is precisely by $\text{Stab}_G(x)$. The Orbit-Stabilizer Theorem then gives the following.
	  $$
	  \sum_{x\in X} |\text{Stab}_G(x)| = \sum_{x\in X} \frac{|G|}{|\text{Orb}_G(x)|} = |G| \sum_{x\in X} \frac{1}{\text{Orb}_G(x)}
	  $$
	  Let $\mathcal{O}$ be the set of unique orbits. Let $|\mathcal{O}|= r$. We can group each $x$ that are part of the same orbit (since orbits define an equivalence relation).
	  
	  $$
	  \sum_{x\in X} \frac{1}{\text{Orb}_G(x)} = \sum_{O\in \mathcal{O}} \sum_{x\in O} \frac{1}{|O|} = \sum_{O\in \mathcal{O}} |O| \frac{1}{|O|} = \sum_{O\in \mathcal{O}}1 = |\mathcal{O}| =r
	  $$ 
	* Every element of $X$ is in precisely one orbit. Therefore 
	  $$
	  |X| = \sum_{\mathcal{O}} |\mathcal{O}|
	  $$
	* Every element of $X^g$ consists of one-element orbits in $X$. Therefore 
	  $$
	  |X| = |X^G| + \sum_{\mathcal{O}\notin X^g} |\mathcal{O}|
	  $$
	  Where $\mathcal{O}\notin X^g$ is notational shorthand for orbits with more than one element.


# Links
* [[Cosets, Group Indices]]
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh]]