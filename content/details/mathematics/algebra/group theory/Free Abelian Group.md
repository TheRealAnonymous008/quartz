* (*Fraleigh 38.1*) Let $X$ be a subset of a nonzero [[Abelian Group|Abelian Group]] $G$.  The following are equivalent [^matroid]
	* Each nonzero element $a\in G$ can be expressed uniquely, up to order of summands, in the form 
	  $$
	  a = \sum n_i x_i 
	  $$
	  For $n_i\ne 0$ in $\mathbb{Z}$ and distinct $x_i\in X$. 
	* $X$ generates $G$ and $\sum n _ix_i = 0$ for $n_i\in\mathbb{Z}$ and distinct $x_i\in X$ if and only if $n_1 = n_2 = \dots = n_r = 0$.

[^matroid]: For an analogous concept, see [[Matroid Theory]]. We may think of this theorem as talking about linear independence.

* An Abelian group having a [[Group Action|generating set]] $X$ satisfying the conditions in (*Fraleigh 38.1*) is called a **Free Abelian Group**. $X$ is called the **[[Vector Space|basis]]** for the group.
* Another way to define it is using [[Free Group|free groups]] and [[Factor Group|factor groups]].  Let $X$ be the basis, $G$ a free abelian group,  $F[X]$ a free group on $X$ and  $C$ the [[Commutator Group|commutator]] subgroup of $F[X]$. Then
  $$
  G\cong F[X]/  C
  $$

* (*Fraleigh 38.5*) If $G$ is a nonzero free abelian group with a basis of $r$ elements, then 
  $$
  G \cong \mathbb{Z}^r 
  $$
* (*Fraleigh 38.6*) Let $G\ne \set{0}$ be a free abelian group with a finite basis. Then every basis of $G$ is finite and all bases of $G$ have the same number of elements (see [[Linear Combination|Fraleigh 30.20]]). 

* If $G$ is a free abelian group, then the **rank** of $G$ is the number of elements in a basis for $G$. 

* (*Fraleigh 38.8*) Let $G$ be a finitely generated abelian group with generating set $\set{a_1,\dots, a_n}$. Let 
  $$
  \phi : \mathbb{Z}^n \to G
  $$
  be defined by 
  $$
  \phi(h_1,h_2,\dots, h_n) = h_1a_1 + \dots + h_n a_n
  $$
  Then $\phi$ is a [[Group Homomorphism|homomorphism]].

* (*Fraleigh 38.9*) **Basis Replacement Theorem** If $X=\set{x_1,\dots,x_r}$ is a basis for a free abelian group $G$ and $t\in \mathbb{Z}$. Then for $i\ne j$, the set
  $$
  Y= \set{x_1,\dots,x_{j-1}, x_j + tx_i, x_j, x_{j+1}, \dots x_r}
  $$
  Is also a basis for $G$. Note we removed $x_i$ from $X$ and replaced it with $x_j + tx_i$. 

* (*Fraleigh 38.11*) Let $G\ne \set{0}$ be a nonzero abelian group of finite rank $n$ and let $K$ be a nonzero subgroup of $G$. Then $K$ is free abelian of rank $s\le n$. 
  
  Also, there exists a basis $\set{x_1,\dots,x_n}$ for $G$ and positive integers $d_1,\dots,d_s$ where $d_i$ divides $d_{i+1}$ for $i=1,\dots,s-1$ such that 
  $$
  \set{d_1x_1,d_2x_2,\dots,d_sx_s}
  $$
  is a basis for $K$.
	* *Idea*: Clearly a basis $X$ for $G$ is also a basis for $K$. The general idea will be to construct a new basis $Y=\set{x_1 ,\dots, x_s, y_{s+1},\dots, y_{n}}$ in $G$ such that for all non-zero $w\in K$, we have
	  $$
	  w= k_1x_1 + \dots + k_sx_s 
	  $$
	  That is, the coefficients for each $y_i$ is $0$.  
	  The basis can be constructed iteratively. In particular, starting with a basis $Y_1$ and a potential reordering of elements in the basis, derive, using an element $w_1\in K$ a constant $d_1$ such that $d_1x_1 \in K$ (via the [[Number Theory|division algorithm]]).
	  
	  Now each element of $K$ can be expressed as a sum of a multiple of $d_1x_1$ and the rest of the elements in the bases. From these elements, repeat the process above and obtain $d_2x_2,\dots, d_sx_s$. The process terminates when the only element in $K$ that remains is $0$. Also from the repeated subtraction we have $d_i$ divides $d_{i+1}$.


* (*Fraleigh e38.10*) A free abelian group contains no nonzero elements of finite order
	* *Idea*: Any such element $a\in G$ will satisfy $a^n = e$. Also, clearly $a^{2n}=e$. Therefore $a^{2n}-a^n = 0$. Thus, the abelian group is not free. 
# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh]]