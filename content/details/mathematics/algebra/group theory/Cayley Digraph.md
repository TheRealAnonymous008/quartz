* A **Cayley Digraph** is a [[Directed Graph]] where each vertex corresponds to an element of $G$ and each edge $xy$, $x\in G, y\in G$ corresponds to $y=xa$ where $a$ is a [[Subgroup|generator]] of $G$. We overlay multiple such edge types for each element in some generating set $S$. 
* If we are considering only subgraphs of a Cayley digraph using generating set $C\subseteq S$, we use the notation $\text{Cay}(G,C)$.  In such a case, the arc set is defined as  
  $$
  \set{(g,h) : g^{-1}h \in C}
  $$


* A Cayley Digraph necessarily and sufficiently satisfies the following properties.
	* (*Godsil 3.7.4*) The digraph using the entire generating set $S$ (i.e, $\text{Cay}(G,S)$) is necessarily [[Graph Connectivity|connected]] because every linear equation in the group has a solution.
	* The digraph has at most one arc from $g$ to $h$ because the solution $gx=h$ is unique. 
	  
	  That is, another way to formulate the digraph is via the arc set
	  $$
	  \set{(g,h) \mid hg^{-1} \in S}
	  $$
	  Where $S\subseteq G$. 

	* Each vertex $g$ has exactly one arc of each type starting at $g$ and one arc of each type ending at $g$ because the products are unique. 
	* If two different sequences of arc types starting from $g$ lead to the same vertex $h$, then those same arc types starting from any vertex $u$ will lead to $v$. 
	  
	  If $gq=h, gr=h$, then $uq=ug^{-1}h=ur$

* (*Godsil 3.1.2*) Cayley graphs are [[Vertex Transitive Graph|vertex transitive]]. 


* (*Godsil 3.7.1; Godsil 3.7.2*) Let $G$ be a group and $C$ an inverse-closed subset of $G-\set{e}$. Then the [[Group Automorphism|automorphism group]] $\text{Aut}(\text{Cay}(G,C))$ contains a [[Regular Group|regular]] subgroup [[Group Isomorphism|isomorphic]] to $G$.  
  
  Conversely if a group $G$ acts regularly on the vertices of $X$, then $X$ is a Cayley graph for $G$ relative to some inverse closed subset of $G-\set{e}$. 
	* *Proof*: The forward direction follows by considering the permutation $\lambda_g$. It can be shown that $\forall g\in G: \  \lambda_g \in\text{Aut}(\text{Cay}(G,C))$. The left regular permutations $\set{\lambda_g\mid g\in G}$ form a subgroup isomorphic to $G$.  
	  
	  The converse is shown as follows. Fix $u\in X$ and choose $v\in X$. Because $G$ is regular, it is transitive thus, there exists $g\in G$ such that $gu = v$. 
	  
	  Let $C_v=\set{g^nv\mid n\in \mathbb{Z}^+}$. These classes ([[Subgroup|formed via the generators of ]] $G$) determine subgraphs in the Cayley graph. Inverse closure is provided because $G$ is transitive. 


* (*Godsil 3.7.3*) If $\theta$ is an [[Group Automorphism|automorphism]] of $G$, then  
  $$
  \text{Cay}(G,C)\cong \text{Cay}(G,\theta(C))
  $$ 
* (*Godsil 3.8.1*) Let $\alpha,\beta$ be generators of $G$ and $X=X(G,\set{\alpha,\beta})$ be the directed Cayley graph of $G$. Also suppose that $\alpha, \beta$ have $k$ and $l$ [[Trails, Walks, Paths and Cycles|cycles]] respectively, in their action by left multiplication on $G$. If $\text{ord}(\beta^{-1}\alpha$} is odd and $V(x)$ has a partition into $r$ disjoint directed cycles, then $r,k,l$ have the same parity. 
	* *Proof*: Consider a permutation $\pi$ such that $\pi(x)=y$ if $(x,y)$ is in one of the directed cycles. Define the partitions as $P=\set{x \mid \pi x = \alpha x}$ and $Q=\set{x\mid \pi x = \beta x}$. 
	  
	  The permutation $\tau$ defined by $\tau(x)=\beta^{-1}\pi(x)$ fixes every element of $Q$ and so fixes $P$. Thus for any $x\in P, \tau(x) = \beta^{-1}\alpha x$. $\text{ord}(\beta^{-1}\alpha)$ is odd then so is $\tau$. Thus, $\tau$ is an even permutation.
	  
	  The result follows by considering that the parity of a permutation on $n$ elements with $r$ cycles equals the parity of $n+r$.  Here $k+r$ and $l+r$ are both even so $r,k,l$ share the same parity. 

* (*Godsil 3.8.2*) If $n$ is even and $n\ge 4$, then the directed Cayley graph corresponding to $\text{Sym}(n)$ is not [[Hamiltonian Graph|Hamiltonian]]. 
	* *Proof*: If $n$ is even, the vertices can be partitioned into an even number of directed cycles, which means there are no Hamiltonian cycles. 

* (*Godsil e3.9*) Let $G$ be an [[Abelian Group|Abelian group]] and $C$ an inverse closed subset of $G-\set{e}$. If $|C|\ge 3$ then $\text{Cay}(G,C)$ has girth of at most $4$.
	* *Proof*:: Let $g_i\in C$ and $h\in G$.  A cycle of length $4$ can always be formed as follows assuming $|C|>3$
	  $$
	  \begin{split}
	  h &\to& g_1h &\to& g_2 g_1 h&\to& g^{-1}_1 g_2g_1h &\to& g_2^{-1}g_1^{-1}g_2g_1 h \\
	  h &\to& g_1h &\to& g_2g_1h&\to& g_2 h&\to& h
	  \end{split}
	  $$
	  If $|C|=3$ then we have at least one element $g_1$ such that $g_1=g_1^{-1}$. The above cycle can still be formed by replacing $g_1^{-1}$ with $g_1$.

* (*Godsil e3.10*) Let $C$ be an inverse-closed subset of $G-\set{e}$. If $G$ is Abelian and contains an element $g$ such that $\text{ord}(g)\ge 3$, then $|\text{Aut}(\text{Cay}(G,C))| \ge 2|G|$ 
	* *Proof*: By (*Godsil 3.7.1*) $\text{Aut}(\text{Cay}(G,C))$ contains a regular subgroup $H\cong G$.   Let $\phi$ be the automorphism defined by $\phi(x)=x^{-1}$.  Clearly this preserves adjacency since $\phi(cx)= (cx)^{-1}= x^{-1}c^{-1} = c^{-1}x^{-1}=\phi(c)\phi(x)$ so it is a [[Graph Automorphism|graph automorphism]].  
	  
	  $\phi$ is non-trivial because $\phi(g)=g^{-1}\ne g$.  
	  
	  Also $\phi\notin H$. Otherwise  for any $h\in G$  
	  $$
	  \phi(x)=\lambda_h(x)\implies x^{-1}=hx\implies x^2 = h^{-1} \implies h=x^{-2}
	  $$
	  So it is always possible to find an element for which left multiplication does not map to the inverse. Alternatively $x^{-2}=k$ for all $x$ but this contradicts the existence of $g$. Therefore $\phi$ is not  a left multiplication and the subgroup formed by $\set{e,\phi}$ gives us our second subgroup. By Lagrange's Theorem, we get our bound.  
# Links
* [[Algebraic Graph Theory by Godsil and Royle]]
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh]]

