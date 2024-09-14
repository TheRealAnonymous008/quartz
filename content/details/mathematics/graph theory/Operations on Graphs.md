* We can usually use these operations to produce a proof by induction. 
# Graph Operations
* The **complement** of $G$, denoted $\overline{G}$ is a graph such that $V(G)=V(\overline{G})$  and the following holds: 
  $$
  e\in E(G)\iff e \notin E(\overline{G})
  $$
	* The complements of two isomorphic graphs are isomorphic. That is 
	  $$
	  G\cong H \iff \overline{G} \cong \overline{H}
	  $$
	  

* The **Union** of $G$ and $H$, denoted $G\cup H$ is the graph where 
  $$
  \begin{equation}
  \begin{split}
  V(G\cup H) &=V(G)\cup V(H) \\
  E(G\cup H) &=E(G)\cup E(H)
  \end{split}
  \end{equation}
  $$
* The **Intersection** of $G$ and $H$, denoted $G\cap H$ is the graph where
  $$
  \begin{split}
  V(G\cap H) &= V(G) \cap V(H) \\
  E(G\cap H) &= E(G) \cap E(H) 
  \end{split} 
  $$
* Let $G=(V,E)$ and $S\subseteq V(G)$. The **boundary** of the induced subgraph is denoted $\partial G[S]$ is [[Real Analysis|defined]] as 
  $$
  \begin{split}
  \partial S &= \set{v_i \in V \mid v_i \notin S \wedge \exists v_j \in S \text{ s.t } v_iv_j \in E} \\
  \partial G[S] &= (\partial S, \set{v_iv_j \in E \mid v_i, v_j \in \partial S})
  \end{split}
  $$
  That is, it is the induced subgraph whose vertices are adjacent to some vertex in $S$ but are not in $S$. 
* The **closure** of $G[S]$ is defined as the union between $G[S]$ and its boundary
  $$
  \text{cl} (G[S]) = G[S] \cup \partial G[S]
  $$

* A **graph decomposition** is a list of edge-disjoint subgraphs. That is, if we have $H_1,\dots, H_k\subseteq G$ such that each $H_1,\dots, H_k$ are pairwise disjoint, then 
  $$
  G= G[H_1\cup H_2 \cup\dots\cup H_k]
  $$
  We denote this by saying
  $$
  G=H_1\oplus H_2 \oplus \dots \oplus H_k
  $$
  analogous to [[Vector Sum and Direct Sum|direct sums]] 

* [[Cartesian Product of Graphs]]

# Edge Operations
### Edge Addition
* Let $G$ be a graph and $F$ a set of edges. The graph obtained from **edge addition** is denoted $G+F$ and is the graph where all edges in $F$ are added to $G$.
  
$$
E(F+G) = F\cup E(G)
$$

* If $F$ is singleton $\{e\}$ we denote this as $G+e$
* *Edge addition cannot increase the number of [[Graph Connectivity|components]]*.
	* Intuitively, this follows from the fact that adding an edge may connect two components together or it may not. In either case, we do not create any new components as a result.
### Edge Contraction
* An **Edge Contraction** is an operation that removes an edge $e=uv\in E(G)$  while simultaneously merging $u$ and $v$ into a new vertex $w$ which is incident  to all edges that were previously incident to either $u$ or $v$ 
* The resulting graph is notated as $G/e$. We say that $G$ is **contractible** to $G/e$ 

### Edge Deletion
* If $F\subseteq E(G)$, then **edge deletion** is  the operation of removing all edges in $F$ from $G$. This is denoted $G-F$
* If $F=\{e\}$ is singleton, then we denote this as $G-e$

### Edge Smoothing
* **Edge Smoothing** is an operation on edges  Consider a [[Trails, Walks, Paths and Cycles|path contained]] in graph $P=u\to w\to v$ , where $w$ is adjacent to no other vertex.
  
  Delete vertex $w$ and connect $u$ and $v$. Essentially, replace $P$ with the edge $uv$.
  
  More succinctly, it is the reverse operation of [[#Edge Subdivision]]

### Edge Subdivision
* Let $e=uv$ be an edge of $G$. **Edge subdivision** involves deleting this edge and replacing it with a path of length $2$ by adding new edges $uw, wv$.

# Vertex Operations
* Let $F\subseteq V(G)$. The graph obtained from **vertex deletion** is denoted as $G-F$ and is the graph with all vertices and all incident edges from vertices in $F$ removed from $G$.
  
  If $F$ is a singleton $\{v\}$, we similarly denote the vertex deletion as $G-v$.

# Links
* [[Fundamental Constructs of Graph Theory]]