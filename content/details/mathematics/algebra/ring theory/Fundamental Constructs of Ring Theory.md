* A **ring** $(R,+,\cdot)$ is a set $R$ with two binary operations $+$ and $\cdot$ called **addition** and **multiplication** defined on $R$ such that the following hold
	* $(R,+)$ is an [[Abelian Group]]. 
	* Multiplication is associative
	* For all $a,b,c\in R$ the **left distributive law**  holds
	  $$
	  a\cdot (b+c) = (a\cdot b) +(a\cdot c)
	  $$
	  The **right distributive law**
	  $$
	  (a+b)\cdot c = (a\cdot c) + (b\cdot c)
	  $$
	  also holds

	* $0$ is the additive identity (which always exists because $(R,+)$ is a group)
	  
	  We denote the additive inverse of $r\in R$ as $-r$

* (*Fraleigh 18.8*) If $R$ is a ring, then for any $a,b\in R$ 
	* $0a=a0=0$
	* $a(-b)=(-a)b=-(ab)$
	* $(-a)(-b)=ab$



* A **subring** of a ring is a subset of the ring that is a ring under induced operations from the whole ring. It is a generalization of [[Subgroup]]. 
	* (*Fraleigh e18.49a*) The intersection of subrings of a ring $R$ is again a subring of $R$

* An element $a$ of a ring $R$ is **idempotent** if $a^2=a$.
* An element $a$ of a ring $R$ is **nilpotent** if $a^n=0$ for some $n\in \mathbb{Z}^+$
	* (*Fraleigh e18.47*) A ring has no non-zero nilpotent element if and only if $0$ is the only solution to $x^2=0$ in $R$.
	  
	  Trivially, it is easy to see the case where the $x^2=0$ for some $x\ne 0$ gives a non-zero nilpotent element.
	  
	  For the converse, suppose $x^2\ne 0$, but $x^p=0$. Then we can consider $x^2,x^4,\dots, x^{2^{\lg p}}\ne 0$,    

* A ring $R$ is a **[[Boolean Algebra|Boolean]] Ring** if every element is idempotent.

# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh|Fraleigh]]