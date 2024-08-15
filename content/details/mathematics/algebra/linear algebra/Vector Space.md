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

# Topics
* [[Vector Subspace]]
* [[Vector Sum and Direct Sum]]
* [[Linear Combination]]
# Links
* [[Linear Algebra by Friedberg Insel and Spence]]