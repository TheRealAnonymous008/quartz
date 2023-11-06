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
* We show sufficiency by showing that each one of the subsets contains more than one element that can be removed without altering the condition outlined in Hall's Theorem, and eventually we may reduce this to the case where each subset contains exactly one element, the element in the [[Matroid Theory|transversal]]
  
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
* A **vertex cover** $V'$ is a subset of vertices such that every edge in the graph is incident to at least one vertex in $V'$
* A **minimum vertex cover** is a vertex cover which contains as few vertices as possible.

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

# Flow Networks 
### Definitions
* A **Flow Network** is a weighted [[Directed Graph|digraph]] where the edges have a flow and capacity, and there is exactly one source vertex, and one sink vertex 
	* The **sink vertex** has exactly $0$ outdegree.
	* The **source vertex** has exactly $0$ indegree

* The **capacity** is a function denoted $c$ which assigns each edge in the flow network a non-negative real number. 
* A **flow** in a flow network is a function $f$ that assigns each arc in the flow network to a non-negative real number (called the *flow of an arc*) such that the following constraints hold 
	* **Capacity Constraint** - the flow of each arc is no greater than the capacity of each arc. 
	* **Flow Conservation Constraint** - for each vertex, the total flow that comes in the vertex is the same as the total net flow leaving the vertex. 
	  $$
	  \deg^-(v) = \deg^+(v)
	  $$
* The **value** of a flow between vertices $s$ and $t$ is calculated as 
  
  $$
  |f| = \sum_{v\mid sv\in E} f_{sv} = \sum_{v\mid vt\in E} f_{vt}
  $$
  
### Augmenting Paths and Residual Networks
* A **pseudo-flow** $f$ is a function on each network which satisfies.
	* The capacity constraint.
	* For arc $uv$, $f(u,v)=-f(v,u)$
* The **residual capacity** of an arc $a$ under the pseudo-flow $f$ is the difference between the capacity and the flow of the arc.
* The **residual network** represents the amount of flow that can be transferred across the flow network. 
	* It is obtained by having each arc in the flow network have the residual capacities as their weight.
* An **augmenting path** is a [[Trails, Walks, Paths and Cycles|path]] in the residual network from the source $s$ and sink $t$ and where a flow is available from $s$ to $t$ satisfying the constraints of flow.
* The **bottleneck** of a flow network is the minimum residual capacity of all edges in a given augmenting path.


* The **maximum flow** in a flow network is the maximum value of a flow from source to sink.
	* A network is in maximum flow if and only if there are no augmenting paths.
* The **minimum cut** of a flow network is an edge cut that separates the source and skink in such a way that the capacity of the cut is minimized.

### Key theorems
* **Max-Flow Min Cut Theorem** - In any flow network, the maximum flow is equal to the capacity of the minimum cut. 
	* The capacity constraint restricts $\max f \le \min c$. 
	* Generating a residual network by finding  an augmenting path $p$ of bottleneck $c_p$  and increase the flow up to a limit by increasing the flow from $u$ to $v$ by $c_p$ and decreasing the flow from $v$ to $u$ by $c_p$. 
	* The new flow no longer contains the augmenting path $p$. We either augment with $0$ or with the maximum capacity of the new flow. 
	* When the process terminates, we have the maximum flow, and at least the minimum capacity. Hence $\max f \ge \min f$,

# Menger's Theorem 
* Can be thought of as a special case of the Max-Flow, Min-Cut Theorem
* (*Wilson 28.1*) **Edge Version** - the maximum number of edge-independent paths connecting two distinct vertices $v$ and $w$ of a connected graph is equal to the minimum number of edges in a $v,w$-edge cut.
* (*Wilson 28.1*) **Vertex Version** - the maximum number of vertex disjoint paths connected two distinct vertices $v$ and $w$ of a connected graph is equal to the minimum number of edges in a $v,w$-vertex cut.
* (*Wilson 28.6*) **Menger's Theorem implies Hall's Theorem**
* (*Wilson 28.3*) - A graph is $k$-connected if and only if any two distinct vertices of $G$ are connected by at least $k$-edge disjoint paths 
* (*Wilson 28.4*) - A graph is $k+1$-connected if and only if any two distinct vertices of $G$ are connected by at least $k$-vertex disjoint paths 
# Links
* [[Families of Graphs]]