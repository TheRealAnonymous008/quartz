* **Empty Graph** - the graph with no vertices.
* **Null Graph** - $N_n$  - the graph with no edges.

* **Complete Graph** - $K_n$ - the graph where each pair of distinct vertices is adjacent.


* **Hypercube Graph** - $Q_n$ - the graph whose vertices correspond to the vertices and edges correspond to that of a $n$-dimensional hypercube
	* It can also be interpreted as the graph on $2^n$ binary numbers where edges connect tuples which differ in one bit. 
	* (*Godsil 3.1.1*) $Q_n$ is [[Vertex Transitive Graph|vertex transitive]].
	* $|\text{Aut}(Q_n)| = 2^kk!$  

* [[Trails, Walks, Paths and Cycles]]
	* A **path** of $n$ vertices is denoted $P_n$.
	* A **cycle** of $n$ vertices is denoted $C_n$ 
* [[Eulerian Graph]]
* [[Hamiltonian Graph]]
* [[Bipartite Graph]]
* [[Tree]]
* [[Infinite Graph]]
* [[Directed Graph]]

* A **circulant graph** is defined as follows.  Let $C\le \mathbb{Z}_n$ (see [[Cyclic Group|here]]). Construct a directed graph $X$ such that 
  $$
  \begin{split}
  V(X) &= \mathbb{Z}_n \\
  E(X) &= \set{(i,j) \mid j-i\in C}
  \end{split}
  $$
  If we assume that $-c\in C\iff c\in C$, then $C$ is closed under additive inverses and the graph is undirected. 
  
  That is, a circulant graph is a graph acted on by a cyclic group [[Group Action|acting]] on the vertices of the graph.

* [[Generalized Johnson Graph]]
* [[Line Graph]]

* [[Asymmetric Graph]]
* [[Vertex Transitive Graph]]
* [[Edge Transitive Graph]]
* [[Arc Transitive Graph]]
* [[Distance Transitive Graph]]
* [[Cayley Digraph]]
* [[Regular Graph]]

* The **Halin Graph** is a graph constructed as follows. Start with a [[Tree|tree]] with no vertex of degree $2$ and with at least one vertex of degree greater than $2$. Draw $T$ on the [[Graph Planarity|plane]] and then connect all leaves to form a cycle. 

* The **Latin squares** of order $n$ form a graph as follows. Each entry is represented as a tuple $(i,j,L_{ij})$ and edges are constructed between triples which agree on one coordinate.
	* It is [[Distance Transitive Graph|distance regular]] but not necessarily distance transitive.
	* It has diameter $2$.
	* It is regular with degree $3(n-1)$

* The **Coxeter Graph**
	* It has $28$ vertices
	* It is cubic 
	* It has girth $7$. 
	* Its full automorphism group has size $336$.
	* It acts $3$-regularly.
	* It can be made as an induced subgraph of $J(7,3)$. In particular, using the orbits of the triples $\set{124, 357, 367, 567}$. 
	* It can be constructed using the circulants on $\mathbb{Z}_7$. Start with the circulants. Then, add $7$ more vertices that are adjacent to the corresponding vertices in each circulant. 

![[Coxeter Graph 1.png|300]]
<figcaption> Coxeter Graph By Watchduck - Own work, CC BY-SA 4.0, https://commons.wikimedia.org/w/index.php?curid=121361030</figcaption>

* **Tutte's 8-cage** 
	* It consists of $30$ vertices.
	* There are two equivalent constructions for it:
		* Take the cube and the additional vertex $\infty$. In each set of four parallel edges, join the midpoint of each pair of opposite edges by an edge. Then join the midpoint of the two new edges by an edge. Then join the midpoint of this edge to $\infty$. 
		* Take the complete graph $K_6$. Construct a bipartite graph with the $15$ edges of $K_6$ as one partition and the $15$ $1$-factors as the other. Each edge is adjacent to the three $1$-factors that contain it. 

	* It is cubic
	* It is distance regular.

![[Tutte's 8-Cage.png|300]]
<figcaption> Tutte's 8 Cage Public Domain, https://commons.wikimedia.org/w/index.php?curid=618430 </figcaption>



# Links
* [[Fundamental Constructs of Graph Theory]]

* [[Algebraic Graph Theory by Godsil and Royle]]
* [[Introduction To Graph Theory by Wilson]]