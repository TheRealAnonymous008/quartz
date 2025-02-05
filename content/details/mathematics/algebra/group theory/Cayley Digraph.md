* A **Cayley Digraph** is a [[Directed Graph]] where each vertex corresponds to an element of $G$ and each edge $xy$, $x\in G, y\in G$ corresponds to $y=xa$ where $a$ is a [[Subgroup|generator]] of $G$  (we do not necessarily require all generators to be used). We overlay multiple such edge types for each element in some generating set $S$. 

* A Cayley Digraph necessarily and sufficiently satisfies the following properties.
	* The digraph is necessarily connected because every linear equation in the group has a solution.
	* The digraph has at most one arc from $g$ to $h$ because the solution $gx=h$ is unique. 
	  
	  That is, another way to formulate the digraph is via the arc set
	  $$
	  \set{(g,h) \mid hg^{-1} \in S}
	  $$
	  Where $S\subseteq G$. 

	* Each vertex $g$ has exactly one arc of each type starting at $g$ and one arc of each type ending at $g$ because the products are unique. 
	* If two different sequences of arc types starting from $g$ lead to the same vertex $h$, then those same arc types starting from any vertex $u$ will lead to $v$. 
	  
	  If $gq=h, gr=h$, then $uq=ug^{-1}h=ur$

* (*Godsil 3.1.2*) Cayley graphs are [[Transitive Graph|vertex transitive]]. 

# Links
* [[Algebraic Graph Theory by Godsil and Royle]]
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh]]

