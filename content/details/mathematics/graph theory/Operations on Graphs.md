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


## Boundaries 
* Let $G=(V,E)$ and $S\subseteq V(G)$. The induced subgraph denoted $\partial G[S]$ is [[Real Analysis|defined]] as 
  $$
  \begin{split}
  \partial S &= \set{v_i \in V \mid v_i \notin S \wedge \exists v_j \in S \text{ s.t } v_iv_j \in E} \\
  \partial G[S] &= (\partial S, \set{v_iv_j \in E \mid v_i, v_j \in \partial S})
  \end{split}
  $$
  That is, it is the induced subgraph whose vertices are adjacent to some vertex in $S$ but are not in $S$.  We call $\partial S$ as the **(outer) boundary** of $S$. 
  
  We can similarly define the **edge boundary** of the induced subgraph denoted $\partial_eS$ defined as
  $$\partial_e S = \set{xy\in E \mid |S\cap \set{x,y}| = 1}
  $$
  That is, it is the set of edges where one endpoint is in $S$ and the other is not. 
	* (*Godsil 3.3.1*) Let $A,B\subseteq V(G)$, then
	  $$
	  |\partial_e(A\cup B) | + |\partial_e(A\cap B) | \le |\partial_eA| + |\partial_eB|
	  $$
		* *Proof*:  Let $E(A,B)$ be the set of edges $xy$ such that $x\in A$ and $y\in B$.  Let us find the quantity $E(A-B,B-A)$. 
		  
		  For each term in the inequality, we can express them as follows. The last term in the fourth equation below is negative to account for double counting.
		  $$
		  \begin{split}
		  |\partial_e A| &= E(A\cap B,B-A) + E(A-B,B-A) + E(A, \overline A -B) \\
		  |\partial_eB| &= E(A\cap B, A-B) + E(B-A,A-B) + E(B,\overline B-A) \\
		  |\partial_e(A\cap B)| &= E(A\cap B, A-B)+ E(A\cap B, B-A) + E(A\cap B, \overline{A\cup B}) \\
		  |\partial_e (A\cup B) | &= E(A,\overline A - B) + E(B,\overline B - A) - E(A\cap B, \overline {A\cup B})
		  \end{split}
		  $$
		  And so we have
		  $$
		  \begin{split}
		  0 & \le E(A-B,B-A) + E(B-A,A-B) \\ &=2E(A-B,B-A) \\ &= |\partial_e A|+|\partial_e B| - |\partial_e(A\cap B)| - |\partial_e (A\cup B)|
		  \end{split}
		  $$
		  
		  
* An **edge atom** of a graph is  defined as $S\subseteq V(G)$ such that 
  $$
  |\partial_eS| = \lambda (G)
  $$
	* (*Godsil 3.3.2*) Any two distinct edge atoms are vertex disjoint
		* *Proof*: Let $A, B$ be two distinct edge atoms of $X$. If $A\cup B = V(X)$, then since neither $A$ nor $B$ contain more than half the vertices of $X$, we have
		  $$
		  |A| = |B| =\frac{1}{2}|V(X)|
		  $$
		  Hence $A\cap B=\emptyset$.  
		  
		  Consider the other case, $A\cup B\subset V(X)$. By (*Godsil 3.3.1*) 
		  $$
		  |\partial (A\cup B) | + \partial |(A\cap B)| \le 2 \lambda (X)
		  $$
		  But also
		  $$
		  |\partial (A\cup B) | = |\partial (A\cap B)| = \lambda (X)
		  $$
		  But this is impossible since $\emptyset \ne A\cap B\subset A$ so $A\cap B = \emptyset$ 

* The **closure** of $G[S]$ is defined as the union between $G[S]$ and its boundary
  $$
  \text{cl} (G[S]) = G[S] \cup \partial G[S]
  $$
  Similarly, the closure of $S$ can be defined as
  $$
  \text{cl}(S) = S\cup \partial S
  $$


* A **fragment** of graph $G$ is a subset $A\subseteq V$ such that $\overline {\text{cl}(A)}\ne \emptyset$ and $|\partial A|=\kappa(G)$. An **atom** of $G$ is a fragment that contains the minimum number of vertices (it must  be connected).
	* For any fragment $A\subseteq S$
	  $$
	  |\partial A| =  |\partial  \ \overline{\text{cl(A)}}|
	  $$
	* (*Godsil 3.4.3*) Let $A,B$ be fragments of $X$. Then
		* $\text{cl}(A\cap B)\subseteq (A\cap \text{cl}(B)) \cup (\text{cl}(A)\cap B) \cup (\text{cl}(A)\cap \text{cl}(B))$
		* $\text{cl}(A\cup B) = (\overline A \cap \text{cl}(B))\cup (\text{cl}(A) \cap \overline B) \cup (\text{cl}(A)\cap \text{cl}(B))$
		* $\overline{\text{cl}(A)} \cup \overline{\text{cl}(B)} \subseteq \overline{\text{cl}(A\cap B)}$
		* $\overline{\text{cl}(A\cup B)} = \overline{\text{cl}(A)} \cap \overline{\text{cl}(B)}$
	* (*Godsil 3.4.4*) Let $X$ be a graph on $n$ vertices with connectivity $\kappa$. Suppose $A,B$ are disjoint fragments of $X$. If $|A|\le |\overline{\text{cl}(B)}|$ then $A\cap B$ is a fragment. 
	* (*Godsil 3.4.5*) If $A$ is an atom and $B$ a fragment of $X$ then $A$ is a subset of exactly one of $B, \text{cl}(B)$ and $\overline{\text{cl}(B)}$
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
* [[Algebraic Graph Theory by Godsil and Royle]]