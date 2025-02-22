# Trails and Walks
* Let  $G=(V,E)$ be an undirected graph. 
  
  A **walk** in $G$ is a finite sequence of vertices and edges of the form 
  $$
  v_0, e_1, v_1, e_2, \dots e_n, v_n
  $$
   such that  $v_0, \dots, v_n \in V$ and $e_1, \dots, e_n \in E$ and each edge is incident to the vertices to its left and right in the sequence (i.e., $e_1=v_0v_1$).
   
   We do not require that each vertex and each edge is distinct from each other.
	* In the definition we call $v_0$ as the **initial vertex** and $v_n$ as the **final vertex** of the walk.
	* If the initial vertex is $u$ and the final vertex is $v$, the walk is called a **$u,v$-path**
	* The **length** of a walk refers to the number of edges in the walk.
 
* A **trail** is a walk in which all edges are distinct.
	* A $u,v$-trail is a trail which starts and ends at $u$ and $v$ respectively.

# Path
* A **path** is a graph with the following property with the following property.  
  
  We may list the vertices as  $V=\{v_1,\dots,v_n\}$ such that the only edges are of the form $(v_i, v_{i+1})$ for $i\le n-1$. 
	* A path is a trail where we also require the vertices to be distinct from each other.

* We denote the path graph on $n$ vertices as $P_n$. We call $n$ its **length**

* We say that a path $P$ is **in** a graph $G$ if $P\subseteq G$
* If the path starts with vertex $u$ and ends with $v$, such a path is called a  **$u,v$-path**

* A family of paths in a graph is **edge independent** or **edge disjoint**  if no edge of $G$ is an edge of more than one path in the family
* A family of paths in a graph is **internally disjoint** if no vertex of $G$ is an internal vertex of more than one path in the family.

* (*Godsil e3.18*) Any two paths of maximum length in a connected graph must have at least one vertex in common.
	* *Proof*: Let $G$ be the graph .Denote $P(u,v)$ as a $u,v$-path. 
	  By connectivity, $P(u,v)$ is always well-defined. Also let $P_1 = P(u_1,v_1)$ and $P_2=P(u_2,v_2)$ and $|P_1|=|P_2|=d$ such that both are maximum length paths. 
	  
	   Let $P$ be the path  $u_1\to x_1\to x_2 \to u_2$.  To choose $x_1$ and $x_2$, we consider a path $P'=P(u_1,u_2)$.   $x_1$ is chosen to be the last vertex of $P'$ in $P_1$ and $x_2$ the first vertex of $P'$ in $P_2$. This ensures that all the subpaths in $P$ are internally disjoint  so that $P$ is a valid path.   WLOG, assume $|P(u_1,x_1)|\ge |P(x_1,v_1)|$ and $|P(u_2,x_2)|\ge |P(x_2,v_2)|$. 
	  
	  By connectivity, $|P(x_1,x_2)|>0$ and disjointness.
	 
	 $P(u_1,x_1)$ and $P(u_2,x_2)$ must have length at least $k/2$. Therefore
	  $$
	  \begin{split}
	  |P| &= |P(u_1,x_1) | + |P(x_1,x_2) | + |P(x_2,u_2)| \\
	  &\ge k /2 + k/2  + |P(x_1,x_2)| \\ 
	  &\ge k + |P(x_1,x_2) | \\
	  &> k
	  \end{split} 
	  $$
	  Therefore $P$ is a longer path which is a contradiction

## Shortest Paths
* Let $G$ be a weighted graph. The **shortest path** is the path between two vertices $u$ and $v$ that has a minimum weight.
  
  In an unweighted graph, this reduces to the path with the minimum number of vertices.


# Cycle
* A **cycle** is a graph that is connected and 2-[[Regular Graph|regular]].
  
* A cycle is **in** a graph if $C\subseteq G$. 
	* A cycle is a trail where each vertex is distinct except for the first and last vertex.
* A cycle of $n$ vertices is denoted $C_n$. $n$ is the **length** of the cycle.

* The **girth** of an undirected graph $G$ is the length of the shortest cycle in $G$.

