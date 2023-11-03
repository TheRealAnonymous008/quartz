* An **infinite graph** $G$ consists of an infinite set $V(G)$ of vertices and an infinite family $E(G)$ of edges.
* A **countable graph** is an infinite graph where both the edge set and the vertex set are countable.

* A **locally countable graph** is an infinite graph where the degree of each vertex is countable. 
	* That is, the set of edges incident to any vertex $v$ is a countable set.
* A **locally finite graph** is an infinite graph where the degree of each vertex is finite. 
	* That is, the set of edges incident to any vertex $v$ is finite.

* (*Wilson 16.1*) Every connected locally countable infinite graph is a countable graph
* (*Wilson 16.2*) Every connected locally finite graph is a countable graph.
* (*Wilson 16.4*) If $G$ is a countable graph, every finite subgraph of which is [[Graph Planarity|planar]], then $G$ is planar.
# Traversals
* A **one-way infinite walk** is of the form 
  $$
  v_0, e_1, v_1, e_2, \dots
  $$
  such that of $v_0, v_1, \dots \in V$ and $e_1, e_2, \dots \in E$ and each edge is incident to the vertices to its left and right in the sequence (i.e., $e_1=v_0v_1$).

* A **two-way infinite walk** is of the form 
  $$
  \dots,v_{-1},e_{-1},v_0, e_1, v_1, e_2, \dots
  $$
   such that of $\dots, v_0, \dots \in V$ and $\dots, e_{-1}, e_1, \dots \in E$ and each edge is incident to the vertices to its left and right in the sequence (i.e., $e_1=v_0v_1$).
* An **Eulerian Line** generalizes Eulerian trails to infinite graphs. It is a two-way infinite path that traverses each edge.

* An **Eulerian Infinite Graph** is an infinite graph wherein there exists an Eulerian Line in the graph

* **Konig's Infinity Lemma** 
  
  Let $G$ be a connected locally finite infinite graph.
  
  For any vertex $v\in V(G)$, there exists a one-way infinite path with initial vertex $v$
  * For each vertex $z\ne v$, there is a non-trivial $v,z$-path. It follows there are infinitely many paths in $G$ with initial vertex $v$. 
    
    Since the degree of $v$ is finite, infinitely many of these paths must start with the same edge. If $vv_1$ is such an edge, then we can repeat the procedure to get the one-way infinite path we want 
    $$
    v\to v_1 \to v+2 \to \dots
    $$

* (*Wilson 16.4, Wilson 16.6*) Let $G$ be a connected countable graph. $G$ is Eulerian if and only if all of the following hold.
  
  1. $G$ has no vertices of odd degree.
  2. For each finite subgraph $H\subset G$, the infinite graph $K$ obtained by performing the edge division $G-E(H)$ has at most two infinite connected components
  3. If, in addition, each vertex of $H$ has even degree, then $H$ has exactly one infinite connected component.


# Links
* [[Fundamental Constructs in Graph Theory]]
* [[Trails, Walks, Paths and Cycles]]