* Given an arbitrary orientation to the edge set $E(G)$, the graph [[Matrices in Graph Theory|Laplacian]] can be defined as 
  $$
  L(G) = B(G^o) B(G^o)^T
  $$
	* The Laplacian is [[Self-Adjoint Matrix|self-adjoint]] and [[Definite Matrix|positive semi-definite]]
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

* (*Mesbahi e2.5*) Let $G$ be a graph, then
  $$
  \text{rank}(L(G)) = |V| - \omega(G) 
  $$
	* *Intuition*: The adjacency matrix can be arranged as a block diagonal matrix through reordering of matrices. The rank of which is known  [[Dimension Theorem|to be the sum of the ranks of the block matrices]]). 
	  
	  Let $B$ be a block in the Laplacian with $n$. Then, $\text{rank}(B)= n - 1$.  This is the case because $L$ is positive semi-definite. Therefore it has $0$ as an eigenvalue exactly once (by *Mesbahi 2.8*). 

* (*Mesbahi 2.8*) Let $L(G)$ be the Laplacian of $G$. Sort the eigenvalues as $0=\lambda_1(G)\le \dots \le \lambda_n(G)$.  We refer to this listing as the **Laplacian [[Spectral Theorem|spectrum]]
  
  $G$ is connected if and only if $\lambda_2(G)>0$ 
	* $\lambda_1(G) = 0$ since $L$ is positive semi-definite. This corresponds to the eigenvector of all $1$s (and it is $0$ because the sum of any row on an incident matrix is $0$).
	* Using the Spectral Properties of the Laplacian, we can extend the [[Graph Connectivity|connectivity inequality]]
	  $$
	  \lambda_2(G) \le   \kappa(G) \le \lambda(G) \le \delta (G)
	  $$
	  Provided that $G$ is not the complete graph.

* (*Mesbahi 2.9*) **Kirchhoff's Matrix [[Trees|tree]] Theorem** Consider the graph $G$ with $n$ vertices and $n-1$ edges. Then using the [[Determinant|determinant]]
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

* (*Mesbahi 3.8*) A digraph $D$ on $n$ vertices contains an arborescence if and only if 
  $$
  \text{rank}(L(D)) = n-1
  $$
  In that case $N(L(D))$ is spanned by the vector of all ones.

* (*Mesbahi 3.10*) Let $D$ be a weighted digraph on $n$ vertices. By the [[Matrix Limit|Gerschgorin Disk Theorem]]
  $$
  \text{spec}(L(D)) \subseteq \set{z\in \mathbb{C} \mid |z - \overline{d}_{in}(D)| \le \overline{d}_\text{in} (D)}
  $$
  Where $\overline{d}_\text{in}$ is the maximum weighted in-degree in $D$.
  
  Thus, every eigenvalue of $L(D)$ has non-negative real parts.

 * (*Mesbahi 3.11*) Let $L(D) = PJ(\Lambda) P^{-1}$ be the [[Jordan Canonical Form|Jordan]] decomposition of the in-degree Laplacian for $D$. When $D$ contains an arborescence, thee nonsingular matrix $P$ can be chosen such that
   $$
   J(\Lambda) = \begin{bmatrix}
   0 & 0 & \cdots & 0 & 0\\
   0 & J(\lambda_2) & \cdots & 0 & 0\\
   0 & 0 & \cdots & 0 & 0 \\
   \vdots & \vdots & \ddots & \vdots & \vdots \\ 
   0 & 0 & \cdots & 0 & J(\lambda_n)\\
   
   \end{bmatrix}
   $$
   Where $J(\lambda_i)$ is the Jordan block associated with $\lambda_i$, and each $\lambda_i$ has positive real parts.
   
   This implies that 
   $$
   \lim_{t\to\infty} e^{-J(\Lambda) t} = \begin{bmatrix}
   1 & 0 & \cdots  & 0 \\
   0 & 0 & \cdots  & 0 \\
   0 & 0 & \cdots  & 0 \\
   \vdots & \vdots & \ddots & \vdots \\
   0 & 0 & \cdots  & 0 \\
   \end{bmatrix}
   $$
   And
   $$
   \lim_{t\to \infty} e^{-L(D)t} = p_1q_1^T
   $$
   Where  $p_1$ is the first column of $P$ and $q_1^T$ the first row of $P^{-1}$. 



# Factorization Lemma
* (*Mesbahi 3.22*) Let $G_1,G_2$ be graphs on $n$ and $m$ vertices respectively. Then 
  $$
  L(G_1 \square G_2) = L(G_1) \otimes I_m + I_n \otimes L(G_2) = L(G_1) \oplus L(G_2)
  $$
  That is, *The Laplacian of the [[Cartesian Product of Graphs|Cartesian Product]] is the [[Matrix Kronecker Product|Kronecker sum]] of the Laplacians of the individual graphs*.
* (*Mesbahi 3.23*) Let $G_1,G_2$ be graphs on $n$ and $m$ vertices such that $L(G_1)$ and $L(G_2)$ respectively have as eigenvalues: $\lambda_1,\dots,\lambda_n$ and $\mu_1,\dots,\mu_1$ with associated eigenvectors $u_1,\dots, u_n$ and $v_1,\dots, v_m$. Then $\forall i,j$
  $$
  u_i \otimes v_j 
  $$
  Is the eigenvector associated with the eigenvalue $\lambda_i + \mu_j$ of $L(G_1 \square G_2)$. 
# Links
* [[Graph Theoretic Methods in Multiagent Networks by Mesbahi and Egerstedt]]