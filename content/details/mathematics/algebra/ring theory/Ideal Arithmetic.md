* If $A$ and $B$ are [[Ideal|ideals]] of ring $R$, then their **sum** is defined as 
  $$
  A+B=\set{a+b\mid a\in A, b\in B}
  $$
	* (*Fraleigh e27.34a*)  $A+B$ is an ideal
	* (*Fraleigh e27.34b*) $A\subseteq A+B$ and $B\subseteq A+B$ 

* If $A$ and $B$ are ideals of ring $R$, then their **product** is defined as 
  $$
  AB=\bigg\{\sum_{i=1}^n a_i b_i  \mid a\in A, b\in B, n\in \mathbb{Z}^+\bigg\}
  $$
	* (*Fraleigh e27.35a*)  $AB$ is an ideal
	* (*Fraleigh e27.35b*) $AB\subseteq A\cap B$  
* Let $A$ and $B$ be ideals of a [[Commutative Ring]] $R$. The **quotient** is defined by
  $$
  A: B = \set{r\in R \mid rb\in A \forall b\in B}
  $$
	* (*Fraleigh e27.36*) $A:B$ is an ideal

* An element $a$ of a ring $R$ is **nilpotent** if $a^n=0$ for some $n\in \mathbb{Z}^+$
	* (*Fraleigh e18.47*) A ring has no non-zero nilpotent element if and only if $0$ is the only solution to $x^2=0$ in $R$.
	  
	  Trivially, it is easy to see the case where the $x^2=0$ for some $x\ne 0$ gives a non-zero nilpotent element.
	  
	  For the converse, suppose $x^2\ne 0$, but $x^p=0$. Then we can consider $x^2,x^4,\dots, x^{2^{\lg p}}\ne 0$,    
	* We refer to the set of nilpotent elements of ring $R$ as its **nilradical**. 
	* (*Fraleigh e26.30*) The nilradical is an ideal.

* (*Fraleigh e26.30*) The nilradical of $R$  forms an ideal in $R$. 

* Let $R$ be a commutative ring and $N$ an ideal of $R$. The **radical*** of $N$ is defined as
  $$
  \sqrt{N} = \set{a\in R\mid a^n\in N \text{ for some } n\in \mathbb{Z}^+}
  $$
	* (*Fraleigh e26.34*) The radical is an ideal of $R$.
	* Let $N$ be an ideal in $R$, Then the nilradical of the [[Factor Ring]] $R/N$ is the factor ring of the radical $\sqrt{N}/N$

# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh|Fraleigh]]