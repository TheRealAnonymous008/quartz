* A [[Group Homomorphism|homomorphism]] between graphs $X$ and $Y$ is a mapping $f:V(X)\to V(Y)$ such that 
  $$
  xy\in E(X) \implies f(x)f(y) \in E(Y) 
  $$
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

# Retracts
* A homomorphism $f:V(X)\to V(Y)$ is a **retraction** from $X$ to  $Y$, where $Y\le X$ if  
  $$
  f(V(Y))=V(Y)
  $$ 
  
  If a retraction exists, we say $Y$ is a **retract** of $X$. 

# Topics
* [[Graph Isomorphism]]
* [[Graph Automorphism]]

# Links
* [[Introduction To Graph Theory by Wilson]]
* [[Algebraic Graph Theory by Godsil and Royle]]

* [[Fundamental Constructs of Group Theory]]
* [[Families of Graphs]]