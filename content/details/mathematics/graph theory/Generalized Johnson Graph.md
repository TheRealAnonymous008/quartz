* A **Generalized Johnson Graph** denoted $J(n,k,i)$ is defined as follows for $n\ge k\ge i$. Let $\Omega$ be a set of size $n$. Then
  $$
  \begin{split}
  V(J(n,k,i)) &= \set{A\in \mathcal{P}(\Omega) \mid |A| =k} \\
  E(J(n,k,i)) &= \set{(A,B) \mid |A\cap B| = i}
  \end{split}
  $$
	* The **Johnson Graph**  is defined as 
	  $$
	  J(n,k) = J(n,k,k-1)
	  $$
	* The **Kneser Graph** is the graph
	  $$
	  K(n,k) = J(n,k,0)
	  $$



* The Johnson graph is a [[Families of Graphs|regular graph]] with degree
  $$
  {k\choose i}{n-k\choose k-i}
  $$
* (*Godsil 1.6.1*) if $n\ge k \ge i$, then 
  $$
  J(n,k,i)\cong J(n,n-k,n-2k+i)
  $$
	* *Proof*: Let $f:\mathcal{P}(\Omega) \to \mathcal{P}(\Omega)$ map from $k$ sets to their complements. This map is an isomorphism. 
	  
	  Every $k$-set has a unique complement, which is an $n-k$-set. 
	  
	  Also, if $A,B$ are $k$-sets where $|A\cap B| = i$ then 
	  $$
	  |\overline{A}\cap \overline{B}| = |\overline{(A\cup B)}| = n-|A\cup B| = n-(|A|+|B|-|A\cap B|) = n -2k +i
	  $$
	  The converse is also true: If $A,B$ are $(n-k)$-sets, then the intersection of their complements has magnitude $i$.


* (*Godsil 1.6.2*) If $n\ge k\ge i$, then the [[Graph Homomorphism|automorphism]] $\text{Aut}(J(n,k,i))$ contains a [[Subgroup|subgroup]] [[Group Isomorphism|isomorphic]] to $\text{Sym}(n)$.
	* *Idea*: A [[Permutations and Orbits|permutation]] $\sigma$ on sets $A,B$ does not change the size of their intersections. That is
	  $$
	  |A\cap B| = |\sigma A \cap \sigma B| 
	  $$




# Links
* [[Algebraic Graph Theory by Godsil and Royle]]
