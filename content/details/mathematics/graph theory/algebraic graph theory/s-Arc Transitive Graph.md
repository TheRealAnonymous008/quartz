* An **$s$-arc** in a graph is a sequence of vertices $(v_0, \dots, v_s)$ such that consecutive vertices are adjacent and $v_{i-1}\ne v_{i+1}$. 
  
  A graph is **$s$-arc transitive** if its [[Graph Automorphism|automorphism group]] is transitive on $s$-arcs. That is, the stabilizer on $u\in V(X)$ $G_u$ acts transitively on all $s$-arcs with vertices starting at $u$.
	* Let $\alpha(v_0,\dots,v_s)$ be an arc. We define the **head** and **tail** as 
	  $$
	  \begin{split}
	  \text{head}(\alpha) &= (v_1,\dots,v_{s}) \\
	  \text{tail}(\alpha) &= (v_0,\dots,v_{s-1})
	  \end{split}
	  $$
	* If $\alpha$ and $\beta$ are $s$-arcs, then $\beta$ **follows** $\alpha$ if there is an $(s+1)$-arc $\gamma$ where $\text{head}(\gamma)=\beta$ and $\text{tail}(\gamma)=\alpha$. We say that $\alpha$ can be **shunted** onto $\beta$. 
	* $X^{(s)}$ denotes the directed graph with $s$-arcs of $X$ as its vertices such that $(\alpha,\beta)$ is an arc if and only if $\alpha$ can be shunted onto $\beta$.
* An $s$-arc transitive graph is also $(s-1)$-arc transitive.
	* A $0$-arc transitive graph is a vertex transitive graph.
	* A $1$-arc transitive graph is an arc transitive graph or a **symmetric graph**. 


* (*Godsil 4.1.3*) **Tutte's Theorem** If $X$ is $s$-arc transitive graph with degree at least $3$ and girth $g$, then $g\ge 2s-2$
	* *Proof*: Assume $s\ge 3$. $X$ contains a cycle of length $g$ and a path of length $g$ whose end vertices are not adjacent. To see the latter, take vertex $u$ in the cycle. It has degree $3$ therefore it must be adjacent to a vertex  $v$. not in the cycle. The path thus starts at $v$ and travels along the cycle. 
	  
	  No automorphism maps a $g$-arc corresponding to a cycle and a $g$-arc corresponding to a path.  Therefore $s < g$.  Any $s$-arc must lie in a cycle.
	  
	  Consider $v_0,\dots, v_s$ and $v_0,\dots,w$ where $w\ne v_{s-2} \ne v_s$. Delete $v_0, \dots, v_{s-1}$ and the graph contains a cycle of length at most $2g-2(s-2)\ge g$. The result follows. 

* (*Godsil 4.1.4*) **Tutte's Theorem** If $X$ is an $s$-arc transitive graph with girth $2s-2$ it is [[Bipartite Graph|bipartite]] with diameter $s-1$.
	* *Proof*: If $X$ has girth $2s-2$, every $s$-arc lies in at most one cycle of length $2s-2$. $X$ therefore has diameter at least $s-1$. Additionally, if $u\in V(X)$, then there is an $s$-arc, lying in the cycle, joining it to a vertex $v$ in the cycle. Thus $d(u,v)<s$. 
	  
	  If $X$ is not bipartite, it contains an odd cycle. Since the diameter is $s-1$, the cycle must have length $2s-1$. Two adjacent vertices $v,v'$ in the cycle of distance $s-1$ from $u$ forms an $s$-arc which clearly forms a cycle of length $2s-2$ ($u\to v' \to v \to u$) which is a contradiction. 

* If $X$ is $s$-arc transitive, then $X^{(s)}$ is [[Vertex Transitive Graph|vertex transitive]].

* (*Godsil 4.2.1*) Let $X$ and $Y$ be directed graphs and $f:V(X)\to V(Y)$ a [[Graph Homomorphism|homomorphism]] such that every edge $Y$ is the image of an edge in $X$, and it maps the out-neighbors of $x$ to the out-neighbors of $f(x)$. Let $y_0,\dots, y_r$ be a path in $Y$. Then for each $x_0\in V(X)$ such that $f(x_0)=y_0$, there is a path $x_0,\dots, x_r$ such that $f(x_i)=y_i$
	* *Proof*:  Since there always exists $x_i$ such that $f(x_i)=y_i$, what remains is to show that each of the $x_i$ forms a directed path.  Since each $y_i$ has a corresponding $x_i$ and $y_1y_2\implies x_1x_2$. Repeatedly apply the latter to get a path of any length.



* (*Godsil 4.2.2*) If $X$ is a connected graph with minimum degree  two that is not a cycle, then $X^{(s)}$ is [[Directed Graph|strongly connected]] for all $s\ge 0$. 
	* *Idea*:  Treat $\text{head}(\cdot)$ as a homomorphism from $X^{(s+1)}\to X^{(s)}$.  Clearly, every edge of $X^{(s)}$ is an image of an edge in $X^{(s+1)}$ and neighborhoods are also clearly preserved.  Thus, edges and paths are also preserved by (*Godsil 4.2.1* ). Take $a,\beta$ as $(s+1)$-arcs. Argue by induction. By connectivity of $X^{(s)}$, there is a path joining $\text{head}(\alpha)$ to $\text{tail}(\beta)$.   This path is preserved under homomorphism such that $\gamma \mapsto \alpha$ and $\text{head}(\gamma)=\text{tail}(\beta)$. 
	  
	  The proof proceeds by induction. The base case for $s=1$ shows that it is possible to shunt $xy$ onto $yx$. 


* A graph is **$s$-arc regular** if for any two $s$-arcs, there is a unique automorphism mapping the first to the second.

* (*Godsil 4.3.2*) Let $X$ be a connected cubic graph that is $s$-arc transitive but not $(s+1)$-arc transitive. Then $X$ is $s$-arc regular
	* *Proof*: $X^{(s)}$ has degree $2$. Let $G=\text{Aut}(X)$, and $\alpha\in X^{(s)}$. $G$ acts vertex transitively on $X^{(s)}$. 
	  
	  Suppose $G_\alpha$ is non-trivial on the out-neighbors of $\alpha$. $G_\alpha$ must swap the $2$ $s$-arcs following $\alpha$. 
	  
	  By transitivity, map two $(s+1)$-arcs in $X$ to $(s+1)$ arcs that have $\alpha$ as the initial $s$-arc. Thus, $G$ is also transitive on $X^{(s+1)}$ which is a contradiction.
	  
	  Therefore $G_\alpha=\set{e}$ and $G$ is regular by (*Godsil 4.3.1*) 


* (*Godsil 4.3.3*) **Tutte's Theorem** If $X$ is an $s$-arc regular cubic graph then $s\le 5$. 
* (*Godsil 4.5.3*) A connected $s$-arc transitive graph with girth $2s-2$ is [[Distance Transitive Graph|distance transitive]] with diameter $s-1$.
	* *Proof*: By (*Godsil 4.1.4*), the graph has diameter $s-1$.  Therefore, we can map $i$-arcs, $i<s$ to each other by arc transitivity.  Therefore, two vertices remain the same distance and thus the graph is distance transitive.

# Links
* [[Algebraic Graph Theory by Godsil and Royle]]