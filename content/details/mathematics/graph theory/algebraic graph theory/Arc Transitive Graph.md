* A graph is **[[Arc Transitive Graph|Arc Transitive]]** if its [[Graph Automorphism|automorphism group]] acts transitively on its [[Directed Graph|arcs]] (i.e., ordered pairs of adjacent vertices). 
	* An **$s$-arc** in a graph is a sequence of vertices $(v_0, \dots, v_s)$ such that consecutive vertices are adjacent and $v_{i-1}\ne v_{i+1}$. 
	  
	  A graph is **$s$-arc transitive** if its automorphism group is transitive on $s$-arcs. That is, the stabilizer on $u\in V(X)$ $G_u$ acts transitively on all $s$-arcs with vertices starting at $u$.
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
	* Arc transitive graphs are necessarily [[Vertex Transitive Graph|vertex]] and [[Edge Transitive Graph|edge]] transitive. However, the converse is not necessarily true.


* (*Godsil 3.2.2*) If a graph $X$ is vertex and edge transitive, but not arc transitive, the degree of all vertices is even (i.e., it is [[Eulerian Graph|Eulerian]] assuming connectivity).  [^duality] 
	* If $X$ is  arc transitive, then the degree of all vertices is odd.
	* *Proof*: Let $G=\text{Aut}(X)$ and $x,y\in V(X)$ such that $xy\in E(X)$. Also let $\Omega$ be the orbit on $G$ containing $(x,y)$. 
	  
	  $X$ is edge transitive, therefore every arc can be mapped by automorphism to either $(x,y)$ or $(y,x)$. 
	  
	  $X$ is not arc transitive, therefore $(y,x)\notin \Omega$ and thus $X$ is the graph with the edge set $\Omega \cup \Omega^T$ 
	  
	  The out-degree of $x$ is the same in both $\Omega$ and $\Omega^T$ we have that $x$ is even.  

[^duality]: Note how (*Godsil 3.2.1*) and (*Godsil 3.2.2*) Deal with bipartite and Eulerian graphs. Both are edge transitive but one is vertex transitive while the other not. See [[Graph Duality|graph]] and [[Matroid Duals|matroid]] duality for more on this.


* (*Godsil 4.1.3*) **Tutte's Theorem** If $X$ is $s$-arc transitive graph with degree at least $3$ and girth $g$, then $g\ge 2s-2$
* (*Godsil 4.1.4*) **Tutte's Theorem** If $X$ is an $s$-arc transitive graph with girth $2s-2$ it is [[Bipartite Graph|bipartite]] with diameter $s-1$.

* If $X$ is $s$-arc transitive, then $X^{(s)}$ is [[Vertex Transitive Graph|vertex transitive]].

* (*Godsil 4.2.1*) Let $X$ and $Y$ be directed graphs and $f:V(X)\to V(Y)$ a [[Graph Homomorphism|homomorphism]] such that every edge $Y$ is the image of an edge in $X$. Let $y_0,\dots, y_r$ be a path in $Y$. Then for each $x_0\in V(X)$ such that $f(x_0)=y_0$, there is a path $x_0,\dots, x_r$ such that $f(x_i)=y_i$
* (*Godsil 4.2.2*) If $X$ is a connected graph with minimum degree  two that is not a cycle, then $X^{(s)}$ is strongly connected for all $s\ge 0$. 

* (*Godsil 4.3.1*) Let $X$ be a strongly connected digraph and $G$ a [[Transitive Group|transitive]] subgroup in its [[Graph Automorphism|automorphism group]]. If there is a vertex $u\in V(X)$ such that $G_x$ restricted on $N(u)$ is an identity, then $G$ is [[Regular Group|regular]]. 

* A graph is **$s$-arc regular** if for any two $s$-arcs, there is a unique automorphism mapping the first to the second.

* (*Godsil 4.3.2*) Let $X$ be a connected cubic graph that is $s$-arc transitive but not $(s+1)$-arc transitive. Then $X$ is $s$-arc regular
* (*Godsil 4.3.3*) **Tutte's Theorem** If $X$ is an $s$-arc regular cubic graph then $s\le 5$. 
* (*Godsil 4.3.4*) If $X$ is an arc transitive cubic graph, $v\in V(X)$ and $G=\text{Aut}(X)$, then $|G_v|$ divides $48$ and is divisible by $3$.

* (*Godsil 4.5.3*) A connected $s$-arc transitive graph with girth $2s-2$ is [[Distance Transitive Graph|distance transitive]] with diameter $s-1$.
# Links
* [[Algebraic Graph Theory by Godsil and Royle]]