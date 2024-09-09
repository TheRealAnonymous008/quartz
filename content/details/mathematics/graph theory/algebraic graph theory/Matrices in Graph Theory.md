* We can represent the adjacency relation with a square [[Matrix]] called the **adjacency matrix** denoted $A$. It is $|V| \times |V|$ and we obtain the entries as follows. 
  
  For an undirected, graph 
  $$
  A_{ij} = \begin{cases}
  1 & v_i \leftrightarrow v_j \\ 
  0 & \text{otherwise}
  \end{cases}
  $$
  
  For a directed graph we can define the adjacency matrix with either the in-degree or the out-degree.
  
  For the in-degree definition we have that 
  $$
  A_{ij} = \begin{cases}
  1 & (v_j, v_i) \in E(G) \\ 
  0 & \text{otherwise}
  \end{cases}
  $$
  
  For the out-degree definition we have that 
   $$
  A_{ij} = \begin{cases}
  1 & (v_i, v_j) \in E(G) \\ 
  0 & \text{otherwise}
  \end{cases}
  $$
  
  We denote the adjacency matrix of $G$ as $A(G)$.
	* *Notation*: For digraphs, we assume the in-order definition by default unless otherwise stated. 

* The **Incidence Matrix** is an $|V|\times |E|$ matrix $B$ where: 
  $$
  \begin{equation}
  B_{ij} = 
  \begin{cases}
  1 & \text{if } v_i \text{ is incident with } e_j\\
  0 & \text{otherwise}
  \end{cases} 
  \end{equation}
  $$
  
  We denote the incidence matrix of $G$ as $B(G)$.
  
  If the graph is [[Directed Graph|directed]], then we have
  $$
  \begin{equation}
  B_{ij} = 
  \begin{cases}
  1 & \text{if } e_j = v_ix, \text{ that is, } v_i \text{ is the head of the edge} \\
  -1 & \text{if } e_j = xv_i, \text{ that is, } v_i \text{ is the tail of the edge} \\
  0 & \text{otherwise}
  \end{cases} 
  \end{equation}
  $$
  In this case, we say that the incidence matrix captures the graph's *orientation*. 
	* For any incidence matrix on $G^0$, the column sum of any column is $0$.
	  
	  If there is no orientation, the column sum is $0 \text{ mod } 2$
	  
	  This corresponds to the fact that edges have exactly one head and one tail.  


* The **Degree Matrix** is the diagonal matrix $D$ obtained by
  $$
  D_{ii}=\deg v_i
  $$
  We denote this with $D(G)$ for graph $G$.
  
  For digraphs, we may define this with either the in-degree or the out-degree instead.
	* *Notation*: By default, we assume the in-degree notation unless otherwise stated. 

* The **Laplacian Matrix** of $G$ is the square matrix $L$ whose components are obtained as 
  
  $$
  \begin{equation} \begin{split}
  L_{ij} &= \begin{cases} 
  \deg(v_i) & i=j \\
  -1 & v_i \text{ is adjacent to } v_j \\
  0 & \text{otherwise}
  \end{cases}
  \end{split}\end{equation}
  $$
  
  It may also be obtained as 
  $$
  L=D-A
  $$
	* The rows of the Laplacian of any graph sum to zero. 

* For a weighted graph, the **Weight Matrix** is an $m\times m$ diagonal matrix such that 
  $$
  W_{ii} = w(e_i)
  $$

* The **Topological Overlap Matrix** between nodes $i$ and $j$ is calculated as 
  
  $$
  X_{ij}^o = \frac{J(i,j)}{\min(k_i,k_j)+1-\Theta (A_{ij})}
  $$
  Where $k_i$ and $k_j$ are the degrees of node $i$ and $j$
  $\Theta(x)$ is the Heaviside Function
  $J(i,j)$ is the number of common neighbors of node $i$ and $j$ (i.e., $|\phi(i)\ cap \phi(j)|$) 
 
# Links
* [[Introduction To Graph Theory by Wilson]]
* [[Matrix]] and more generally [[Linear Algebra]]
* [[Graph Theoretic Methods in Multiagent Networks by Mesbahi and Egerstedt]]