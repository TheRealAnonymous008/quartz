# Distance-Bassed
* The **distance** between vertices $u,v$ is defined as the length of the shortest path from $u$ to $v$.

* The **diameter** of a graph, denoted $d_{\text{max}}$ is the length of the longest shortest path in a graph. 
  
  $$
  d_\text{max} = \max_{u,v\in V^2} d (u,v)
  $$
  
  We may calculate it [[Graph Algorithms|algorithmically]] using BFS.

* The **center** of $G$ is a vertex with the property that the maximum distance between $v$ and any other vertex is as small as possible. That is it satisfies
  
  $$
  \underset{v\in V(G)}{\text{argmin}}\max_{u\in V(G), u\ne v} d(u,v)
  $$

# Centrality
* The **centrality** of a vertex in a given graph is a function $f:V\to\mathbb{R}$ that captures the vertex's "importance".

* The **Betweenness Centrality** is a measure based on shortest paths.
  
  Let
  $\sigma_{st}$ is the total number of shortest paths from $s$ to $t$
  $\sigma_{st}(v)$ is the number of those paths that have $v$ as an internal vertex.
  
  Then 
  $$
  g(v)=\sum_{s\ne v \ne t} \frac{\sigma_{st}(v)}{\sigma_st}
  $$
  
  We usually normalize to obtain a proper ranking independent of the number of nodes
  
  $$
  \text{normal}(g(v))=\frac{g(v)-\min g}{\max g - \min g}
  $$

* The **Link Betweenness Centrality** is similar to the betweenness centrality except it is based on internal edges.
  
  Let 
  $\sigma_{st}$ is the total number of shortest paths from $s$ to $t$
  $\sigma_{st}(e)$ is the number of those paths that have $e$ as an internal edge in the path.
  
  $$
  g(v)=\sum_{s\ne  t} \frac{\sigma_{st}(e)}{\sigma_st}
  $$
  
  We usually perform normalization to obtain a proper ranking
  
  $$
  \text{normal}(g(e))=\frac{g(e)-\min g}{\max g - \min g}
  $$
# Density and Disjointedness
* The **density** of a graph is the ratio of the number of edges with respect to the maximum number of edges. We denote this with $D$ , $D(G)$
	* For undirected simple graphs, we have 
	  
	  $$
	  D = \frac{2|E|}{|V|(|V|-1)}
	  $$
	  * For directed graphs, we have 
	    
	    $$
	    D = \frac{|E|}{|V|(|V|-1)}
	    $$
	* A graph is **dense** if its density is as close to $1$ [^1]. Otherwise it is **sparse**

[^1]: The definition of "closeness" is arbitrary.

* The **[[Clustering]] coefficient** is a quantity which captures the extent in which neighbors $v$ form a clique.
  
  Let $L$ be the number of edges between $d$ and neighbors of $v$. 
  
  The clustering coefficient is calculated as 
  
  $$
  C_v=\frac{2L}{d(d-1)}
  $$
  It should be noted that $0\le C_v\le 1$


# Links
* [[Fundamental Constructs in Graph Theory]]
* [[Trails, Walks, Paths and Cycles]]