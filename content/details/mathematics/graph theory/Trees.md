* A **forest** is an acyclic graph.
* A **tree** is a connected, acyclic graph

* (*Wilson 9.1*) Let $T$ be a graph with $n$ vertices. The following are equivalent.
1. $T$ is a tree
2. $T$ contains no cycles and has $n-1$ edges
3. $T$ is connected and has $n-1$ edges
4. $T$ is connected and each edge is a  bridge
5. Any two vertices of $T$ are connected by exactly one path
6. $T$ contains no cycles but the addition of any new edge creates exactly one cycle.

* A **leaf** is a vertex in a forest with degree $1$.
* A tree is **rooted** if one vertex has been designated the **root**.

* Let $T$ be the spanning tree of a connected graph. The **cotree** $\overline{T}$ is defined as the subgraph obtained by 
  
  $$
  \overline{T} = G-E(T)
  $$
  
  That is the graph whose edges are not in the spanning tree.

# Theorems
* (*Wilson 9.2*) If $G$ is a forest with $n$ vertices and $k$ components, then $G$ has $n-k$ edges
* (*Wilson 9.2x*) Any tree on $n\ge 2$ vertices has at least two leaves.
* (*Wilson 9.3b*) Each cycle of $G$ has an edge in common with the cotree of $T$.
* (*Wilson 9.3b*) Each cycle of $G$ has an edge in common with $G-T$.
* (*Wilson e9.3.1*) Every tree is bipartite
* (*Wilson e9.9*) A tree has either one center or two adjacent centers [^1]

[^1]: This is based on deleting vertices starting from the leaf nodes.

* (*Wilson 33.7*) A graph $G$ splits into $k$ forests if and only if for all subgraphs $H\subseteq G$, 
  
  $$
  k\xi (H) \ge m(H)
  $$
  Where $m(H)$ is the number of edges of $H$.

# Topics
* [[Spanning Trees and Forests]]
* [[Labelled Trees]]

# Links
* [[Graph Connectivity]] - more on connectivity.
* [[Trails, Walks, Paths and Cycles]] - more on cycles.