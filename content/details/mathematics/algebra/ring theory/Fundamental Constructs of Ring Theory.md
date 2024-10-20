---
aliases:
  - ring
---

* A **ring** $(R,+,\cdot)$ is a set $R$ with two binary operations $+$ and $\cdot$ called **addition** and **multiplication** defined on $R$ such that the following hold
	* $(R,+)$ is an [[Abelian Group]].  [^abelianness]
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

[^abelianness]: The requirement that $(R,+)$ be Abelian is forced by distributivity. In particular, if we compute $(1+1)(a+b)$, commutativity is forced for both left distributivity and right distributivity to hold.

* (*Fraleigh 18.8*) If $R$ is a ring, then for any $a,b\in R$ 
	* $0a=a0=0$
	* $a(-b)=(-a)b=-(ab)$
	* $(-a)(-b)=ab$

* If for a ring $R$ a positive integer $n$ exists such that $n\cdot a=0$ $\forall a\in R$, then the least such positive integer is the **characteristic** of the ring. If no such positive integer exists, then $R$ has characteristic $0$. We denote this $\text{char}(R)$


# Misc
* A **subring** of a ring is a subset of the ring that is a ring under induced operations from the whole ring. It is a generalization of [[Subgroup]]. 
	* (*Fraleigh e18.49a*) The intersection of subrings of a ring $R$ is again a subring of $R$

* An element $a$ of a ring $R$ is **idempotent** if $a^2=a$.
* A ring $R$ is a **[[Boolean Algebra|Boolean]] Ring** if every element is idempotent.



# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh|Fraleigh]]