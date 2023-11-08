## Field Types
* A **trivial matroid** is the matroid whose only independent set is the empty set. Its rank is $0$.
* A **discrete matroid** on a non-empty finite set $E$ is a matroid in which every subset of $E$ is an independent set 
* A **$k$-uniform matroid** is a matroid on a non-empty finite set $E$, whose bases are those subsets with exactly $k$-elements. If $E$ has $n$ elements, then we denote this matroid as $U^k_n$. 
	* The independent of a **uniform matroid** are the subsets of $E$ with no more than $k$ elements. 
	* It also follows that the rank is defined as 
	  $$
	  r(A)=\min(|A|,k)
	  $$


* A **representable matroid** is a matroid over a set $E$ over a field $F$ where there exists a [[Linear Algebra|vector space]] over $F$ and a map $\phi: E\to V$ such that a subset $A\subseteq E$ is independent in $M$ if and only if $\phi(A)$ is linearly independent. 
	* In other words, we may map all independent sets of the matroid to linearly independent subsets of the vector space.
	* A matroid is **representable** if such a field exists.
	* Representable matroids form an isomorphism class
  
* A **regular matroid** is representable over every field.

 * A **binary matroid** is a matroid that is representable over the field of integers modulo $2$.

* The **Fano Matroid** $F$ is the matroid defined on the set $E=\{1,2,3,4,5,6,7\}$ whose bases are all the subsets of $E$, except $\{1,2,4\}$,  $\{2,3,5\}$,  $\{3,4,6\}$,  $\{1,5,6\}$,  $\{2,6,7\}$,  $\{4,5,7\}$ and  $\{1,3,7\}$.
	* The Fano Matroid is binary and Eulerian 
	* The Fano Matroid is not graphic, cographic, transversal, nor regular

## [[Graph Theory]] related
* The **cycle matroid** also called the **graphic matroid** of a graph $G$ is an isomorphism class of matroids associated with graph $G$ denoted $M(G)$
  
  It is defined as the matroid on the set of edges of $G$, with the bases being the [[Spanning Trees and Forests|spanning forests]] of $G$.
	* In a graphic matroid, a loop generalizes the graph theory loops and parallel elements generalize multiple edges. 
	* Isomorphism preserves cycles, cut-sets and the number of edges, but not necessarily connectedness the number of vertices or their degrees

* The **cutset matroid** also called the **cographic matroid** of a graph $G$ is an isomorphism class of matroids associated with $G$ denoted $M^\ast(G)$
  
  It is the matroid on the set of edges of $G$ with the bases being the [[Trees|cotrees]] and the cycles being the [[Graph Connectivity|cut-sets]]

* A **Planar Matroid** is a matroid that is both graphic and cographic. 
  
  It corresponds to [[Graph Planarity|planar graphs]].

* A **[[Families of Graphs|bipartite]] matroid** is a matroid in which each cycle has an even number of elements.
* An **[[Trails, Walks, Paths and Cycles#Eulerian Graphs|Eulerian]] Matroid** is a matroid on $E$ if $E$ can be written as a set of disjoint of disjoint cycles. 

## [[Transversal Theory|Transversal]] Related  
* Let $E$ be a non-empty finite set and $\mathcal{F} = \{S_1, \dots, S_m\}$ a family of subsets of $E$. Then, the **transversal matroid** is a matroid where the independent sets are the partial transversals of $\mathcal{F}$
  
  We denote this matroid as $M(\mathcal{F})$. 

* Up to isomorphism, the number of transversal matroids where $n=|E|$ is 
  $$
  2^{n^2}
  $$
* Every transversal matroid is representable over some field $F$.
* Every transversal matroid is binary if and only if it is graphic. 

# Other Theorems 
* Graphic Matroids are Binary Matroids. [^1] 

[^1]: Each edge of $G$ can be associated with a binary vector in line with its incidence matrix. If a set of edges form a cycle, the sum of the vectors is even. 

* (*Wilson e31.6*) Every uniform matroid is transversal. 
	* *Proof*: If $M$ is a $k$-uniform matroid, then $M=M(\mathcal{F})$, where $\mathcal{F}$ consists of $k$ copies of $E$.

* **Tutte's Theorems**
	* A binary matroid is regular if and only if it contains no minor isomorphic to the Fano Matroid or its dual 
	* (*Wilson 32.9*) A matroid is graphic if and only if it is binary and it contains no minor isomorphic to $M^\ast(K_5). M^\ast(K_{3,3})$ or to the Fano Matroid and its dual. 
	* (*Wilson 32.9*) A matroid is cographic if and only if it is binary and it contains no minor isomorphic to $M(K_5). M(K_{3,3})$ or to the Fano Matroid and its dual. 

* **[[Graph Planarity|Kuratowski's Theorem]] Analogue** -- A matroid is planar if and only if it regular, and contains no minor isomorphic to $M(K_5), M(K_{3,3})$ or their duals.  [^2]

[^2]: Tutte's Theorems on graphic, cographic, and binary matroids combined lead to the theorem.
# Links 
* [[Matroid Definitions and Constructs]]
* [[Graph Duality]] - related applications of Matroids to Graph Theory