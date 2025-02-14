* An **[[Group Automorphism|automorphism]]** is an [[Graph Isomorphism|isomorphism]] from graph $G$ to itself. 
  The set of automorphisms of $G$ forms the Automorphism group $\text{Aut}(G)$. 
	* Clearly, by  definition, a group on permutations is a subgroup of the [[Symmetric Group]]. Therefore
	  $$
	  \text{Aut}(G) \le \text{Sym}(V(G))
	  $$
	* For $g\in\text{Sym}(V)$, the graph obtained by applying $g$ is denoted $Y^g$. It is the graph where
	  $$
	  \begin{split}
	  V(Y^g) &= \set{gx : x\in V(Y)} \\
	  E(Y^g) &= \set{(gx,gy) \mid (x,y) \in E(Y)}
	  \end{split}
	  $$
* (*Godsil 1.3.1*) If $x\in V(X)$ and $g\in \text{Aut}(X)$, then
  $$
  \deg(gx) = \deg(x)
  $$
    
  In other words, $\text{Aut}(X)$ *[[Permutations and Orbits|permutes]] the vertices of equal degree among themselves*.
  
  Additionally, In a [[Directed Graph|digraph]], directions are also preserved.
* (*Godsil 1.3.2*) If $x,y\in V(X)$ and $g\in\text{Aut}(X)$, then 
  $$
  d(x,y)=d(gx,gy)
  $$
  In other words *Automorphisms preserve distances between vertices*.
* (*Godsil 1.3.3*) $\text{Aut}(X)=\text{Aut}(\overline X)$. (see [[Operations on Graphs|graph complements]]).
* Clearly, $\text{Aut}(X)\le \text{End}(X)$.


* $\mathbb{Z}_n \times \mathbb{Z}_2 \le \text{Aut}(C_n)$. In fact (*Godsil e2.2*) , 
  $$
  |\text{Aut}(C_n)| = 2n
  $$
	* *Proof*: This can be shown as follows: Vertex $1$ must map to one of $n$ possibilities, say $v_1\mapsto v_k$,. $v_2$ then maps to either $v_{k-1}$ or $v_{k+1}$. This can be continued inductively. 

  
# Links
* [[Algebraic Graph Theory by Godsil and Royle|Godsil and Royle]]