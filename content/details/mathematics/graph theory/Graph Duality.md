# Cycle and Cut-set

* The **cut-set rank** is the number of edges in a spanning forest of a graph $G$.  If $G$ is a graph with $n$ vertices and $k$ components, we have the cut-set rank as 
  
  $$
  \xi(G)=n-k
  $$
* The **cycle rank** of an undirected graph is the total number of edges needed to be removed so that the resulting graph is a forest. If the graph has $n$ vertices, $m$ edges and $k$ components, we have 
  $$
  \gamma(G) = m-n+k
  $$

* Let $b$ be an edge of a spanning forest. The **fundamental cut-set** with respect to $b$ is the cut-set of $G$ which contains $b$ as well as the edges
  
  $$
  xy\in E(G), x\in X, y\in Y
  $$
  Where $X$ and $Y$ are disconnected subgraphs that are produced when removing $b$. The set of fundamental cut-sets is the **fundamental set of cut-sets**

* Let $e=uv$ such that $uv\notin E(T)$. Let $P$ be the unique $u,v$-path from $u$ to $v$ on $T$. The **fundamental cycle** is formed by the addition $P+e$. 

* (*Wilson 15.3*) **Cycle Cut-Set Duality**. Let $G$ be a planar graph and $G^\ast$ its dual. Then, a set of edges in $G$ forms a cycle in $G$ if and only if the corresponding edges in $G^\ast$ forms a cut-set.

* (*Wilson 9.3a cor*) Let $C_T^*(G)$ be the fundamental set of cut-sets of $G$ associated with spanning forest $T$. We have that
  $$
  |C_T^*(G)|=\xi(G)
  $$

* (*Wilson e5.12a*) If $C$ is a cycle and $C^\ast$ is a cut-set of a connected graph $G$, then then $C$ and $C^*$ have an even number of edges in common.
	* *Proof*: 
	  This is trivially true if $C$ and $C^*$ are edge disjoint.
	  
	  Since $C^*$ is a cut-set, it must disconnect the graph. Consider any two vertices $u,v\in V(C)$. If they were separated because of the cut, then $e=uv \in E(C)$. But also, note that since $C$ is a cycle, some other $u,v$-path that does not pass through $e$ must exist and be deleted
	  
	  This applies if we consider any pair of vertices $v_i,v_{i+1}$ as listed in the cycle. Hence, there is always an even number of edges that are both in the cycle and in the cut-set. 

* (*Wilson e5.12b*) If $S$ is any set of edges in $G$ with an even number of edges in common with each cut-set of $G$, then $S$ can be split into edge-disjoint cycles
	* *Proof* Let  $H$ be the union of $S$
	  
	  We prove by contradiction  Also, without loss of generality we assume $H$ is connected otherwise we apply the same logic here to each component of $H$.
	  
	  $S$ cannot be split into edge disjoint cycles. This implies that there is at least one edge that appears in two cycles say $C_1$ and $C_2$.  Say the set of edges they have in common is $D$ and $|D|=n$
	  
	  Now for any cut-set $C^*$ that does not cut these common edges, by *Wilson e5.12a*, there must be an even number of edges shared by the cycles with $C^*$ which means there are a total of $k_1+k_2$ edges shared by $C_1\cup C_2$, and this quantity must be even by our stipulations.  Furthermore,  by *Wilson e5.11a* there must exist a cycle $C$ which does not pass through any edge in $D$ and clearly it intersects with $C^*$ in $k_1 + k_2$ edges
	  
	  But, now consider a cut-set obtained by passing through one of the edges in $D$ which is guaranteed to exist by *Wilson e5.11b*. Such a cut-set now yields $k_1 + k_2-1$ common edges with $C$ which is impossible since there must be an even number of edges shared between $C$ and $C^*$.



# Links
* [[Trails, Walks, Paths and Cycles]]
* [[Graph Planarity]]
* [[Trees]]
* [[Matroids]]