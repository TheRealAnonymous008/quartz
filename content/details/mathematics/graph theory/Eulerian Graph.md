* An **Eulerian Trail** is a [[Trails, Walks, Paths and Cycles|trail]] in an undirected graph that visits every edge exactly once. In a [[Directed Graph|digraph]], it contains all arcs of the digraph.
* An **Eulerian Cycle** is an Eulerian trail that starts and ends on the same vertex.
* A graph $G$ is **Eulerian** if it contains an Eulerian Cycle. For digraphs, we require the existence of a (directed) Eulerian trail.

* A graph is **Semi-Eulerian** if it contains an Eulerian trail but not an Eulerian Cycle

* (*Wilson 6.2*) **Euler's Theorem**: A connected graph $G$ is Eulerian if and only if the degree of each vertex of $G$ is even.
* (*Wilson 6.3*) A [[Graph Connectivity|connected]] graph is Eulerian if and only if its set of edges can be split into disjoint cycles.
* (*Wilson 6.4*) A connected graph is Semi-Eulerian if and only if it has exactly two vertices of odd-degree.

* (*Wilson 23.1*) A connected digraph is Eulerian if and only if for all $v$
  
  $$
  \deg^+(v) = \deg^{-}(v)
  $$
 
# Links
* [[Introduction To Graph Theory by Wilson]]
