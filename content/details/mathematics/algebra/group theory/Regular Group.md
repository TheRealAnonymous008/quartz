
* A permutation group $G$ acting on $X$ is **semiregular** if no non-identity element of $G$  fixes a point of $X$.
	* If $G$ is semiregular, then all all orbits have length equal to $G$. 
* A permutation group is **regular** if it is semiregular and [[Transitive Group|transitive]]. 
	* If $G$ is regular on $X$, then $|G|=|X|$. 
	* The group $G$ acts on itself regularly. 

* (*Godsil 3.7.1; Godsil 3.7.2*) Let $G$ be a group and $C$ an inverse-closed subset of $G-\set{e}$. Then the [[Group Automorphism|automorphism group]] $\text{Aut}(X(G,C))$ contains a regular subgroup [[Group Isomorphism|isomorphic]] to $G$.  
  
  Conversely if a group $G$ acts regularly on the vertices of $X$, then $X$ is a [[Cayley Digraph|Cayley graph]] for $G$ relative to some inverse closed subset of $G-\set{e}$. 
	* *Proof*: The forward direction follows because the Cayley graph is [[Vertex Transitive Graph|vertex transitive]].
	  
	  The converse is shown as follows. Fix $u\in X$ and choose $v\in X$. Because $G$ is regular, it is transitive thus, there exists $g\in G$ such that $gu = v$. 
	  
	  Let $C_v=\set{g^nv\mid n\in \mathbb{Z}^+}$. These classes (the [[Subgroup|formed via the generators of ]]) $G$ determine subgraphs in the Cayley graph. Inverse closure is provided because $G$ is transitive. 


# Links
* [[Algebraic Graph Theory by Godsil and Royle]]

* [[Group Action]]
* [[Symmetric Group]]