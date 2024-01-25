* Let $G$ be graph. The graph is $k$-**colorable** if it is possible to assign for each vertex $v\in V(G)$ colors such that adjacent vertices have different colors.
* A graph is **$k$-edge colorable** if its edges can be colored with $k$ colors so that no two adjacent edges (i.e., edges that share an endpoint) have the same color .
* A map is $k$-**face colorable** if its faces can be colored with $k$ colors such that no two faces with a boundary edge in common have the same color.
# Chromatic Number
* The **chromatic number** of $G$ denoted $\chi(G)=k$ implies that $G$ is $k$-colorable but not $(k+1)$-colorable.
* A graph $G$ has a **chromatic index** denoted $\chi'(G)$ if it is $k$-edge colorable but not $k-1$ edge colorable.

* (*Wilson Ch. 18*) **Brook's Theorem** - If $G$ is a simple connected graph and not an odd cycle, and if $\Delta(G)\ge 3$, then $G$ is $\Delta$-colorable.
* **Vizing's Theorem**  [^2]
  
  $$
  \Delta \le \chi'(G) \le \Delta +1
  $$
  
[^2]: This follows by coloring a vertex one color, and all its neighbors any of the remaining colors (at most $\Delta$) by definition.

* (*Wilson 20.2*) 
  $$
  \begin{equation} 
  \begin{split}
  \chi'(K_n) &= \begin{cases} 
  n & n \text{ is odd} \\
  n-1 & n \text{ is even}
  \end{cases}
  \end{split}
  \end{equation}
  $$
  
* (*Wilson 20.4*) **Konig's Theorem** If $G$ is bipartite,  then 
  $$
  \chi'(G)=\Delta
  $$
  
  
# Four Color Theorem
* **Vertex Formulation**:  Every simple [[Graph Planarity|planar]] graph is $4$-colorable.
* **Face Formulation**: Any map is $4$-face colorable
* (*Wilson 20.3*) **Edge Formulation**: $\chi'(G)=3$ for each cubic map of $G$. 

# Chromatic Polynomials
* Let $G$ be a simple graph. The **chromatic polynomial**, denoted $P_G(k)$ is the number of ways to perform a vertex coloring with $k$ colors available.
	* $P_G(k)=0$ If $k<\chi(G)$

* (*Aydelotte 2.6, Wilson 21.2*). The chromatic polynomial is a polynomial.

* **The Deletion-Contraction Formula**. If $G$ is a simple [^1] graph, then 
  
  $$
  P_G(k) = P_{G-e}(k) -P_{G/e}(k)
  $$
  
  [^1]: Consider $e=uv$. The number of colorings in $P_{G-e}(k)$ where $u$ and $v$ have different colors is $P_G(k)$. The number of colorings where $u$ and $v$ have the same colors is $P_{G/e}(k)$ where $e$ is contracted and $u=v$.  
  
* (*Aydelotte 2.4*) Let $G$ be a simple graph, $G_1,\dots, G_n$ be a decomposition of $G$. Then
  
  $$
  P_G(k)  = P_{G_1}(k)\cdot P_{G_2}(k) \cdot \dots \cdot P_{G_n}(k)
  $$

* (*Aydelotte 3.1*) The degree of $P_G(k)$ l is the number of vertices of $G$.
* (*Aydelotte 3.2*) The chromatic polynomial has the following properties.
	1. The Leading Coefficient of $P_G(k)$ is $1$.
	2. The absolute value of the coefficient of the $k^{n-1}$ term in $P_G(k)$ is the number of edges of $G$.
	3. The first coefficient of $P_G(k)$ is positive, and all terms alternate in sign.
	4. All coefficients are integer.
	5. If the coefficient of $x^{n}$, then so is $x^{n-1}$.
* (*Aydelotte 3.2*) The constant term of the chromatic polynomial of any graph is $0$.
* (*Aydelotte 3.7*) The chromatic polynomial of $K_n$ is 
  $$
  P_{K_n}(k) = {n\choose{k}} 
  $$
* (*Aydelotte 3.8*) The chromatic polynomial of $C_n$ 
  $$
  P_{C_n}(k)= (k-1)^n + (-1)^n (k-1)
  $$
* (*Theorem*) The chromatic polynomial of a tree of $n$ vertices $T_n$ is 
  $$
  P_{T_n} (k) = k(k-1)^{n-1}
  $$
* **Read's Theorem** For a given chromatic polynomial $P_G(k)$ with coefficients $a_0, \dots, a_n$, $P_G(k)$ is unimodal. That is, there is some $m$ such that 
  
  $$
  |a_n|\le|a_{n-1}|\le\dots \le |a_{m+1}| \ge |a_{m-1}|\ge \dots \ge |a_0|
  $$
  
# Chromatic Equivalence
* Two undirected graphs are said to be **chromatically equivalent** if they have the same chromatic polynomial but they are not isomorphic.
* An undirected graph $G$ is **chromatically unique** if for any graph $H$ with the same chromatic polynomial as $G$, then $G\cong H$


* An undirected graph $G$ is a $k$-**critical** if $\chi(G)=k$ and the vertex deletion of any vertex yields a graph with a smaller chromatic number, namely for vertex $v$ we have
  
  $$
  \chi(G-v) = k-1
  $$

* (*Wilson e17.11.3a*) Let $G$ be $k$-critical. Then [^3
  $$
  \delta(G) \ge k-1
  $$

[^3]: Argue by contradiction. If $\deg v < k-1$, then $v$ has at most $k-2$ neighbors, and the induced subgraph is $k-1$ colorable. The Pigeonhole Principle applies and we find that we can replace the color of $v$ and we have the original graph as $k-1$ colorable. 

* (*Wilson e17.11.3b*) Let $G$ be a $k$-critical graph. Then $G$ does not contain cut vertices. A special case of *Wilson e17.11.3b*.  [^4]

[^4]: Let $G-v$ consist of components by virtue of $v$ beng a cut-set. Now, $G-v$ is $k-1$ colorable. Any component combined with $v$ (and the edges to $v$) $C_i+v$ is $k-1$ colorable. Taking the union of the components gives us a $k-1$ coloring.

* (*Wilson e17.11z*) Let $G$ be a $k$-critical graph. Any vertex cut of $G$ cannot be in a clique. 
	* This follows from *Wilson e17.11.3b* except applying the argument to multiple vertices instead.

# Links
* [[An Exploration of the Chromatic Polynomial by Aydelotte]]

* [[Fundamental Constructs of Graph Theory]]
* [[Families of Graphs]]
