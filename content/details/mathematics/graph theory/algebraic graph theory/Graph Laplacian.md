* Given an arbitrary orientation to the edge set $E(G)$, the graph Laplacian can be defined as 
  $$
  L(G) = B(G^o) B(G^o)^T
  $$
	* The Laplacian is symmetric and [[Self-Adjoint Matrix|positive semidefinite]]
	* The Laplacian associated with a weighted graph is given by 
	  $$
	  L(G) = B(G) W B(G)^T
	  $$
* We may define an **Edge Laplacian** for any $G$ defined as
  $$
  L_e(G) = B(G)^T B(G)
  $$
	* The set of nonzero [[Matrix Diagonalization|eigenvalues]] of $L_e(G)$ is equal to the set of nonzero eigenvalues of $L(G)$
	* The nonzero eigenvalues of $L_e(G)$ and $L(G)$ are equal to the square of the [[Singular Value Decomposition|nonzero singular values]] of $B(G)$.
	* If $G$ has $p$ connected [[Graph Connectivity|components]] $G_i$, the edge Laplacian of $G$ has a block diagonal form
	  $$
	  L_e (G) = \begin{bmatrix}
	  B(G_1)^T B(G_1)  & O & \cdots & O \\
	  O & B(G_2)^T B(G_2) & \cdots & O \\
	  \vdots & \vdots & \ddots & \vdots \\
	  O & O & \cdots  & B(G_p)^T B(G_p)  
	  \end{bmatrix}
	  $$
	  This can be interpreted as an adjacency matrix, where edges that share common vertices are considered non-adjacent. 

* For any digraph, the vector of all ones is the eigenvector associated with the zero eigenvalue of $L(D)$
	* The in-degree version of the Laplacian captures how a node is influenced by others.
	* The out-degree version of the Laplacian captures how a node influences other nodes. 

* (*Mesbahi 2.8*) Let $L(G)$ be the Laplacian of $G$. Sort the eigenvalues as $\lambda_1(G)\le \dots \le \lambda_n(G)$.  We refer to this listing as the **Laplacian [[Spectral Theorem|spectrum]]
  
  $G$ is connected if and only if $\lambda_2(G)>0$ 

* (*Mesbahi 2.9*) **Matrix [[Trees|tree]] Theorem** Consider the graph $G$ with $n$ vertices and $n-1$ edges. Then using the [[Determinant|determinant]]
  $$
  \det (L(G-v)) = 1
  $$
  for any vertex $v$. 
  
  (*Mesbahi 2.10, Wilson 10.3*) Let $t(G)$ be the number of spanning trees in $G$. Then 
  $$
  t(G) = \text{det}(L(G-v))
  $$
  In other words, the number of [[Spanning Trees and Forests|spanning trees]] of $G$ is equal to the cofactor of any element of $L(G)$. 
  
  (*Mesbahi 2.12*) A directed graph version can be defined as follows. Let $v$ be an arbitrary vertex of a weighted digraph $D$. Then
  $$
  \text{det}(L(D-v)) = \sum_{T\in T_v} \prod_{e\in T} w(e)0
  $$
  Where $T_v$ is the set of spanning $v$-arborescences in $D$. 

# Links
* [[Graph Theoretic Methods in Multiagent Networks by Mesbahi and Egerstedt]]