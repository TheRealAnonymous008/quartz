
* **Bipartite Graph** - it is possible to split the vertex set into two disjoint sets called the **bipartition** $A,B$ such that each edge is of the form $ab, a\in A, b\in B$ 
	* $G$ is bipartite if it can be expressed as the union of disjoint, possibly empty independent sets
	* $G$ is $2$-colorable.
	* (*Wilson 5.1*) $G$ is bipartite if and only if every cycle has even length.
	* A bipartite graph is **semi-regular** if it has a proper $2$-coloring such that all vertices with the same color have the same degree.

* **Complete Bipartite Graph** - $K_{r,s}$ given the bipartition of the bipartite graph. $A,B$, all vertices from $A$ are adjacent to all vertices in $B$.
  
  $$
  \forall a\in A, \forall b\in B, ab\in E(G)
  $$
  Here $r=|A|, s=|B|$
	* A **star** graph is a special case, $K_{1,n}$. 


# Links
* [[Introduction To Graph Theory by Wilson]]