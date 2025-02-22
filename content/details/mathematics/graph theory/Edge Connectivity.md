*  A **Disconnecting set** in a connected graph $G$ is a set of edges whose removal disconnects $G$. 
	* In general, a disconnecting set increases the number of components.
* A **cut-set** is a disconnecting set such that no proper subset of it is a disconnecting set.
	* (*Wilson e5.11b*) If two distinct cut-sets of $G$ contain an edge $e$, then $G$ has a cut-set that does not contain $e$  [^2]

[^2]: Each cut set partitions the graph into $S_1,T_1$ and $S_2,T_2$ respectively. Clearly $S_1\cap T_2$ and $T_2\cap S_1$ cannot be empty (show this is true). The cut-set $S_1\cap T_2$ and $T_2\cap S_1$ whichever is non-empty is the one we desire. Demonstrate $e$ cannot be in this cut-set either 

* A **bridge** is a cut-set with only one edge.
	* (*Theorem*): If $e$ is a bridge, then it appears in every [[Tree|spanning forest]]. 
		* If it didn't then the spanning forest would not be able to cover all vertices since removing it disconnects the graph.

* Let $G$ be a connected graph. The **edge connectivity** of $G$, denoted $\lambda(G)$ is the size of the smallest cut-set in $G$.
  
  It is the minimum number of edges we need to delete to disconnect $G$. 
  
  If $\lambda(G) = k$, we say that $G$ is **$k$-edge connected**


* (*Wilson 28.1*) **Menger's Theorem (Edge Version)** - the maximum number of edge-independent paths connecting two distinct vertices $v$ and $w$ of a connected graph is equal to the minimum number of edges in a $v,w$-[[Edge Connectivity|edge cut]].

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
		  |\partial_e (A\cup B) | + |\partial _e(A\cap B)| \le 2 \lambda (X)
		  $$
		  But also
		  $$
		  |\partial_e (A\cup B) | = |\partial_e (A\cap B)| = \lambda (X)
		  $$
		  But this is impossible since $\emptyset \ne A\cap B\subset A$ which contradicts the fact that $\lambda(X)=|\partial_e (A\cap B)| < |A|=\lambda(X)$ so $A\cap B = \emptyset$ 
# Links
* [[Introduction To Graph Theory by Wilson]]
* [[Algebraic Graph Theory by Godsil and Royle]]

* [[Fundamental Constructs of Graph Theory]]
* [[Operations on Graphs]]
* [[Vertex Connectivity]]