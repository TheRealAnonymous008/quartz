
* An **incidence structure** consists of a set $\mathcal{P}$ of points, a set $\mathcal{L}$ of lines (disjoint from $\mathcal{P}$) and a [[Relation|relation]] $I \subseteq \mathcal P \times \mathcal L$ called **incidence**. If $(p,L)\in I$ we say that the point and the line are **incident**. +
* The **[[Graph Duality|dual]]** of an incidence structure $\mathcal{I}=(\mathcal P, \mathcal L, I)$ is the structure given by
  $$
  \mathcal I^\ast = (\mathcal L, \mathcal P, I^\ast)
  $$
  Where $I^\ast =\set{(L,p)\mid (p,L)\in I}$. 

* The **Incidence graph** also called the **Levi Graph** of an incidence structure $\mathcal I$ is the graph $X(\mathcal I)$ where
  $$
  \begin{split}
  V(X(\mathcal I)) &= \mathcal P \cup \mathcal L \\
  E(X(\mathcal I)) &= \set{(p,L)\mid (p,L) \in I}
  \end{split}
  $$
	* The incidence graph is [[Bipartite Graph|bipartite]]. 
	* Any bipartite graph can define an incidence structure by declaring one partition as points and the other as edges.
	* A bipartite graph contains both an incidence structure and its dual. 
* A **partial linear space** is an incidence structure where any two points are incident with at most one line.
	* Two points are **collinear** if they are joined by a [[Geometry|line]] (they are both incident to the line).
	* Two lines are **concurrent** if they meet at a point (they are both incident to the point).

* (*Godsil 5.1.1*)  The incidence graph $X$ of a partial linear space has girth at least $6$. 

* An [[Graph Automorphism|automorphism]] $\sigma$ of an incidence structure $(\mathcal P, \mathcal L, I)$ is a permutation of $\mathcal P\cup\mathcal L$ such that 
  $$
  \begin{split}
  \sigma(\mathcal P) &= \mathcal P \\ 
  \sigma(\mathcal L) &= \mathcal L \\
  (\sigma (p), \sigma (L)) &\iff (p,L)\in I
  \end{split}
  $$

	* An incidence preserving $\sigma$ of $\mathcal P\cup \mathcal L$ such that $\sigma(\mathcal P)=\mathcal L$ and $\sigma (\mathcal L) = \mathcal P$ is called a **duality**.
	* An incidence structure with a duality is **self-dual**. Such a structure is [[Category Theory|isomorphic]] to its dual.

# Topics
* [[Projective Plane]]
* [[Generalized Polygon]]
* [[t-Design]]


# Links
* [[Algebraic Graph Theory by Godsil and Royle]]