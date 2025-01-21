* **Empty Graph** - the graph with no vertices.
* **Null Graph** - $N_n$  - the graph with no edges.

* **Complete Graph** - $K_n$ - the graph where each pair of distinct vertices is adjacent.

* A **regular** graph is a graph where the [[Graph Connectivity|degree]] of each vertex in the graph is equal. If each vertex has degree $k$, then the graph is $k$-regular.
  
  More formally, if $G$ is the $k$-regular graph then 
  
  $$
  \forall v\in V(G), \ \deg(v)=k
  $$

* **Cubic Graph** - a $3$-regular graph.

* [[Trails, Walks, Paths and Cycles]]
	* A **path** of $n$ vertices is denoted $P_n$.
	* A **cycle** of $n$ vertices is denoted $C_n$ 

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
# Links
* [[Fundamental Constructs of Graph Theory]]

* [[Algebraic Graph Theory by Godsil and Royle]]
* [[Introduction To Graph Theory by Wilson]]