# Components
* A **component** of a graph is a maximally connected subgraph of the particular graph. That is, we cannot add any more vertices and edges to the subgraph. The number of components is denoted $\omega(G)$
	* (*Component-Edge Inequality*, *Wilson 5.2*) - Let $G$ be a simple graph with $n$vertices. If $G$ has $k$ components, then the number of edges $m$ satisfies:
	  $$
	  n - k \le m \le \frac{(n-k)(n-k+1)}{2}
	  $$
	  * (*Theorem*): Let $H\subseteq G$, then 
	    $$
	    \omega(G) \le \omega(H)
	    $$
	* (*Wilson 5.3*) Any simple graph with $n$ vertices and more than $\frac{(n-1)(n-2)}{2}$ edges is connected [^3]

[^3]: Substitute $k=1$ to the Component-Edge inequality.

* Two special cases of components
	* An **isolated vertex** is a vertex with degree $0$.
	* A component is **trivial** if it has no edges

* Two vertices $v,w\in V$ are **connected** if there exists a a [[Trails, Walks, Paths and Cycles|path]] in $G$ that connects $u$ and $v$. Otherwise they are **disconnected vertices**.
	* Adjacency is a special case of ocnnectivity.

* A graph is **connected** if each vertex in the graph is connected.  It has only one component otherwise $G$ is **disconnected**
	* (*Theorem*) If $G$ is simple, then $G$ and $\bar{G}$ cannot both be disconnected

# Vertex Subsets
* A **clique** of $G$ is a set of pairwise adjacent vertices. More formally let $C$ be a clique of $G$. Then: 
  $$
  \forall x,y\in C, x\ne y\iff xy\in E(G)
  $$
* An **independent set** of the graph $G$ is a set of pairwise non-adjacent vertices. More formally, the following holds for independent set $S$
    
    $$
    \forall x,y\in S, xy \notin E(G)
    $$
* A **neighborhood** of a vertex $x$ is the set of all vertices that are adjacent to $x$. This is denoted as $\phi(x)$. 
  
  We can generalize it to a set of vertices $A$. The neighborhood of $A$, denoted $\phi(A)$ is the set of all vertices that are adjacent to a vertex in $A$.

# Connectivity
### Vertices
* A **separating set** in a connected graph $G$ is a set of vertices whose deletion disconnects $G$.
	* In general it is the set of vertices that increase the number of components by $1$.
* A **cut vertex** is a separating set with only one element.

* If $G$ is connected, its **vertex connectivity**, denoted $\kappa(G)$ is the size of the smallest separating set in $G$.
  
  It is the minimum number of vertices we need to delete to disconnect $G$.
  
  If $\kappa(G)=n$, we say the graph is **$n$-connected**

### Edges
*  **Disconnecting set** in a connected graph $G$ is a set of edges whose removal disconnects $G$. 
	* In general, a disconnecting set increases the number of components.
* A **cut-set** is a disconnecting set such that no proper subset of it is a disconnecting set.
	* (*Wilson e5.11b*) If two distinct cut-sets of $G$ contain an edge $e$, then $G$ has a cut-set that does not contain $e$  [^2]

[^2]: Each cut set partitions the graph into $S_1,T_1$ and $S_2,T_2$ respectively. Clearly $S_1\cap T_2$ and $T_2\cap S_1$ cannot be empty (show this is true). The cut-set $S_1\cap T_2$ and $T_2\cap S_1$ whichever is non-empty is the one we desire. Demonstrate $e$ cannot be in this cut-set either 

* A **bridge** is a cut-set with only one edge.
	* (*Theorem*): If $e$ is a bridge, then it appears in every [[Trees|spanning forest]]. 
		* If it didn't then the spanning forest would not be able to cover all vertices since removing it disconnects the graph.

* Let $G$ be a connected graph. The **edge connectivity** of $G$, denoted $\lambda(G)$ is the size of the smallest cut-set in $G$.
  
  It is the minimum number of edges we need to delete to disconnect $G$. 
  
  If $\lambda(G) = k$, we say that $G$ is **$k$-edge connected**

### General Connectivity
* (*Bondy and Murty 3.1*) **Connectivity Inequality**  If $G$ is a connected graph, then 
$$
\kappa(G) \le \lambda(G) \le \delta (G)
$$

* Graphs $G$ and $H$ are **disjoint** if they have no vertices in common 
* Graphs $G$ and $H$ are **edge disjoint** if they have no edges in common

# Biconnectivity and Blocks
* A graph is **biconnected** if it is $2$-connected
* A connected graph that has no cut vertices is called a **block**.
* A **biconnected component** is a maximal biconnected subgraph.

* (*Bondy and Murty 3.2.1*) In a biconnected graph, any two distinct vertices lie in a common cycle.
* (*Bondy and Murty 3.2.2*) If $G$ is a block with $|V(G)|\ge 3$, then any two edges of $G$ lie on a common cycle.
* **Whitney's Theorem** A graph $G$ with $|V(G)|\ge 3$ is biconnected if and only if two vertices of $G$ are connected by at least two internally disjoint paths.

# Links
* [[Fundamental Constructs in Graph Theory]]
* [[Families of Graphs]]
* [[Operations on Graphs]]