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

# Isomorphism
* An **[[Group Isomorphism|isomorphism]]** from $G$ to $H$ is a bijection $f:V(G)\to V(H)$ such that if $xy\in E(G)$ , then $f(x)f(y)\in E(H)$. 
	* We say that if an isomorphism between $G$ and $H$ exists, then the two [[Fundamental Constructs of Graph Theory|graphs]] are **isomorphic**, which we denote as $G\cong H$ .
	* Isomorphism is an equivalence class
	* *Adjacency is preserved under isomorphism*.

* Given a graph $X$, the set of graphs isomorphic to $X$ forms an isomorphism class which partition the set of graphs with vertex set $V$ (where $|V|=n$) 
  
  Isomorphism classes are [[Permutations and Orbits|orbits]] of $\text{Sym}(V(X))$ with the [[Group Action|action]] defined on the subsets of $E(K_n)$. 
	* (*Godsil 2.3.1*) The size of the isomorphism class containing $X$ is 
	  $$
	  \frac{n!}{|\text{Aut}(X)|}
	  $$
		* *Proof*: From the Orbit-Stabilizer Theorem. There are $n!$ permutations and $|\text{Aut}(X)|=|\text{Stab}_{\text{Sym}(V)}(X)|$   by the definition of an [[Graph Automorphism|automorphism]].
	* (*Godsil 2.3.2*) The number of isomorphism classes of graphs on $n$ vertices is at most.
	  $$
	  (1 + o(1)) \frac{2^{n \choose 2}}{n!}
	  $$
		* *Idea*: Show that among the permutations of $\text{Sym}(V)$ with size $2r$, the maximum value of $\lg |V^g|$ is realized by the permutation with exactly $r$ cycles of length $2$. 
		  
		  Let  $g\in \text{Sym}(V)$. An orbit of $g$ corresponds to a clique of the vertices within the orbit. Hence, if $g$ has $r$ orbits on $E(K_n)$, then $g$ fixes $2^r$ graphs (every possible choice of clique subgraphs to include). 
		  	  
		  Fix an even integer $m\le n-2$ and divide $\text{Sym}(V)$ into three classes -- the identity, the permutations containing support of size at most $m$ and the rest. The size of each class is given as 
		  $$
		  \begin{split}
		  |C_1| &= 1 \\
		  |C_2| &\le {n\choose m}m ! &< n^m \\
		  |C_3| &< n! &< m
		  \end{split}
		  $$
		  Elements $g_2\in C_2$ and $g_3\in C_3$ have orbit counts bounded as follows
		  $$
		  \begin{split}
		  \lg |V^{g_2} | &\le {n\choose 2} - (n-2) \\
		  \lg |V^{g_3} | &= {n\choose 2} - \frac{m}{2}\left(n-\frac{m}{2} - 1\right) &\le {n\choose 2} - \frac{nm}{4} 
		  \end{split}
		  $$
		  The result follows using Burnside's lemma. 

# Links
* [[Introduction To Graph Theory by Wilson]]
* [[Algebraic Graph Theory by Godsil and Royle]]

* [[Fundamental Constructs of Group Theory]]
* [[Families of Graphs]]