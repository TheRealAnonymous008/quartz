* A graph $X$ is **edge transitive** if its automorphism group acts transitively on $E(X)$.  


* (*Godsil 3.2.1*) Let $X$ be an edge-transitive graph with no isolated vertices. If $X$ is not vertex transitive, then $\text{Aut}(X)$ has exactly two [[Permutations and Orbits|orbits]] and these two orbits form a [[Bipartite Graph|bipartition]] of $X$. That is *all edge transitive graphs that are not vertex transitive are bipartite*.  [^duality]
	* *Proof*: For any edge $(x,y)\in E(X)$ there will be an automorphism  mapping an edge incident to $w\in V(X)$  to $(x,y)$. Here, either $w\mapsto x$ or $w\mapsto y$ under the automorphism but not both. Thus, $x,y$ are part of different orbits.   
	  
	  No automorphism maps $(u,v)$, where $u,v$ lie in the same orbit, to $(x,y)$  above.  Hence the two orbits form a bipartition. 


[^duality]: Note how (*Godsil 3.2.1*) and (*Godsil 3.2.2*) Deal with bipartite and Eulerian graphs. Both are edge transitive but one is vertex transitive while the other not. See [[Graph Duality|graph]] and [[Matroid Duals|matroid]] duality for more on this.

# Links
* [[Algebraic Graph Theory by Godsil and Royle]]