* Let $G$ be a transitive group on $X$. A nonempty subset $S\subseteq X$ is a **block of primitivity** for $G$ if, for any $g\in G$, either $S^g=S$ or $S\cap S^g=\emptyset$.  A partition of $X$ into distinct blocks of primitivity gives a **system of imprimitivity** for $G$ .

* A transitive group with no nontrivial system of primitivity is **primitive** otherwise it is **imprimitive.**
* In other words, *a primitive group acts transitively and the action preserves only the trivial partitions -- $S$ or $|S|$ singletons*.

* (*Godsil 2.5.1*) Let $G$ be a transitive permutation group on $X$ and $x\in X$. Then $G$ is primitive if and only if $\text{Stab}_G(x)$ is a maximal subgroup of $G$

* Motivated by [[Directed Graph|Godsil 2.6.1]], a non-symmetric orbit $\Omega$ is **connected** if the corresponding [[Directed Graph|digraph]], whose vertex set is $X$ and arc set based on $\Omega$, is strongly / weakly connected. 
  
  Both strong / weakly connected conditions are equivalent because $G$ acts transitively so for any vertex, the indegree equals the outdegree.

* (*Godsil 2.6.2*) Let $G$ be a transitive [[Permutations and Orbits|permutation]] group on $X$. Then $G$ is primitive if and only if each non-diagonal orbit is connected. 

* (*Godsil e2.12*) The only primitive permutation group on $X$ that contains a transposition is the [[Symmetric Group|symmetric group]] $\text{Sym}(X)$
	* *Proof*: Let $G$ be a primitive permutation group and $\sigma\in G$ be the transposition of two elements $x,y\in X$.  
	  
	  $G$ is primitive, therefore it is transitive. Thus, there exists a permutation mapping $x\to z$ for all $z\in X$. Let $g$ be this mapping. Then, $g\sigma g^{-1}$ gives us another transposition between $(z, gy)$.
	  
	  Since $G$ is primitive, $\text{Stab}_G(z)$ acts transitively on $X-\set{z}$. Which means, there must exist  $h$ such that $gy\to a$. This lets us generate the transposition $(z,a)$ for arbitrary $z$ and $a$.
	   
	  Since $G$ must contain all transpositions, it must also contain all permutations. It is thus $\text{Sym(G)}$

# Links
* [[Algebraic Graph Theory by Godsil and Royle]]
* [[Group Action]]