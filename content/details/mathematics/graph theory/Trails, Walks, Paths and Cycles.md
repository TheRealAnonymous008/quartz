# Basic Definitions
### Trails and Walks
* Let  $G=(V,E)$ be an undirected graph. 
  
  A **walk** in $G$ is a finite sequence of vertices and edges of the form 
  $$
  v_0, e_1, v_1, e_2, \dots e_n, v_n
  $$
   such that  $v_0, \dots, v_n \in V$ and $e_1, \dots, e_n \in E$ and each edge is incident to the vertices to its left and right in the sequence (i.e., $e_1=v_0v_1$).
   
   We do not require that each vertex and each edge is distinct from each other.
	* In the definition we call $v_0$ as the **initial vertex** and $v_n$ as the **final vertex** of the walk.
	* If the initial vertex is $u$ and the final vertex is $v$, the walk is called a **$u,v$-path**
	* The **length** of a walk refers to the number of edges in the walk.
 
* A **trail** is a walk in which all edges are distinct.
	* A $u,v$-trail is a trail which starts and ends at $u$ and $v$ respectively.

### Path
* A **path** is a graph with the following property with the following property.  
  
  We may list the vertices as  $V=\{v_1,\dots,v_n\}$ such that the only edges are of the form $(v_i, v_{i+1})$ for $i\le n-1$. 
	* A path is a trail where we also require the vertices to be distinct from each other.

* We denote the path graph on $n$ vertices as $P_n$. We call $n$ its **length**

* We say that a path $P$ is **in** a graph $G$ if $P\subseteq G$
* If the path starts with vertex $u$ and ends with $v$, such a path is called a  **$u,v$-path**

* A family of paths in a graph is **edge independent** or **edge disjoint**  if no edge of $G$ is an edge of more than one path in the family
* A family of paths in a graph is **internally disjoint** if no vertex of $G$ is an internal vertex of more than one path in the family.

* (*Wilson 28.3*) A graph is $k$-edge connected if and only if two distinct vertices of $G$ are connected by at least $k$-edge disjoint paths
* (*Wilson 28.4*) A graph with at least $k+1$ vertices is $k$-connected if and only if two distinct vertices of $G$ are connected by at least $k$ vertex disjoint paths.

### Cycle
* A **cycle** is a graph that is connected and 2-regular.
  
* A cycle is **in** a graph if $C\subseteq G$. 
	* A cycle is a trail where each vertex is distinct except for the first and last vertex.
* A cycle of $n$ vertices is denoted $C_n$. $n$ is the **length** of the cycle.

* The **girth** of an undirected graph $G$ is the length of the shortest cycle in $G$.

* *(Wilson 6.1)* If $G$ is a finite graph in which the degree of each vertex is at least $2$, then $G$ contains a cycle.
* (*Wilson e5.11a*) If two distinct cycles of a graph each contain edge $e$, then $G$ has a cycle that does not contain $e$ [^3]

[^3]: Consider the $u,v$-path that goes from $C_1$ and then the $v,u$-path in $C_2$.

# Triangles
* A **triangle-graph** is the complete graph $K_3$. 
* A graph that does not contain a triangle is **triangle-free**

* **Mantel's Theorem** [^1]  Let $G$ be triangle free. 
  
  If $V(G)=2k$, then $E(G)\le k^2$. 

* (*Wilson e5.10*): The triangle free graph with $2n$ vertices and $n^2$ edges is $K_{n,n}$. [^2]

[^1]: The proof is by induction. Given a triangle free graph, perform an edge deletion on $e=uv$to get a smaller triangle-free graph. Show we can choose at most $2n-2$ vertices to join to one of $u,v$ but not both. This implies, there are at most $2n-1$ vertices not in the smaller graph. This will completes the proof.
[^2]:  Given an edge $e=uv$, we may partition the remaining vertices into sets if they are connected to $u$ or $v$.

# Eulerian Graphs
* An **Eulerian Trail** is a trial in an undirected graph that visits every edge exactly once.
* An **Eulerian Cycle** is an Eulerian trail that starts and ends on the same vertex.
* A graph $G$ is **Eulerian** if it contains an Eulerian Cycle.
* A graph is **Semi-Eulerian** if it contains an Eulerian trail but not an Eulerian Cycle

* (*Wilson 6.2*) **Euler's Theorem**: A connected graph $G$ is Eulerian if and only if the degree of each vertex of $G$ is even.
* (*Wilson 6.3*) A connected graph is Eulerian if and only if its set of edges can be split into disjoint cycles.
* (*Wilson 6.4*) A connected graph is Semi-Eulerian if and only if it has exactly two vertices of odd-degree.

# Hamiltonian Graphs
* A **Hamiltonian Path** is a path contained within a graph such that it passes through vertex exactly once.
* A **Hamiltonian Cycle** is a cycle contained within a Graph such that it passes through each vertex exactly once.
* A **Hamiltonian Graph** is a graph which contains a Hamiltonian Cycle
* A graph is **Semi-Hamiltonian** if it contains a Hamiltonian Path but not a Hamiltonian Cycle

### Undirected
* (*Bondy and Murty 4.2*) If $G$ is Hamiltonian, then for every non-empty $S\subset V$. 
  $$
  \omega(G-S) \le |S|
  $$
* (*Bondy and Murty 4.3*) **Dirac's Theorem**. If $G$ is a graph with $n\ge 3$ vertices and $\delta \ge \frac{n}{2}$ then $G$ is Hamiltonian.

* *(Wilson 7.1)* **Ore's Theorem** [^2]. Let $G$ be a simple graph with $n\ge 3$ vertices. If $$\deg(v)+\deg(w)\ge n$$for each pair of non-adjacent vertices $v$ and $w$, then $G$ is Hamiltonian

[^2]: Ore's Theorem generalizes Dirac's Theorem

### Directed
* **Ghouila-Houri Criterion** Let $D$ be a strongly connected digraph with $n$ vertices. If $\text{outdeg}(v)\ge \frac{n}{2}$ and $\text{indeg}(2)\ge \frac{n}{2}$ for each vertex then $D$ is Hamiltonian

# Links
* [[Graph Connectivity]]
* [[Families of Graphs]]
* [[Directed Graph]]