* An **automorphism** of a graph is a [[Permutations and Orbits|permutation]] $\psi$ of its vertex such that 
  $$
  \psi(u)\psi(v) \in E \iff uv\in E
  $$
  An **automorphism [[Fundamental Constructs of Group Theory|group]]** is defined as the set of all graph automorphisms on $G$. 

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
