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
	* The **Odd Graph** is the Kneser graph 
	  $$
	  O_k= K(2k-1, k-1)
	  $$
		* Each edge in an odd graph has an "odd one out". 



* The Johnson graph is a [[Regular Graph|regular graph]] with degree
  $$
  {k\choose i}{n-k\choose k-i}
  $$
	* In fact, it's [[Edge Transitive Graph|edge transitive]]. 

* For any vertex in $J(n,k,i)$ say $u=\set{1,\dots,k}$ the [[Group Action|stabilizer]] follows
  $$
  \text{Sym}(k) \times \text{Sym}(n-k) \le G_u
  $$
  Clearly, any permutation which permutes the $k$ elements in $u$ and the $n-k$ elements not in $u$ is an element of $G_u$.
  

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

* (*Godsil 4.1.1*) $J(n,k,i)$ is at least arc-transitive.
	* *Proof*: Any two vertices in $J(n,k,i)$ that meet at a vertex $v$ can be mapped to each other via $\text{Sym}(k)\times \text{Sym}(n-k)$. 

* (*Godsil 4.1.2*) $K(2k+1,k)$ is at least $2$-transitive.
	* *Proof*: Consider two $2$-arcs $(u,x_1, x_2)$ and $(u,y_1,y_2)$. By definition, we know that WLOG, we may represent each vertex as 
	  $$
	  \begin{split}
	  u&=\set{1,\dots,k}\\ 
	  x_1&= \set{k+1,\dots 2k} \\ 
	  y_1 &= \set{k+1,\dots,2k-1,2k+1} \\
	  x_2 &= \set{1,\dots, k-1, 2k+1} \\
	  y_2 &= \set{1,\dots, k-1, 2k}
	  \end{split}
	  $$
	  Thus $G_u$ acts transitively on the $2$-arcs.

* (*Godsil 4.5.1*) $J(n,k)$ is [[Distance Transitive Graph|distance transitive]].
	* *Proof*: We show that $d(u,v)=i\iff |u\cap v|=k-i$.  Thus, the automorphism on $J(n,k)$ acts distance transitively. 
	  
	  First suppose $d(u,v)=i$.  Note that if $d(u,v)=1$, then $|u\cap v|=k-1$ by definition. Argue by induction and suppose $d(u,v)=i-1\implies |u\cap v| = k-i+1$. WLOG, $u=\set{1,\dots, k}$ and $v=\set{1,\dots,k-i+1, k + 1,\dots k+i-1}$ 
	  
	  Now, consider $v'$ adjacent to $v$. $|v\cap v'|=k-1$ so they only differ by exactly one element. In  fact,  $v$ and $v'$ differ by an element in $\set{1,\dots,k-i+1}$ as if they differed in $\set{k+1,\dots, k+i-1}$ we would get $d(u,v')=i-1$.  WLOG, replace $k-i+1$ with $k+i$ and clearly $d(u,v')=i$ as was to be shown.
	  
	  Conversely, suppose $|u\cap v|=k-i$.  Clearly if $|u\cap v|=k-1$ then $u$ is adjacent to $v$. Again, argue by induction but this time on $i$ so that $|u\cap v|=k-i+1\implies d(u,v)=i-1$. Take $v'$ such that $|u\cap v'|=k-i < |u\cap v|$Therefore, using transitivity, we can ensure that $u\cap v' \subset u\cap v$. In fact 
	  $$
	  u\cap v = (u\cap v') \cup \set{x}
	  $$
	  Therefore $v$ is adjacent to $v'$. They must differ by exactly one element. By extension $d(u,v')\ge i$.  Also, clearly $d(u,v')\le i$ since we can construct the path where we iteratively replace the last $i$ elements. Both inequalities give us the desired result.   
 
* (*Godsil 4.5.2*) The odd graph $O_k$ is distance transitive.
	* *Proof*:  Observe that any path in $O_k$ corresponds to the addition of $1$ vertex and the removal of another vertex.  Clearly, any automorphism which preserves what vertex gets added and removed works and preserves paths. Hence, they preserve distance and so $O_k$ is distance transitive.
# Petersen Graph
* The **Petersen Graph** is defined as a special Kneser graph $K(5,2)$
![[Petersen Graph.png|300]]
<figcaption> The Petersen Graph By Leshabirukov - Own work by uploader based on http://en.wikipedia.org/wiki/File:Heawood_Graph.svg, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=5788203 </figcaption>


* (*Godsil e3.2*) The Petersen graph is not a [[Cayley Digraph|Cayley graph]]. In fact, it is the smallest vertex-transitive graph that is not  a Cayley graph.
	* *Proof*: Suppose $\text{Cay}(G,S)$ is a Cayley graph on $10$ elements isomorphic to the Petersen graph. Since $G$ must be order $10$, Either $G=\text{C}_{10}$ or $G=D_5$. In both cases, there are no $5$-cycles, which the Petersen graph contains.  
* (*Godsil 4.4.1*) The Petersen graph cannot be $3$-edge [[Graph Coloring|colored]].
* The Petersen graph is distance transitive.

# Links
* [[Algebraic Graph Theory by Godsil and Royle]]
