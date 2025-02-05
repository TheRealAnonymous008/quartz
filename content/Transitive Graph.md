# Vertex Transitivity
* A [[Fundamental Constructs of Graph Theory|graph]] $X$ is **vertex transitive** if its [[Graph Automorphism|automorphism group]] [[Group Action|acts]] transitively on $V(X)$. 
* Every vertex transitive graph is [[Families of Graphs|regular]].
* (*Godsil 3.3.3*) If $X$ is a connected vertex-transitive graph, then $\kappa(X)$ is equal to its degree.
* (*Godsil 3.4.2*) A vertex transitive graph $X$ with degree $k$ has vertex [[Graph Connectivity|connectivity]]. 
	$$
	\kappa(X) \ge \frac 23 (k+1)
	$$

# Edge Transitivity
* A graph $X$ is **edge transitive** if its automorphism group acts transitively on $E(X)$.  Similarly, a graph is **arc transitive** if its automorphism group acts transitively on its [[Directed Graph|arcs]] (i.e., ordered pairs of adjacent vertices). 
	* Arc transitive graphs are necessarily vertex and edge transitive. However, the converse is not necessarily true.

* (*Godsil 3.2.1*) Let $X$ be an edge-transitive graph with no isolated vertices. If $X$ is not vertex transitive, then $\text{Aut}(X)$ has exactly two [[Permutations and Orbits|orbits]] and these two orbits form a [[Bipartite Graph|bipartition]] of $X$. That is *all edge transitive graphs that are not vertex transitive are bipartite*. 
	* *Proof*: For any edge $(x,y)\in E(X)$ there will be an automorphism  mapping an edge incident to $w\in V(X)$  to $(x,y)$. Here, either $w\mapsto x$ or $w\mapsto y$ under the automorphism but not both. Thus, $x,y$ are part of different orbits.   
	  
	  No automorphism maps $(u,v)$, where $u,v$ lie in the same orbit, to $(x,y)$  above.  Hence the two orbits form a bipartition. 

* (*Godsil 3.2.2*) If a graph $X$ is vertex and edge transitive, but not arc transitive, the degree of all vertices is even (i.e., it is [[Eulerian Graph|Eulerian]] assuming connectivity).  [^duality] 
	* If $X$ is  arc transitive, then the degree of all vertices is odd.
	* *Proof*: Let $G=\text{Aut}(X)$ and $x,y\in V(X)$ such that $xy\in E(X)$. Also let $\Omega$ be the orbit on $G$ containing $(x,y)$. 
	  
	  $X$ is edge transitive, therefore every arc can be mapped by automorphism to either $(x,y)$ or $(y,x)$. 
	  
	  $X$ is not arc transitive, therefore $(y,x)\notin \Omega$ and thus $X$ is the graph with the edge set $\Omega \cup \Omega^T$ 
	  
	  The out-degree of $x$ is the same in both $\Omega$ and $\Omega^T$ we have that $x$ is even.  

[^duality]: Note how (*Godsil 3.2.1*) and (*Godsil 3.2.2*) Deal with bipartite and Eulerian graphs. Both are edge transitive but one is vertex transitive while the other not. See [[Graph Duality|graph]] and [[Matroid Duals|matroid]] duality for more on this.


# Links
* [[Algebraic Graph Theory by Godsil and Royle]]