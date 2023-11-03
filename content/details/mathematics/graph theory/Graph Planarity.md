* A **planar graph** is an undirected graph that can be drawn in the plane in such a way that no two edges intersect except at a common vertex. The drawing is called a **Plane Graph**
	* A **map** is a $3$-connected plane graph.
* The plane graph will divide the plane into regions called **faces**. The unbounded region on the exterior of the plane graph is called the **infinite face**.

* The **crossing number** of $G$, denoted $\text{cr}(G)$ is the minimum number of crossings that can occur when $G$ is drawn in the plane
* The **thickness** of a graph is the number of planar graphs such that the union of these planar graphs is $G$. This is denoted $t(G)$

* A graph is **outerplanar** if it can be drawn in the plane so that all vertices lie on the exterior boundary.

# Topological Extensions
* A graph is of **genus** $g$ if it can be drawn on a surface with genus $g$ but not on one of genus $g-1$
* Let $A,B$ be graphs. They are **homeomorphic** if they are isomorphic to each other after performing either edge subdivision or edge smoothing. That is, *they look the same when their plane graphs are drawn*. 

### Theorems
* **Ringel-Youngs Theorem** 
  
  $$
  g(K_n) = \left\lceil \frac{(n-3)(n-4)}{12} \right\rceil
  $$
* (*Wilson 14.1*) The genus of a graph does not exceed its crossing number.
* (*Wilson 14.2*) Let $G$ be a connected graph of genus $g$ with $V$ vertices, $M$ edges and $F$ faces. Then 
  
  $$
  V - E + F = 2-2g
  $$
  This is a variation of [[#Euler's Formula]]

* (*Wilson 14.3*) The genus of a simple graph of $n\ge 4$ vertices and $m$ edges satisfies
  
  $$
  g(G) \ge \left\lceil 
  \frac{m-3n}{6} + 1
  \right\rceil
  $$
* (*Wilson 14.3.z* ) If the graph has girth $r$, then the genus satisfies
   
   $$
     g(G) \ge \left\lceil 
  \frac{(r-2)m-rn}{2r} + 1
  \right\rceil
  
   $$
# Theorems
### Euler's Formula
* Let $G$ be a plane graph of a connected planar graph with 
  $V$ vertices
  $E$ edges and 
  $F$ faces.
  
  We have
  $$
  V-E+F = 2
  $$
  
* An informal way to see this: every edge either introduces a new face or joins with a lone vertex.

* (*Wilson 13.3*) Let $C$ be the number of components. Then: 
  
  $$
  V-E+F = C+1
  $$

### Fary's Theorem
* Every Planar Graph can be drawn such that all the edges in the Plane graph are line segments

### Kuratowski's Theorem
* A graph is planar if and only if it contains no subgraph that is homeomorphic to either $K_5$ or $K_{3,3}$
* **Outerplanar Extension** a graph is outerplanar if and only if $G$ contains no subgraph homeomorphic or edge contractible to $K_4$ or $K_{2,3}$.

* (*Wilson 12.3*) A graph is planar if and only if it contains no subgraph contractible to either $K_5$ or $K_{3,3}$

### Other Theorems
* (*Wilson 13.4a*) If $G$ is a connected simple planar graph with $V\ge 3$ vertices and $E$ edges, then $E\le 3V-6$
* (*Wilson 13.6*) Every simple planar graph has a vertex with minimum degree $\delta\le 5$.  
* (*Wilson 13.7*) For $n\ge 3$ vertices, the thickness satisfies the following:
  
  $$
  \begin{equation} 
  \begin{split}
  t(G) &\ge \left\lceil\frac{m}{3n-6}\right\rceil \\
  t(G) &\ge \left\lfloor\frac{m+3n-7}{3n-6}\right\rfloor
  \end{split}
  \end{equation}
  $$

 * (*Wilson e13.3*) [^1] If $G$ is a connected, simple, planar graph with girth $r$, $V\ge r$ vertices and $E$ edges, then
   $$
   E\le \frac{r}{r-2}(V-2)
   $$
   
   [^1]: Same logic as *Wilson 13.4a* but observing that each face is incident to at least $r$ edges.

 * (*Wilson 15.6*) A graph is planar if and only if it has an [[Graph Duality|algebraic dual]].
 * (*Wilson 15.9*) Let $G$ be a connected, plane graph. $G$ is bipartite if and only if $G^\ast$ is [[Trails, Walks, Paths and Cycles#Eulerian Graphs|Eulerian]].

# Links
* [[Graph Duality]]
* [[Operations on Graphs]]
* [[Graph Coloring]] - one important result is the four color theorem