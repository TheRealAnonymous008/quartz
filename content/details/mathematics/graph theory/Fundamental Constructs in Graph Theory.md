* Let $G=(V,E)$ be a graph. 

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
# Relations between Graphs
* An **[[Group Isomorphism|isomorphism]]** from $G$ to $H$ is a bijection $f:V(G)\to V(H)$ such that if $xy\in E(G)$ , then $f(x)f(y)\in E(H)$. 
	* We say that if an isomorphism between $G$ and $H$ exists, then the two graphs are, which we denote as $G\cong H$ .
	* Isomorphism is an equivalence class
	* *Adjacency is preserved under isomorphism*.

* Let $S\subset V$ be any subset of vertices of $G$. The **induced subgraph**, denoted $G[S]$ is the graph whose vertex set is $S$ and whose edge set consists of all the edges in $E$ that have endpoints in $S$.  More formally, for $u,v\in S$, 
  
  $u\leftrightarrow v$ in $G[S]$ if and only if $u\leftrightarrow v$ in $G$.  

* The graph $H$ is a **subgraph** of a graph $G$, denoted as $H\subseteq G$ if and only if $V(H)\subseteq V(G)$ and $E(G)\subseteq E(H)$.


* Two graphs are **disjoint** if they do not share any vertices.

# Relations in Graphs
* If $xy\in E$, we say that $x$ is **adjacent** to $y$. Denoted as $x\leftrightarrow y$. This is the **adjacency relation**.
* We say that $xy$ is **incident** to the vertices $x,y\in V$. This is the **incidence relation**. 

* We can represent the adjacency relation with a square matrix called the **adjacency matrix** denoted $A$. It is $|V| \times |V|$ and we obtain the entries as follows. 
  
  If $v_i,v_j\in V$, then $A_{ij}$ is the number of edges between $v_i$ and $v_j$ in that order.  
  
  We denote the adjacency matrix of $G$ as $A(G)$.

* The **Incidence Matrix** is an $|V|\times |E|$ matrix $B$ where: $$ {
\begin{equation}
B_{ij} = 
	\begin{cases}
		1 & \text{if } v_i \text{ is incident with } e_j\\
		0 & \text{otherwise}
	\end{cases} 
\end{equation}
}
$$We denote the incidence matrix of $G$ as $B(G)$.
