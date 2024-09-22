---
aliases:
  - graph
---

* For the following, let $G=(V,E)$ be a graph. 

# Edge Types
* A **loop** is an edge whose endpoints are equal.
* **Multiple Edges** are edges that have the same pair of incident vertices
* A graph is **simple** if it has no loops or multiple edges.

* A graph is **undirected** if $xy\in E(G)$, then so is $yx\in E(G)$. 
  
  That is, we do not distinguish between the order of vertices listed in each edge. Otherwise, if there is a notion of direction, we say the graph is **directed**.
	* For directed graphs, we refer to edges as **arcs** and the **arc set** is notated $A(D)$

* A graph is **weighted** wherein each edge is assigned a value called its **weight**. 
  
  We may denote the weight of an edge $e\in E(G)$ as $w(e)$. 
  
  We may also denote the weight of a weighted graph as $w(G)$, that is the sum of weights of all its edges 
  
  $$
  w(G)=\sum_{e\in E(G)}w(e)
  $$
# Vertices
* If $xy\in E$, we say that $x$ is **adjacent** to $y$. Denoted as $x\leftrightarrow y$. This is the **adjacency relation**.
* We say that $xy$ is **incident** to the vertices $x,y\in V$. This is the **incidence relation**. 
* The **degree** of a vertex $v\in V$ denotes the number of edges that are incident to it. This is denoted $\deg(v)$
	* The minimum degree is denoted $\delta(G)$
	* The maximum degree is denoted $\Delta(G)$
* For a directed graph, we have: 
	* The **out-degree** of a vertex $v$ as the number of arcs coming from $v$ (that is, arcs of the form $vu$). This is denoted $\deg^+$
	* The **in-degree** of $v$ as the number of arcs coming to $v$ (that is, arcs of the form $uv$). This is denoted $\deg^-$
	* The **degree** of a vertex in the digraph is the number of arcs incident to it. It is therefore calculated as 

$$
\deg (v) = \text{deg}^-(v) + \text{deg}^+(v)
$$
* Let $G$ be an undirected graph. A **degree sequence** is a monotonic non-increasing sequence of the vertex degrees of its graph vertices.

* **Handshaking Lemma**. In an undirected graph, there must exist an even number of odd degree vertices.

* **Degree Sum Formula (Undirected)**
  
  $$
  \sum_{v\in V} \deg v = 2|E|
  $$

* **Degree Sum Formula (Directed)**
  
  $$
  \sum_{v\in V} \deg^{-}(v) = \sum_{v\in V} \deg^{+}(v) = |E|
  $$

# Relations between Graphs
* An **[[Group Isomorphism|isomorphism]]** from $G$ to $H$ is a bijection $f:V(G)\to V(H)$ such that if $xy\in E(G)$ , then $f(x)f(y)\in E(H)$. 
	* We say that if an isomorphism between $G$ and $H$ exists, then the two graphs are **isomorphic**, which we denote as $G\cong H$ .
	* Isomorphism is an equivalence class
	* *Adjacency is preserved under isomorphism*.

* The graph $H$ is a **subgraph** of a graph $G$, denoted as $H\subseteq G$ if and only if $V(H)\subseteq V(G)$ and $E(G)\subseteq E(H)$. We refer to $G$ as the **supergraph**
	* If $V(H) = V(G)$, we say that $H$ is a **spanning subgraph** of $G$. 

* Let $S\subset V$ be any subset of vertices of $G$. The **induced subgraph**, denoted $G[S]$ is the graph whose vertex set is $S$ and whose edge set consists of all the edges in $E$ that have endpoints in $S$.  More formally, for $u,v\in S$, 
  $$
  u\leftrightarrow v \text{ in } G[S] \iff u\leftrightarrow v \text{ in } G
  $$

* Two graphs are **disjoint** if they do not share any vertices.




* [[Matrices in Graph Theory]]

# Links
* [[Introduction To Graph Theory by Wilson]]