* Let $G$ be a connected graph. A **spanning tree** is a tree contained in $G$ such that it includes all the vertices of $G$.

* A **spanning forest** is a collection of spanning trees
* (*Wilson 9.3*) Let $T$ be a spanning forest of a connected graph. Each cycle of $G$ contains an edge in common with the cotree $\overline T$
* (*Wilson 9.3a*) Let $T$ be a spanning forest. Each cut-set of $G$ has an edge in common with $T$
* (*Wilson 9.3a.z*) Let $T$ be a spanning tree of a connected graph. Each cut-set of $G$ contains an edge in common with $T$.
* (*Wilson 9.3x*) Every edge $e\in E(G)$ is included in some spanning forest of $G$.
* (*Wilson e9.10a*) - Let $C^\ast$ be a set of edges of a graph $G$. If $C^\ast$ has an edge in common with each spanning forest, then $C^\ast$ contains a cut-set [^1]

[^1]: Performing an edge deletion $G-C^\ast$ by definition will disconnect $G$. It follows, there must be a minimal set in $C^\ast$ which is out cut-set.

* (*Wilson 33.5*) A graph $G$ contains $k$ edge-disjoint spanning forests if and only if for each subgraph $H\subseteq G$ 
  $$
  k\left(\xi(G)-\xi(H)\right)\le m(G)-m(H)
  $$
  where $m(G)$ and $m(H)$ denote the number of edges of $G$ and $H$ respectively

# Minimum Spanning Forest
* Let $G$ be a connected weighted graph. A **Minimum Spanning Tree** is a spanning tree wherein the total weight of all the edges in the spanning tree is minimized.

* Let $G$ be a weighted graph. The **Minimum Spanning Forest** is a spanning forest wherein the total weight of all the edges included in the spanning forest is minimized.

* **MST Cut Property** - for any cut-set $C$, if the weight of an edge $e\in E(C)$ is strictly smaller than the weights of all other edges in $C$, then this edge belongs to an MST of the graph.
	* *Proof*: Suppose there is an MST $T$ that does not include $e$. Adding $e$ will produce a cycle that contains some other edge $e'\in E(T)$. By the hypothesis
	  
	  $$
	  w(e) < w(e')
	  $$
	  
	  Clearly, $T-e'+e$ is another MST but it will have smaller weight.

* **MST Cycle Property** - For any cycle $C$ in the graph, if the weight of an edge $e$ of $C$ is larger than any of the individual weights of all other edges of $C$, then this edge is not in the MST.
	* *Proof*: Let $e$ be some MST in $T$. 
	  
	  Now, performing the deletion $T-e$ yields two subtrees so that the two ends of $e$ are now in different subtrees.
	  
	  Form $T'$ as follows. Add some other edge $e'\in E(C)$  $e'\ne e$ so that 
	  $$
	  T'=T-e+e'
	  $$
	  
	  But we know by the theorem $w(e)> w(e')$, so $T'$ is a spanning tree and 
	  $$
	  w(T')=w(T)-w(e)+w(e')<w(T)
	  $$
	  which is a contradiction.

* **MST Uniqueness** - Let $G$ be a Graph with each edge having a distinct weight, there will be one and only one unique minimum spanning tree.
	* *Proof*: We do a proof by contradiction. Suppose there are in fact two MSTs, $A$ and $B$ that are distinct.
	  
	  Since $A$ and $B$ are distinct, there must be at least 1 edge that is in one but not the other. Say $a\in E(A), a\notin E(B)$.
	  
	  Since $B$ is a spanning tree, adding $a$ to $B$ introduces some cycle $C$ with $a$
	  
	  Now $A$ has no cycles so there exists an edge in $C$ and by extension $B$, that is not in $A$. Call this edge $b\in E(B)$
	  
	  Now, in $B$ replace edge $b$ with edge $a$. Clearly $w(a)<w(b)$ so $w(B-b+a)<w(B)$ which is a contradiction since $B$ was an MST.

* We can find the MST using [[Graph Algorithms#Kruskal's Algorithm|Kruskal's algorithm]]
# Links
* [[Trees]]
* [[Matroid Theory]]