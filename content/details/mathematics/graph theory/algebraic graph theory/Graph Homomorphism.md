* A [[Group Homomorphism|homomorphism]] between graphs $X$ and $Y$ is a mapping $f:V(X)\to V(Y)$ such that 
  $$
  xy\in E(X) \implies f(x)f(y) \in E(Y) 
  $$
	* A homomorphism $f:V(X)\to V(Y)$ is a **retraction** from $X$ to  $Y$, where $Y\le X$ if  
	  $$
	  f(V(Y))=V(Y)
	  $$ 
	  
	  If a retraction exists, we say $Y$ is a **retract** of $X$. 
	* For digraphs, homomorphisms preserve direction. That is  
	  $$
	  (x,y) \in E(X) \implies (f(x), f(y))\in E(Y)
	  $$
* (*Godsil e1.4*) If $f$ is a homomorphism from $X$ to $Y$ and $x_1,x_2\in V(X)$. Then
  $$
  d_X(x_1,x_2)\ge d_Y(f(x_1), f(x_2))
  $$


* An **endomorphism** is a homomorphism of the form $f:V(X)\to V(X)$.
  
  The set of all endomorphisms of $X$ is the **endomorphism monoid** $\text{End}(X)$. 

* An **[[Group Isomorphism|isomorphism]]** from $G$ to $H$ is a bijection $f:V(G)\to V(H)$ such that if $xy\in E(G)$ , then $f(x)f(y)\in E(H)$. 
	* We say that if an isomorphism between $G$ and $H$ exists, then the two [[Fundamental Constructs of Graph Theory|graphs]] are **isomorphic**, which we denote as $G\cong H$ .
	* Isomorphism is an equivalence class
	* *Adjacency is preserved under isomorphism*.

# Automorphism
* An **[[Group Automorphism|automorphism]]** is an isomorphism from graph $G$ to itself. 
  The set of automorphisms of $G$ forms the Automorphism group $\text{Aut}(G)$. 
	* Clearly, by  definition, a group on permutations is a subgroup of the [[Symmetric Group]]. Therefore
	  $$
	  \text{Aut}(G) \le Sym(V(G))
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


* $\mathbb{Z}_n \times \mathbb{Z}_2 \le \text{Aut}(C_n)$. In fact, 
  $$
  |\text{Aut}(C_n)| = 2n
  $$
  Here $\mathbb{Z}_2$ corresponds to the observation that we can map vertex $i$ to $-i$.

  

# Links
* [[Introduction To Graph Theory by Wilson]]
* [[Algebraic Graph Theory by Godsil and Royle]]

* [[Fundamental Constructs of Group Theory]]
* [[Families of Graphs]]