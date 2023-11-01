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

* A **graph decomposition** is a list of edge-disjoint subgraphs.

* Let $G,H$ be disjoint graphs.
# Edge Operations
### Edge Addition
* Let $G$ be a graph and $F$ a set of edges. The graph obtained from **edge addition** is denoted $G+F$ and is the graph where all edges in $F$ are added to $G$.
  
$$
E(F+G) = F\cup E(G)
$$

* If $F$ is singleton $\{e\}$ we denote this as $G+e$
* *Edge addition cannot increase the number of [[Graph Connectivity|components]]*.
	* Intuitively, this follows from the fact that adding an edge may connect two components together or it may not. In either case, we do not create any new components as a result.

* The **Union** of $G$ and $H$, denoted $G\cup H$ is the graph where 
$$
\begin{equation}
\begin{split}
V(G\cup H) &=V(G)\cup V(H) \\
E(G\cup H) &=E(G)\cup E(H)
\end{split}
\end{equation}
$$
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
* [[Fundamental Constructs in Graph Theory]]