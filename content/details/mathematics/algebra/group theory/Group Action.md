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


* The subset of $G$ leaving every element of $X$ fixed is a [[Normal Group]] $N\unlhd G$.  
* A subset $S\subseteq X$ is **$G$-invariant** if 
  $$
  \forall x\in S, g\in G \ \ \ gx = x
  $$



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
	* If $x_1,\dots,x_n$ are distinct elements of $X$ then
	  $$
	  \text{Stab}_G(x_1,\dots,x_n) = \bigcap_{i} \ \text{Stab}_G(x_i)
	  $$
	  Which is also a subgroup since intersections of subgroups are subgroups. We call this the **pointwise stabilizer** of $\set{x_1,\dots,x_n}$. 
	* If $S\subseteq X$, then the **setwise stabilizer** is the stabilizer 
	  $$
	  \text{Stab}_G(S) = \set{g\in G\mid \sigma_g(S) = S}
	  $$

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

* (*Fraleigh 16.16*, *Godsil 2.2.2*) **Orbit-Stabilizer Theorem**  Let $X$ be a $G$-set and $x\in X$. Then 
  $$
  |\text{Orb}_G(x)|=(G : \text{Stab}_G(x))
  $$
  Also if $|G|$ is finite, 
  $$
  |G|=|\text{Orb}_G(x)| \ |\text{Stab}_G(x)|
  $$
	* *Intuition*: We can establish a one-to-one map from $\text{Orb}_G(x)$ to the collection of left cosets of $\text{Stab}_G(x)$ which gives the first relation. The second relation follows immediately from the definition of the group index.
	  
	  A more precise lemma is given below
		* (*Godsil 2.2.1*) Let $G$ be a permutation group acting on $X$ and $S$ an orbit of $G$.  If $x,y\in S$, the set of permutations in $G$ that map $x$ to $y$ is a right coset of $\text{Stab}_G(x)$. Conversely, all elements in a right coset of $\text{Stab}_G(x)$ map $x$ to the same point in $S$. 
	* *Intuition* A second way to view this is with the lens of the [[Group Homomorphism|fundamental homomorphism theorem]]. Define a homomorphism $\phi:G\to G$ in the obvious way using the group operation on $G$. The elements of $G$ form a $G$-set. 
	  It can then be shown that $\text{Stab}_G(e)=\text{ker}(\phi)$ and $\text{Orb}_G(e) =\phi(G)$. The Orbit-Stabilizer theorem immediately follows.  

* (*Fraleigh e16.16*) Every $G$-set is isomorphic to a disjoint union of left coset $G$-sets.

* (*Fraleigh 17.1*, *Godsil 2.2.4*) **Burnside's Lemma**. Let $G$ be a finite group and $X$ a finite $G$-set. Then the number of orbits $|X/G|$ is calculated as 
  $$
  |X/G|=\frac{1}{|G|}\sum_{g\in G}|X^g|
  $$
  Where $X^g$ denotes the elements of $X$ fixed by $g$. $$X^g=\{x\in X\mid gx=x\}$$In other words *the number of orbits, equals the average number of fixed points*.
	* *Proof*: The lemma follows by counting two ways in the following equation
	  $$
	  |G| \cdot |X/G| = \sum_{g\in G}|X^g| 
	  $$
	  Both sides count how many total fixed points are possible. That is, the number of $(g,x)$ pairs where $gx=x$. 
	  
	  The RHS counts this on $g$, counting the fixed points for each element $g$
	  
	  The LHS counts this on $x$ can be better expressed as follows. The number is precisely by $\text{Stab}_G(x)$. The Orbit-Stabilizer Theorem then gives the following.
	  $$
	  \sum_{x\in X} |\text{Stab}_G(x)| = \sum_{x\in X} \frac{|G|}{|\text{Orb}_G(x)|} = |G| \sum_{x\in X} \frac{1}{\text{Orb}_G(x)}
	  $$
	  Let $X/G$ be the set of unique orbits. Let $|X/G|= r$. We can group each $x$ that are part of the same orbit (since orbits define an equivalence relation).
	  
	  $$
	  \sum_{x\in X} \frac{1}{\text{Orb}_G(x)} = \sum_{O\in X/G} \sum_{x\in O} \frac{1}{|O|} = \sum_{O\in X/G} |O| \frac{1}{|O|} = \sum_{O\in X/G}1 = |X/G| =r
	  $$ 
	* Every element of $X$ is in precisely one orbit. Therefore 
	  $$
	  |X| = \sum_{\mathcal{O}\in X/G} |\mathcal{O}|
	  $$
* **General Class Equation**: Every element of $X^g$ consists of one-element orbits in $X$. Therefore 
  $$
  |X| = |\text{fix}_G(X)| + \sum_{x \notin \ \text{fix}_G(X)} |{\text{Orb}_G(x)}|
  $$
* **Classic Class Equation**. From the General Class Equation, suppose $X=G$ and the action of $G$ on $G$ is by conjugation so $g\in G$ maps $x\in G$ to $gxg^{-1}$. Then 
  $$
  \begin{split}
  \text{fix}_G(X)  &= \set{x\in G \mid gxg^{-1} = x \ \forall g\in G} = Z(G)
  \end{split}
  $$
  Now we have
  $$
  |G| = |Z(G)| + \sum_{x\notin Z(G) } |\text{Orb}_G (x) |
  $$
	* We refer to each orbit in $G$ under conjugation by $G$ as a **conjugate class** in $G$. 
	* (*Godsil 2.2.3*) Let $G$ be a permutation group acting on $X$ and let  $x\in X, g\in G$. Then 
	  $$
	  g \ G_x   g^{-1} = G_{gx}
	  $$
	  In other words, *the stabilizers of two points in the same orbit are conjugates*
		* *Proof*: If $gx= y$ then we show every element of the LHS fixes $y$. If $h\in G_x$ then 
		  $$
		  ghg^{-1} y = ghx = gx = y
		  $$
		  So $ghg^{-1} \in G_x$. Similarly, we can show that if $h\in G_y$, then $g^{-1}hg$ fixes $x$ which proves the theorem.
# Topics
* [[Group Action Orbital]]
* [[Primitive Permutation]]
* [[Transitive Group]]
* [[Regular Group]]

# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh]]
* [[Algebraic Graph Theory by Godsil and Royle]]

* [[Cosets, Group Indices]]
