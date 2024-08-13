* A **vector space** $V$ over a [[Field]] $F$ consists of a [[Set Theory|set]] on which two operations $+$ and $\cdot$ (respectively called vector addition and scalar multiplication) are defined so that 
  
  $$
  \forall x,y\in V \ \ \exists \ x +y \in V
  $$
  and
  $$
  \forall a\in F, x\in V \ \ \exists \ ax\in V 
  $$
  such that the following axioms hold $\forall x,y,z\in V, a,b\in F$
	* $x+y = y+ x$
	* $(x+y)+z = x+(y+z)$ 
	* $\exists 0\in V$ such that $x+0=x$ 
	* $\forall x \ \exists  -x$ such that $x+(-x) = 0$
	* $1 \cdot x = x$
	* $(ab)x = a(bx)$
	* $a(x+y) = ax+ay$
	* $(a+b)x = ax +bx$

* (*Friedberg 1.1*) - If $x,y,z\in V$ such that $x+z=y+z$, then $x=y$
* (*Friedberg 1.1.1*) - The $0$ vector is unique
* (*Friedberg 1.1.2*) - The additive inverse of $x$ is unique.

* (*Friedberg 1.2*) In any vector space $V$, the following are true
	* $\forall x\in V, 0x=0$
	* $\forall a\in F, x\in V \ \ (-a)x = -(ax)=a(-x)$ 
	* $\forall a\in F, a0 = 0$ 

# Sums and Direct Sums
* If $S_1,S_2$ are nonempty subsets of $V$. The **sum** of $S_1$ and $S_2$ is the set
  
  $$
  S_1 + S_2 = \{x+y \mid x\in S_1, y\in S_2 \}
  $$
* A vector space $V$ is said to be the **[[Direct Product of Groups|direct sum]]** of $W_1$ and $W_2$, denoted $V=W_1\oplus W_2$ if $W_1,W_2\le V$ such that $W_1\cap W_2 = \{0\}$ and $W_1 + W_2 = V$
* (*Friedberg e1.6..20*) If $W_1, W_2$ are finite dimensional subspaces such that $V=W_1+W_2$. Then $V$ is also finite dimensional and
  $$
  \text{dim}(W_1+W_2) = \dim(W_1) + \dim(W_2) - \dim(W_1\cap W_2)
  $$
  Moreover, $V=W_1\oplus W_2$ if and only if
  $$
  \dim(V) = \dim(W_1) + \dim(W_2)
  $$
* (*Friedberg e1.6.24*) If $W_1\le V$ where $V$ is finite-dimensional, then there is a subspace $W_2\le V$ such that $V=W_1\oplus W_2$ 
	* *Intuition*: A basis of $W_1$ is linearly independent in $V$. Such a set can be extended to a basis in $V$. The vectors we add to such a basis defines the subspace $W_2$.



# Topics
* [[Vector Subspace]]
* [[Linear Combination]]
# Links
* [[Linear Algebra by Friedberg Insel and Spence]]