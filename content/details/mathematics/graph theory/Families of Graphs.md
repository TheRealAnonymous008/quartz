* **Empty Graph** - the graph with no vertices.
* **Null Graph** - $N_n$  - the graph with no edges.

* **Complete Graph** - $K_n$ - the graph where each pair of distinct vertices is adjacent.

* A **regular** graph is a graph where the [[Graph Connectivity|degree]] of each vertex in the graph is equal. If each vertex has degree $k$, then the graph is $k$-regular.
  
  More formally, if $G$ is the $k$-regular graph then 
  
  $$
  \forall v\in V(G), \ \deg(v)=k
  $$

* **Cubic Graph** - a $3$-regular graph.

* **Hypercube Graph** - $Q_n$ - the graph whose vertices correspond to the vertices and edges correspond to that of a $n$-dimensional hypercube
	* It can also be interpreted as the graph on $2^n$ binary numbers where edges connect tuples which differ in one bit. 
	* (*Godsil 3.1.1*) $Q_n$ is [[Transitive Graph|vertex transitive]].
	* $|\text{Aut}(Q_n)| = 2^kk!$  

* [[Trails, Walks, Paths and Cycles]]
	* A **path** of $n$ vertices is denoted $P_n$.
	* A **cycle** of $n$ vertices is denoted $C_n$ 
* [[Eulerian Graph]]
* [[Bipartite Graph]]
* [[Trees]]
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
* [[Transitive Graph]]
* [[Cayley Digraph]]

* The **Halin Graph** is a graph constructed as follows. Start with a [[Trees|tree]] with no vertex of degree $2$ and with at least one vertex of degree greater than $2$. Draw $T$ on the [[Graph Planarity|plane]] and then connect all leaves to form a cycle. 
# Links
* [[Fundamental Constructs of Graph Theory]]

* [[Algebraic Graph Theory by Godsil and Royle]]
* [[Introduction To Graph Theory by Wilson]]