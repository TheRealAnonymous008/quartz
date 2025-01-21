* The **line graph** of a [[Fundamental Constructs of Graph Theory|graph]] $X$ is the graph $L(X)$ such that 
  $$
  \begin{split}
  V(L(X)) &= E(X) \\
  E(L(X)) &= \set{xy \mid x \text{ is incident to } y \text{ in } X} 
  \end{split}
  $$

* Line graphs for common families of graphs:
	* $L(K_n) = K_{1,n}$
	* $L(P_n) = P_{n-1}$.
	* $L(C_n)=C_n$. 
	* The only graphs where $L(G)\cong G$ are the $2$-regular graphs.
		* *Proof*: Let $L(G)\cong G$. We have 
		  $$
		  \begin{split}
		  V(G)&\cong V(L(G))\cong E(G) \\
		  E(G) &\cong \set {e_1e_2\mid e_1 \text{ is incident to } e_2}
		  \end{split}
		  $$
		  Thus, there is an isomorphism between $V(G)$ and pairs of edges in $E(G)$ which are incident. A natural mapping is: 
		  $$
		  f(ux,xv) = x
		  $$
		  Because it is an isomorphism, it is also invertible. This means each vertex is incident to only $2$ edges. Thus, the graph is $2$ regular.


* (*Godsil 1.7.1*) If $X$ is $k$-regular, then $L(X)$ is regular with degree $2k-2$.
	* *Proof*: Let $uv$ be an edge in $X$. Since it is $k$-regular, it is incident to $k-1$ other edges from $u$ and $v$ respectively for a total of $2k-2$

* (*Godsil e1.12*) Any induced subgraph of a line graph is also a line graph.

* (*Godsil 1.7.2*) **Krausz Characterization of Line Graphs** A nonempty graph is a line graph if and only if its edge set can be partitioned into a set of cliques with the property that any vertex is in at most two cliques.
	* If $X$ is triangle-free, then all cliques are all maximal.
* (*Godsil 1.7.3*) Except for the pair $K_3, K_{1,3}$, the following is true
  $$
  X\cong Y \iff L(X) \cong L(Y)
  $$

	* *Idea*: There is a bijection between $V(X)$ and the maximal cliques of $L(X)$.
* (*Godsil 1.7.4*) A graph $X$ is a line graph if and only if each induced subgraph of $X$ on at most six vertices is a line graph. 

* (*Godsil 1.7.5*) If $X$ is a [[Graph Connectivity|connected graph]] and $L(X)$ is regular, then $X$ is regular or [[Bipartite Graph|bipartite]] and semiregular. 
	* *Proof*: If $uv\in E(X)$, and $L(X)$ is $k$-regular, then $uv$ has $k$ edges incident to it. Adding itself to the degree counts, we get 
	  $$
	  \deg(u)+\deg(v) = k+2
	  $$
	  Consider arbitrary vertex $u$. Let $N_i(u)$ be the set of vertices of distance exactly $i$ from $u$. We have that all of $N_1(u)$ have the same degree. All of $N_2(u)$ share the same degree, and so on. In general, we can partition the graph (by connectivity) into $N_{2k}(u)$ and $N_{2k+1}(u)$. 
	  
	  To show the theorem, consider two cases. If the degree of $N_{2k}(u)$ equals that of $N_{2k+1}(u)$, then $X$ is regular by definition.
	  
	  This can only happen because of two adjacent vertices with the same degree (i.e., in an odd cycle). If the graph has no odd cycle, it is bipartite and by our characterization semiregular. 



# Links
* [[Algebraic Graph Theory by Godsil and Royle]]

* [[Fundamental Constructs of Graph Theory]]
* [[Families of Graphs]]
