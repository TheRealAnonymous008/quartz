# Components
* A **component** of a graph is a maximally connected subgraph of the particular graph. That is, we cannot add any more vertices and edges to the subgraph. The number of components is denoted $\omega(G)$
	* (*Component-Edge Inequality*, *Wilson 5.2*) - Let $G$ be a simple graph with $n$ vertices. If $G$ has $k$ components, then the number of edges $m$ satisfies:
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
	* Adjacency is a special case of connectivity.

* A graph is **connected** if each vertex in the graph is connected.  It has only one component otherwise $G$ is **disconnected**
	* (*Mesbahi e2.12*) If $G$ is simple, then $G$ and $\bar{G}$ cannot both be disconnected.  

# Vertex Subsets
* A **clique** of $G$ is a set of pairwise adjacent vertices. More formally let $C$ be a clique of $G$. Then: 
  $$
  \forall x,y\in C, x\ne y\iff xy\in E(G)
  $$
* An **independent set** of the graph $G$ is a set of pairwise non-adjacent vertices. More formally, the following holds for independent set $S$
    
    $$
    \forall x,y\in S, xy \notin E(G)
    $$
* Let $G=(V,E)$ and $S\subseteq V(G)$. The induced subgraph denoted $\partial G[S]$ is defined as 
  $$
  \begin{split}
  \partial S &= \set{v_i \in V \mid v_i \notin S \wedge \exists v_j \in S \text{ s.t } v_iv_j \in E} \\
  \partial G[S] &= (\partial S, \set{v_iv_j \in E \mid v_i, v_j \in \partial S})
  \end{split}
  $$
  That is, it is the induced subgraph whose vertices are adjacent to some vertex in $S$ but are not in $S$.  We call $\partial S$ the **(outer) boundary** of $S$ or **neighborhood** of $S$. If $S=\set{x}$ then we simply denote the neighborhood by $\phi(x)$
  
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

* The **closure** of $G[S]$ is defined as the union between $G[S]$ and its boundary
  $$
  \text{cl} (G[S]) = G[S] \cup \partial G[S]
  $$
  Similarly, the closure of $S$ can be defined as
  $$
  \text{cl}(S) = S\cup \partial S
  $$
  For convenience, we will use the notation
  $$
  \overline{S} = \overline{\text{cl}(S)}
  $$


# Topics
* [[Vertex Connectivity]]
* [[Edge Connectivity]]


# General Connectivity
* (*Bondy and Murty 3.1*) **Connectivity Inequality**  If $G$ is a connected graph, then
  $$
  \kappa(G) \le \lambda(G) \le \delta (G)
  $$
  In fact, we can analyze this inequality using [[Graph Laplacian|the Laplacian]]

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
* [[Introduction To Graph Theory by Wilson]]
* [[Graph Theory With Applications by Bondy and Murty]]


* [[Fundamental Constructs of Graph Theory]]
* [[Operations on Graphs]]