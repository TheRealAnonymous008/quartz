* A graph is **[[Arc Transitive Graph|Arc Transitive]]** if its [[Graph Automorphism|automorphism group]] acts transitively on its [[Directed Graph|arcs]] (i.e., ordered pairs of adjacent vertices). 
	* An **$s$-arc** in a graph is a sequence of vertices $(v_0, \dots, v_s)$ such that consecutive vertices are adjacent and $v_{i-1}\ne v_{i+1}$. 
	  
	  A graph is $s$-arc transitive if its automorphism group is transitive on $s$-arcs. 
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

# Links
* [[Algebraic Graph Theory by Godsil and Royle]]