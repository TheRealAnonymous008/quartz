* **Empty Graph** - the graph with no vertices.
* **Null Graph** - $N_n$  - the graph with no edges.

* **Complete Graph** - $K_n$ - the graph where each pair of distinct vertices is adjacent.

* **Bipartite Graph** - it is possible to split the vertex set into two disjoint sets called the **bipartition** $A,B$ such that each edge is of the form $ab, a\in A, b\in B$ 
	* $G$ is bipartite if it can be expressed as the union of disjoint, possibly empty independent sets
	* $G$ is $2$-colorable.
	* (*Wilson 5.1*) $G$ is bipartite if and only if every cycle has even length.

* **Complete Bipartite Graph** - $K_{r,s}$ given the bipartition of the bipartite graph. $A,B$, all vertices from $A$ are adjacent to all vertices in $B$.
  
  $$
  \forall a\in A, \forall b\in B, ab\in E(G)
  $$
  Here $r=|A|, s=|B|$

* A **regular** graph is a graph where the [[Graph Connectivity|degree]] of each vertex in the graph is equal. If each vertex has degree $k$, then the graph is $k$-regular.
  
  More formally, if $G$ is the $k$-regular graph then 
  
  $$
  \forall v\in V(G), \ \deg(v)=k
  $$

* **Cubic Graph** - a $3$-regular graph.

* A **cycle** of $n$ vertices is denoted $C_n$ 

# Links
* [[Fundamental Constructs in Graph Theory]]
* [[Trails, Walks, Paths and Cycles]]