* A graph is **[[Arc Transitive Graph|Arc Transitive]]** if its [[Graph Automorphism|automorphism group]] acts transitively on its [[Directed Graph|arcs]] (i.e., ordered pairs of adjacent vertices). 

* Arc transitive graphs are necessarily [[Vertex Transitive Graph|vertex]] and [[Edge Transitive Graph|edge]] transitive. However, the converse is not necessarily true.


* (*Godsil 3.2.2*) If a graph $X$ is vertex and edge transitive, but not arc transitive, the degree of all vertices is even (i.e., it is [[Eulerian Graph|Eulerian]] assuming connectivity).  [^duality] 
	* If $X$ is  arc transitive, then the degree of all vertices is odd.
	* *Proof*: Let $G=\text{Aut}(X)$ and $x,y\in V(X)$ such that $xy\in E(X)$. Also let $\Omega$ be the orbit on $G$ containing $(x,y)$. 
	  
	  $X$ is edge transitive, therefore every arc can be mapped by automorphism to either $(x,y)$ or $(y,x)$. 
	  
	  $X$ is not arc transitive, therefore $(y,x)\notin \Omega$ and thus $X$ is the graph with the edge set $\Omega \cup \Omega^T$ 
	  
	  The out-degree of $x$ is the same in both $\Omega$ and $\Omega^T$ we have that $x$ is even.  

[^duality]: Note how (*Godsil 3.2.1*) and (*Godsil 3.2.2*) Deal with bipartite and Eulerian graphs. Both are edge transitive but one is vertex transitive while the other not. See [[Graph Duality|graph]] and [[Matroid Duals|matroid]] duality for more on this.


* (*Godsil 4.3.4*) If $X$ is an arc transitive cubic graph, $v\in V(X)$ and $G=\text{Aut}(X)$, then $|G_v|$ divides $48$ and is divisible by $3$.

* (*Godsil e4.4*) Let $X$ be a vertex transitive cubic graph on $n$ vertices and $G=\text{Aut}(X)$. If $|G_u|\equiv0 \mod 3$ for $u\in V(X)$ then $X$ is arc transitive. 
	* *Proof*:  We show that for any vertex $u$, its neighbors are preserved under automorphism. This coupled with vertex transitivity are sufficient to show arc transitivity since we can map $u$ to any vertex and its neighbors (and thus $1$-arcs) are preserved.
	  
	  By (*[[Group Action Orbital|Godsil 2.4.1]]*), we have $X^2/G\cong X/G_u$. It suffices, therefore, to show that $|X/G_u|=1$. By [[Group Action|Burnside's Lemma]].
	  $$
	  |X/G_u| = \frac{1}{|G_u|} \sum_{g\in G_u} |X^g|
	  $$
	  
	 Consider the neighborhood $N(u)$ and the restriction of the automorphism group on $N(u)$. Clearly any $g\in G$ permutes these neighbors since $g$ preserves adjacency. Thus, the restriction of $G_u$ on $N(u)$ must be a subgroup of $S_3$. Because $|G_u|\equiv 0\mod 3$, the only possibilities for $G_u$ are $C_3$ and $\text{Sym}(3)$. 
	 
	 If $G_u\cong C_3$, $e$ fixes all $3$ neighbors while $g,g^2$ fix none. If $G_u\cong \text{Sym}(3)$, then $e$ fixes all $3$ neighbors, transpositions fix $1$ neighbor, and all other elements fix none. In either case, Burnside's lemma gives us  $|X/G_u| = 1$.



# Links
* [[Algebraic Graph Theory by Godsil and Royle]]