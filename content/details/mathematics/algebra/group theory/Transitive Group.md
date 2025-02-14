* $G$ is **transitive** on $G$-set $X$ if for every $x,y\in X$, there exists $g$ such that
  $$
  gx = y
  $$
* (*Godsil e2.3*) If $G$ is a non-trivial transitive permutation group on the set $V$, there is an element of $G$ with no fixed points. 
	* *Proof*: If $G$ has one orbit (i.e., it  is a cycle), then any non-identity element $g\in G$ will suffice. 
	  
	  Otherwise, by (*Fraleigh 9.8*) we can construct $g'\in G$ with no fixed points. For each $\mathcal{O}_i\in X/G$, take $g_i$ (which permutes all elements in its orbit) and form $g'$ by 
	  $$
	  g' = \prod_i g_i
	  $$


* (*Godsil 3.6.2*) Let $G$ be a transitive permutation group on $X$ and $S\subseteq X$. and 
  $$ 
  \min_{g\in G} |S\cap S^g| = c
  $$
  Then
  $$
  |S|\ge \sqrt{c|X|}
  $$

	* *Proof*: Count the pairs $(g,x) \mid g\in G, x\in S\cap S^g$. For each $g\in G$, there are at least $c$ points in $S$ so there are at least $c|G|$ pairs.
	  
	  Also, the elements of $G$ that map $x\mapsto y$ forms a [[Cosets, Group Indices|coset]] of $G_x$ and so there are exactly $|S||G_x|$ elements $g^{-1}$ of $G$ such that $g^{-1} x\in S$ or $x\in S^g$.
	  
	  Since $G$ is transitive, by the Orbit Stabilizer theorem
	  $$
	  |\text{Orb}_G(x)| = |X| = \frac{|G|}{|G_x|}
	  $$
	  So $|S|\le \sqrt{c|X|}$




# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh]]
* [[Algebraic Graph Theory by Godsil and Royle]]

* [[Group Action]]