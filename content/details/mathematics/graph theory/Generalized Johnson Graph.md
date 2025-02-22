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
	* The **Petersen Graph** is defined as a special Johnson graph $J(5,2)$

	* The **Kneser Graph** is the graph
	  $$
	  K(n,k) = J(n,k,0)
	  $$



* The Johnson graph is a [[Regular Graph|regular graph]] with degree
  $$
  {k\choose i}{n-k\choose k-i}
  $$
	* In fact, it's [[Edge Transitive Graph|edge transitive]]. 

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


* (*Godsil 1.6.2*) If $n\ge k\ge i$, then the [[Graph Automorphism|automorphism]] $\text{Aut}(J(n,k,i))$ contains a [[Subgroup|subgroup]] [[Group Isomorphism|isomorphic]] to $\text{Sym}(n)$.
	* *Idea*: A [[Permutations and Orbits|permutation]] $\sigma$ on sets $A,B$ does not change the size of their intersections. That is
	  $$
	  |A\cap B| = |\sigma A \cap \sigma B| 
	  $$

* (*Godsil e3.2*) The Petersen graph is not a [[Cayley Digraph|Cayley graph]]. In fact, it is the smallest vertex-transitive graph that is not  a Cayley graph.
	* *Proof*: Suppose $\text{Cay}(G,S)$ is a Cayley graph on $10$ elements isomorphic to the Petersen graph. Since $G$ must be order $10$, Either $G=\text{C}_{10}$ or $G=D_5$. In both cases, there are no $5$-cycles, which the Petersen graph contains.  

* (*Godsil 4.1.1*) $J(n,k,i)$ is at least arc-transitive. 
* (*Godsil 4.1.2*) $J(2k+1,k)$ is at least $2$-tarnsitive.

# Links
* [[Algebraic Graph Theory by Godsil and Royle]]
