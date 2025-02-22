* A **separating set** also called a **vertex cut**, in a connected graph $G$ is a set of vertices whose deletion disconnects $G$.
	* In general it is the set of vertices that increase the number of components by $1$.
* A **cut vertex** is a separating set with only one element.

* If $G$ is connected, its **vertex connectivity**, denoted $\kappa(G)$ is the size of the smallest separating set in $G$.
  
  It is the minimum number of vertices we need to delete to disconnect $G$.
  
  If $\kappa(G)=n$, we say the graph is **$n$-connected**

# Menger's Theorem 
* Can be thought of as a special case of the [[Flow Network|Max-Flow Min-Cut]] Theorem. 
	* *Intuition*: Consider a weighted graph. For each edge with weight $w$, incident to $u,v$ delete it and create $w$ new edges.  Edge independent / Vertex independent paths now correspond flows in this flow network, while Edge / Vertex cuts now correspond to cuts in the flow network. 
* (*Wilson 28.1*) **Menger's Theorem (Vertex Version)** - the maximum number of vertex disjoint paths connected two distinct vertices $v$ and $w$ of a connected graph is equal to the minimum number of edges in a $v,w$-[[Vertex Connectivity|vertex cut]].
* (*Wilson 28.6*) **Menger's Theorem implies [[Graph Matching|Hall's Theorem]]**


* (*Wilson 28.3*) - A graph is $k$-connected if and only if any two distinct vertices of $G$ are connected by at least $k$-edge disjoint paths 
	* *Proof*: Follows from Menger's Theorem

* (*Wilson 28.4*) - A graph with at least  $k+1$ vertices is $k$-connected if and only if any two distinct vertices of $G$ are connected by at least $k$-vertex disjoint paths 
	* *Proof*: Follows from Menger's Theorem

* (*Wilson 28.5*) The maximum number of arc-disjoint paths from $v$ to $w$ in a [[Directed Graph|digraph]] is equal to the minimum number of arcs in a $vw$-[[Edge Connectivity|disconnecting set]]. 

# Fragments and Atoms
* A **fragment** of graph $G$ is a subset $A\subseteq V$ such that $\overline {\text{cl}(A)}\ne \emptyset$ and $|\partial A|=\kappa(G)$. An **atom** of $G$ is a fragment that contains the minimum number of vertices (it must  be connected).
	* *Intuition*: Consider the minimum vertex cut. It will separate the graph into two components. The components are the fragments.  The vertex cut, therefore, lies in the boundary of both fragments. 
* For any fragment $A$
	* $\partial A =  \partial\overline{A}$
	* $\overline {\overline A} =A$

* (*Godsil 3.4.3*) Let $A,B$ be fragments of $X$. Then
	* $\partial(A\cap B)\subseteq (A\cap \partial B) \cup (\partial A \cap B) \cup (\partial A\cap \partial B)$
	* $\partial(A\cup B) = (\overline{A} \cap \partial B)\cup (\partial A \cap \overline{B}) \cup (\partial A\cap \partial B)$
	* $\overline{A} \cup \overline{B} \subseteq \overline{A \cap B}$
	* $\overline{A\cup B} = \overline{A} \cap \overline{B}$

* (*Godsil 3.4.4*) Let $X$ be a graph on $n$ vertices with connectivity $\kappa$. Suppose $A$ and $B$ are fragments of $X$ such that $A\cap B\ne \emptyset$  . If $|A|\le |\overline{B}|$ then $A\cap B$ is a fragment. 
	* (*Godsil 3.4.4.1*) 
	  $$
	  |A\cup B|<n-\kappa
	  $$
	  Equality holds in the above if and only if $|A\cap B|= 0$. 
	* (*Godsil 3.4.4.2*) 
	  $$
	  |\partial(A\cup B)|\le \kappa
	  $$
	* (*Godsil 3.4.4.3*) 
	  $$
	  \overline A \cap \overline B \ne \emptyset
	  $$
	* (*Godsil 3.4.4.4*) 
	  $$
	  |\partial (A\cup B)| = \kappa
	  $$
* (*Godsil 3.4.5*) If $A$ is an atom and $B$ a fragment of $X$ then $A$ is a subset of exactly one of $B, \partial B$ and $\overline{B}$

* (*Godsil e3.20*) If $A$ is an atom and $B$ a fragment of $X$ such that $A\subseteq \partial B$, then $|A|\le |\partial B| /2$. 
	* *Proof*:   Let $|\partial B|=\kappa$ We have
	  $$
	  \partial(A\cup B) = (\overline A \cap \partial B)\cup (\partial A \cap \overline{B}) \cup (\partial A\cap \partial B)
	  $$
	  Computing the size, this is equivalent to
	  $$
	  |\partial (A\cup B) | = \kappa - |B| + |\partial B \cap \overline A|
	  $$
	  And $|\partial (A\cup B)|\ge \kappa$ by minimality of $\kappa$. Therefore
	  $$
	  \kappa  \le \kappa-|B| + |\partial B\cap \overline A|
	  $$
	 We get $|B| \le |\overline A \cap \partial B|$.  By atomicity, $|A|\le |B|\le |\overline A \cap \partial B|$. Finally, we note that
	 $$
	 \begin{split}
	 |\partial B | &= |A| + |\overline A \cap \partial B | + |\partial A \cap \partial B | \\
	 
	 &\ge 2|A|
	 
	 \end{split}
	 $$
	 This gives us $2|A|\le \kappa$ which completes the proof.  
	  

# Links
* [[Introduction To Graph Theory by Wilson]]
* [[Algebraic Graph Theory by Godsil and Royle]]

* [[Fundamental Constructs of Graph Theory]]
* [[Operations on Graphs]]