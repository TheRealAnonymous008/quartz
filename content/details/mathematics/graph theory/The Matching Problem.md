* A **matching** in an undirected graph is a subset of its edges where each edge does not share endpoints with each other.
  
  We say that a vertex is **matched** or **saturated** if it is an endpoint in one of the edges in the matching, otherwise it is **unmatched** or **unsaturated**.

* A matching is a **maximum matching** if it contains as many edges as possible. Every vertex is adjacent to at most one edge of the matching.

* A **Complete Matching** from $V_1$ to $V_2$ in a bipartite with partitions $V_1$ and $V_2$ is a injection between the vertices in $V_1$ and a subset of vertices in $V_2$ such that corresponding vertices are joined.

# Hall's Marriage Theorem
* Let  $G$ be a bipartite graph with partitions $V_1$ and $V_2$. For each subset $A\subseteq V_1$, let $\phi(A)$ be the neighborhood of $A$.
  
  Then a complete matching from $V_1$
  to $V_2$ exists if and only if 
  $$
  |A|\le |\phi(A)|
  $$
  
## Halmos-Vaughan Proof
* Trivially, for any subset $A\subseteq V_1$ must correspond to at least one vertex in $\phi(A)$ so the condition holds.
  
  For the converse, suppose that for any subset $A\subseteq V_1$, then $|A|\le |\phi(A)|$. Argue by strong induction. Clearly the base case where $|A|=1$ must hold.

* Now suppose it holds for $|V_1|< m$. Consider two cases. Let $k<m$, and consider $|V_1|=m$. Note as well that $G-A$ denotes the unmatched vertices in $V_1$.

1. If $|A|<|\phi(A)|$
   
   Then we are done as we will have at least a spare vertex in $V_2$ which we may match to any vertex in $G-A$.

2. If $|A|=|\phi(A)|$ 
   
   Then, by induction, we may match these vertices to each other leaving us with $m-k$ vertices unmatched.
   
   The induction hypothesis applies for the remaining $m-k$ vertices since this is a smaller subgraph. Let $B\subseteq G-A$ . We show by contradiction that it does.
	
	Now, if $|B|\ge|\phi(B)|$ , then together with the original $k$ vertices, we have 
	$$
	\begin{equation} \begin{split}
	k+|B| &\ge k+|\phi(B)| \\
	|A\cup B| & \ge |\phi(A\cup B)| 
	\end{split}
	\end{equation}
	$$
	Line 2 follows from the fact $A$ and $B$ are disjoint. Note that $A\cup B$ is a subset of $V_1$, so it must follow Halls' condition that $|A\cup B| < |\phi(A\cup B)|$ and this gives a contradiction to the above.
	
	Therefore, the induction hypothesis applies to $B$ as well, and we may find a matching.

## Rado's Proof
* Necessity follows from [[#Halmos-Vaughan Proof|the previous proof]]
* We show sufficiency by showing that each one of the subsets contains more than one element that can be removed without altering the condition outlined in Hall's Theorem, and eventually we may reduce this to the case where each subset contains exactly one element, the element in the [[Matroids|transversal]]
  
  Suppose $S$ contains elements $x,y$, and the removal of either invalidates the condition (i.e., a reduction described above is impossible). Then there are subsets $A$ and $B$ of $\{2,3,\dots,m\}$  with the property that $|P|< |A| + 1$ and $|Q|< |B| + 1$ where 
  
  $$
  \begin{equation}
  \begin{split}
  P&=(S-\{ x\}) \cup \bigcup_{i\in A} S_i\\
  Q&= (S -\{y\}) \cup \bigcup_{i\in B}S_i
  \end{split}\end{equation}
  $$
  That is, consider the family but with one of $x$ and $y$ removed from $S$, and as stipulated, Hall's condition doesn't hold. But also
  $$
  \begin{equation} 
  \begin{split}
  |P\cup Q| &=  \left|\bigcup_{i\in A\cup B} S_i\cup S \right| \\
  |P \cap Q| &\ge \left | \bigcup_{i\in A\cap B} S_i \right | 
  \end{split}
  \end{equation}
  $$
  Now, observe the contradiction The last line follows from inclusion-exclusion principle
  
  $$
  \begin{equation} 
  \begin{split}
  |A|+|B| &\ge |P|+|Q| \\
  &=|P\cup Q|+|P\cap Q| \\
  &\ge \left|\bigcup_{i\in A\cup B} S_i\cup S \right| + \left | \bigcup_{i\in A\cap B} S_i \right |\\
  &\ge |A\cup B|+1+ |A\cap B| \\
  &=|A|+|B|+1
  \end{split}
  \end{equation} 
  $$

# Konig-Egevary  Theorem
* In any bipartite graph, the number of edges in a maximum matching equals the number of vertices in a minimum vertex cover.

* *Proof*:
  Let 
  $G$ be a bipartite graph with bipartition $X, Y$. 
  $C$ be a minimum vertex cover.
  $\mu(G)$ denote the cardinality of the maximum matching 
  $\tau(G)$ the minimum vertex cover.
  
  Clearly $\mu(G)\le \tau(G)$ since the minimum vertex cover is incident to all edges, so any matching must match to at least some of these vertices.
  
  Split $C$ into $C_X = C\cap X$ and $C_Y=C\cap V_Y$, that is into sets that are contained in each of the bipartitions.
  
  Let  $X'=X-C_X$ and  $Y'=Y-C_Y$. 
  
  Clearly there is no edge connecting $X'$ and $Y'$ otherwise these edges weren't covered by the covering.
  
  Consider a subset $S\subseteq C_X$. Clearly $|S|\ge |\phi(S)$| otherwise we may simply use $\phi(S)$ in $C$, leading to a contradiction by the fact that $C$ is already a minimum vertex cover, so there can be no smaller.
  
  The above is Hall's condition so Hall's Marriage Condition applies.
  
  A similar thing applies to $T\subseteq C_Y$.
  
  So there must be a complete matching that contains the vertices of $C_X$ and $C_Y$ (i.e., $C$). This is only possible when $\mu(G)\ge \tau(G)$ (i.e., the matching contains all the vertices in the cover, plus possibly extra.).
  
  Since $\mu(G)\le \tau(G)$ and $\mu(G)\ge \tau(G)$, the theorem is proven.

# Links
* [[Families of Graphs]]