* *(Wilson 6.1)* If $G$ is a finite graph in which the degree of each vertex is at least $2$, then $G$ contains a cycle.
* (*Wilson e5.11a*) If two distinct cycles of a graph each contain edge $e$, then $G$ has a cycle that does not contain $e=uv$ 
	* *Proof*:  Consider the $u,v$-path that goes from $C_1$ and then the $v,u$-path in $C_2$.

* (*Godsil e3.19*) Any two cycles of maximum length in a $3$-connected graph must have at least three vertices in common
	* *Proof*:  Let $C_1,C_2$ be the cycles of interest with length $k$.  By (*Wilson 28.4*), there must be at least $2$ vertex disjoint paths between $u$ and $v$. Denote them as $P,Q$.  We argue by contradiction and show that if $|C_1\cap C_2|\le 2$, it is always possible to create a larger cycle.  $P$ and $Q$ must intersect $C_1,C_2$ at points $p_1,p_2$ and $q_2,q_2$. We also let $u\in C_1-C_2,v\in C_2-C_1$.  respectively;  Let $C_1^+$ be the part of the cycle containing $u$ bounded by $p_1, q_1$ and similarly for $C_2^+$ for $v$, and $C_1^-, C_2^-$ for the other segments in the respective cycles 
	  
	  First suppose that $|C_1\cap C_2|= 0$.  .We create two new cycles.
	  $$
	  \begin{split}
	  p_1\to q_1 \to C_2^+\to  q_2\to p_2 \to C_1^+ \to p_1 \\
	  p_1 \to q_1 \to C_2^-\to q_2\to p_2 \to C_2^- \to p_1
	  \end{split}
	  $$
	  These cycles must have length  $\le k$ but that would imply $p_1=q_1$ and $p_2=q_2$ which, from how we defined the paths implies $|C_1\cap C_2|=2\ne 0$. 
	  
	  Now suppose $|C_1\cap C_2| = 1$ where WLOG $p=p_1=p_2$ and  $p\in C_1\cap C_2$.  Consider the new cycles
	  $$
	  \begin{split}
	  q_1 \to  C_1^-\to x \to C_2^+ \to v\to q_2\to q_1 \\
	  q_2 \to C_2^- \to x \to C_1^- \to u\to q_1\to q_2
	  \end{split}
	  $$
	  These cycles must have length $\le k$ but that would imply $q_1=q_2$ which would also imply $|C_1\cap C_2| = 2\ne 1$.
	  
	  Now suppose $|C_1\cap C_2|=2$. Where $p=p_1=p_2$ and $q=q_1=q_2$ and $p, q\in C_1\cap C_2$. It is possible to find a path $P'$ connecting $u$ and $v$ without passing through $p$ and $q$ by $3$-connectivity. Suppose they intersect the two cycles at $p_1',p_2'$ and we define $C_1^+,C_2^+,C_1^-,C_2^-$ as before. WLOG, suppose  $C_1^+$ and $C_2^+$ are the longer segments.  Note that $|C_1^+| + |C_1^-|= |C_2^+| + |C_2^-|=k$ which implies $|C_1^+|, |C_1^+|\ge k/2$. However, construct the cycle using these two segments. and $P'$ This gives us a cycle of length $> k$ completing the proof.

# Triangles
* A **triangle-graph** is the complete graph $K_3$. 
* A graph that does not contain a triangle is **triangle-free**

* **Mantel's Theorem**  Let $G$ be triangle free. Then
  $$
  V(G)=2k \implies E(G)\le k^2
  $$
	* *Proof*: The proof is by induction. Given a triangle free graph, perform an edge deletion on $e=uv$ to get a smaller triangle-free graph. Show we can choose at most $2n-2$ vertices to join to one of $u,v$ but not both. This implies, there are at most $2n-1$ vertices not in the smaller graph. This will complete the proof.

* (*Wilson e5.10*): The triangle free graph with $2n$ vertices and $n^2$ edges is $K_{n,n}$. 
	* *Proof*: Given an edge $e=uv$, we may partition the remaining vertices into sets if they are connected to $u$ or $v$.




# Links
* [[Introduction To Graph Theory by Wilson|Wilson]]
* [[Graph Theory With Applications by Bondy and Murty|Bondy and Murty]]
* [[Algebraic Graph Theory by Godsil and Royle]]

* [[Graph Connectivity]]
* [[Families of Graphs]]
* [[Directed Graph]]