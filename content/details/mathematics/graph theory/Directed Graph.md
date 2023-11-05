
# Tournaments and Orientability
* A **tournament** is a digraph in which any two vertices are joined by exactly one arc.
* A tournament $T$ is **irreducible** if it is impossible to split the set of vertices of $T$ into the disjoint sets $V_1,V_2$ so that each arc joining a vertex from $V_1$ and a vertex of $V_2$ is directed from $V_1$ to $V_2$.
* A tournament is **transitive** if $uv$ and $vw$ imply the existence of $uw$

* (*Wilson e23.6*) A tournament is irreducible if and only if it is strongly connected
	* *Proof*: By *Redei's Theorem* if a tournament is strongly connected, it is Hamiltonian
	  
	  If $T$ is a Hamiltonian tournament, then there is a Hamiltonian Cycle, but this means that for vertices $v, w$ we may follow the arcs in the cycle to go from $v$ to $w$ and $w$ to $v$. Since this is true for any pair of vertices, it is impossible to divide the tournament to two sets of vertices based on the definition of irreducibility.
	  
	  If $T$ is not Hamiltonian, then it is not strongly connected by *Redei's Theorem*. Now, this means that there exists two vertices $v$ and $w$ such that either there is no $v,w$-path or no $w,v$-path.
	  
	  If both do not exist, then we are done. Simply, set $V_1$ as the vertices reachable from $v$ and  $V_2$ as the vertices reachable from $w$ and they clearly cannot meet from our stipulations.
	  
	  If say one does exist (assume the $v,w-$path), we may still perform the same partition where $V_1$ contains the vertices reachable from $v$ except for $w$. Then, aside from $w$, another vertex must be in $V_2$ that s connected to $w$ but not to $v$ as otherwise, we would have a strongly connected tournament.

* A digraph is **strongly connected** if for any two vertices, there is a path from $u$ to $v$ and from $v$ to $u$

* Let $G$ be an undirected graph. An **orientation** of $G$ is an assignment of a direction to each edge to $G$ to produce a digraph.
* An **oriented graph** can be seen as the result of applying an orientation. More formally, it is a graph where no two vertices are connected by symmetric arcs. That is, $u$ has an edge to $v$ implies $v$ does not have an edge to $u$.
* The **underlying graph** of a digraph is an undirected graph whose edges are the arcs of $D$ interpreted as unordered pairs.
* A **strong orientation** is an orientation that results in a strongly oriented graph.

* (*Wilson 22.1*) Let $G$ be a connected undirected graph. $G$ is strongly connected if and only if each edge is contained in at least one cycle.

# Traversals 
* An **Eulerian Trail** is a trail in a digraph which contains all arcs of the digraph 
* A connected digraph is **Eulerian** if there exists an Eulerian Trail.

* (*Wilson 23.1*) A connected graph is Eulerian if and only if for all $v$
  
  $$
  \deg^+(v) = \deg^{-}(v)
  $$
 
* **Ghouila-Houri Criterion** Let $D$ be a strongly connected digraph with $n$ vertices. If $\deg^+(v)\ge \frac{n}{2}$ and $\deg^-(v)\ge \frac{n}{2}$ for each vertex then $D$ is Hamiltonian

* (*Wilson 23.3*) **Redei's Theorem**. 
  1. Every non-Hamiltonian tournament is semi-Hamiltonian.
  2. Every strongly connected tournament is Hamiltonian.


# Link
* [[Fundamental Constructs in Graph Theory]]
* [[Trails, Walks, Paths and Cycles]] 