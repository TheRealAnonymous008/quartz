* A subset $W$ of a [[Vector Space]] $V$ over a field $F$ is called a **subspace** of $V$ if $W$ is a vector space over $F$ under the operations of addition and scalar multiplication defined in $V$
  
  We denote this as $W\le V$ [^group_theory]

[^group_theory]: Subspaces are generalized by [[Subgroup|subgroups]].

* (*Frieidberg 1.3*) Let $V$ be a vector space and $W$ a subset of $V$. Then $W\le V$ if and only if the following hold:
	* $0\in W$
	* $x\in W \wedge y\in W \implies x+y\in W$
	* $a\in F \wedge x\in W \implies ax\in W$
* (*Friedberg 1.4*) Any intersection of subspaces of $V$ is a subspace of $V$. 
  
  $$
  X,Y\le V \implies X\cap Y \le V
  $$

* (*Friedberg e1.3.18*) Let $W_1,W_2\le V$, then $W_1\cup W_2 \le V$ if and only if $W_1 \le W_2$ or $W_2 \le W_1$ 
* (*Friedberg e1.3.20*) If $W\le V$ and $x_1,\dots,x_n\in W$ then for any scalars $a_1,\dots,a_n\in F$
  
  $$
  a_1x_1 +\dots + a_nx_n \in W
  $$

* (*Friedberg e1.3.21*) If $W_1,W-2 \le V$, then $W_1 + W_2$ is the smallest subspace containing both $W_1$ and $W_2$

* (*Friedberg 1.11*) If $V$ is finite dimensional, then $W\le V$ is finite dimensional, and $\dim(W)\le \dim(V)$. 
  
  Moreover, $\dim(W)=\dim(V) \implies W=V$
	* (*Friedberg 1.11.1*) Any [[Linear Combination|basis]] for $W$ is a subset of a basis in $V$. 

* A [[Cosets, Group Indices|coset]] for vector spaces can be defined as follows. Let $W\le V$. For any $v\in V$, the set 
  $$
  v + W = \{v + w \mid w\in W\}
  $$
  is called the **coset** of $W$ containing $v$. 
	* (*Friedberg e1.3.29a*) $v+W\le W$ if and only if $v\in W$
	* (*Friedberg e1.3.29c*) The following operations are well defined 
	  $$
	  \begin{split}
	  \forall v_1,v_2 \in V, a\in F \\
	  (v_1 + W) + (v_2 + W) &= (v_1 + v_2) + W \\
	  a (v_1 + W) &= av + W
	  \end{split}
	  $$
	* (*Friedberg e1.3.29d*) We can define the [[Factor Group]] as the vector space $V/W=\{v + W \mid v \in V\}$ 

# Links
 * [[Linear Algebra by Friedberg Insel and Spence]]