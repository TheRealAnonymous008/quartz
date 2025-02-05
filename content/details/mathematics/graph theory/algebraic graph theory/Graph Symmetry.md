# Group Formulation
* We can consider a permutation group $G$ [[Group Action|acting]] on the vertices of graph $X$. 
* See also [[Graph Automorphism]] and [[Graph Homomorphism]]

* (*Godsil e2.8*) Let $X$ be self-complementary  with more than one vertex. Then there exists a permutation $g$ of $V(X)$ such that
	* $(x,y)\in E(X) \iff (gx, gy)\in E(\overline{X})$.
		* *Proof*: Because $X\cong\overline X$, we can map edges as follows $(x,y)\mapsto (x',y')$ in a bijective manner for any $x,y\in V$. $g$ is precisely the bijection mapping $x\mapsto x'$, $y\mapsto y'$ and so on.  
	* $g^2\in \text{Aut}(X)$ where $g^2\ne e$
		* *Proof*:  Consider $g\in \text{Aut}(X)$, $g\ne e$ which maps $(x,y)\to (x',y')$, and  $h$ the transposition that swaps $x$ and $y$. In particular, choose $x$ such that $g(x)\ne x'$.  Clearly $gh\in \text{Aut}(X)$ but also $(gh)^2 \in \text{Aut}(X)$. 
		  
		  To show $(gh)^2\ne e$. Consider  $(gh)^2 (x) = ghg(y)=g(y')$. If $x\ne g(y')$ we are done. Otherwise  $x=g(y')$ then $g^2(y')=g(x)=x'$. but clearly $y'\ne x'$ so $g^2 \ne e$. 

	* The [[Permutations and Orbits|orbits]] of $g$ on $V(X)$ induce self-complementary subgraphs of $X$ 
		* *Proof*: Consider the isomorphism $g$ which maps $(x,y)\mapsto (gx, gy)$ where $(x,y)\in E(X)$ and $(gx,gy)\in E(\overline{X})$ and $(x',y')\mapsto (gx',gy')$ where $(x',y')\in E(\overline{X})$ and $(gx',gy')\in E(X)$. $g$ is a permutation which can be decomposed into cycles. Each cycle corresponds to an orbit.
		  
		  Let $C=\set{v_1,\dots, v_r}$ be a cycle. The restriction $X[C]$ on this cycle is clearly self-complementary based on how we defined $g$.  

* (*Godsil e2.13*) Let $X$ be a graph such that $\text{Aut}(X)$ acts transitively on $V(X)$ and $B$ be a [[Primitive Permutation|block of imprimitivity]] for $\text{Aut}(X)$, then $X[B]$ is regular. 
	*  To show $X[B]$ is regular, note that $g\in \text{Aut}(X)$ is an automorphism acting transitively on $B$. If $(x,y)\in E(X[B])$ then so is $(gx,gy)\in E(X[B])$. Because it is always possible to find $h$ such that $x'=hx$, we can map edges with $x$ as one end point to edges with $x'$ as one end point (i.e., $(x,y)\mapsto  (x',y')$). They share the same degree, and because they were arbitrarily chosen, all vertices of $X[B]$ share the same degree. Hence $X[B]$ is regular.  



# Spectral Formulation
* (*Mesbahi 2.19*) Let $A(G)$ be the [[Matrices in Graph Theory|adjacency matrix]] of the graph $G$ and $\psi$ a permutation on its vertex set $V$. Associate the permutation with a permutation matrix $\Psi$ such that 
  $$
  \Psi{ij} = \begin{cases}
  1 & \text{if } \psi(i)=j \\
  0 & \text{otherwise} 
  \end{cases}
  $$
  Then $\psi$ is an automorphism of $G$ if and only if
  $$
  \Psi A(G) = A(G) \Psi
  $$
  
  The **order** of an automorphism is defined as the least positive integer for which 
  $$
  \Psi^z = I
  $$

* (*Mesbahi 2.20*) If all [[Matrix Diagonalization|eigenvalues]] of the adjacency matrix of the graph are simple, then every non-identity automorphism of $G$ has order two.

# Quotient Objects
* A **cell** is a subset of the vertex set $V$. A **partition** of $G$ is a grouping of a vertex set into different cells. A **nontrivial cell** is a cell containing more than one vertex. 
	* A **characteristic vector** $p_i\in \mathbb{R}^n$ of a nontrivial cell $C_i$ has $1$-s in its components associated with $C_i$ and $0$s elsewhere.
	* The **characteristic matrix** $P\in M_{n\times r}(\mathbb{R})$ is a matrix with characteristic vectors as columns.

* An $r$-partition $\pi$ of $V$ with cells $C_1,\dots, C_r$ is **equitable** if each vertex in $C_j$ has the same number of neighbors in $C_i$ for all $i,j$. 
  
  The **cardinality** of a partition is denoted $|\pi|$. 
* The **quotient** of $G$ over $\pi$ is defined as the [[Directed Graph|digraph]], potentially with cell loops where the cells  are the nodes and $b_{ij}$ are edges. [^quotient]
	* The adjacency matrix of the quotient is specified by
	  $$
	  A(G/\pi)_{ij} = b_{ij}
	  $$
* A **non-trivial equitable partition** contains at least one cell with more than one node.

* (*Mesbahi 2.23*) Let $P$ be the characteristic matrix of an equitable partition $\pi$ of $G$. Then 
  $$
  A(G)P = PA(G/\pi)
  $$
  And
  $$
  A(G/\pi) = P^\dagger A(G) P
  $$
  (See [[Matrix Pseudo-Inverse]])

* (*Mesbahi 2.24*) Let $\pi$ be a partition of $V$ with characteristic matrix $P$. Then $\pi$ is equitable if and only if the column space of $P$ is $A(G)$-[[Invariant Subspace|invariant]]. 
  
  That is
  $$
  A(G) R(P) \subseteq R(P)
  $$
# Links
* [[Graph Theoretic Methods in Multiagent Networks by Mesbahi and Egerstedt]] 
* [[Algebraic Graph Theory by Godsil and Royle]]
