---
aliases:
  - field
---

* A **field** is a [[Commutative Ring|commutative]] [[Division Ring|division ring]]. 

* The following axioms hold for a field (which follows from the properties of rings). 
  
  We have operations $+$ (addition) and $\cdot$ (multiplication)
	* *Associativity of Addition*: $a+(b+c)=(a+b)+c$
	* *Associativity of Multiplication*: $a\cdot (b\cdot c) = (a\cdot b) \cdot c$ 
	* *Commutativity of Addition*: $a+b=b+a$
	* *Commutativity of Multiplication*: $a\cdot b=b\cdot a$
	* *Additive Identity*: $\exists 0\in F$ such that $a+0=a$
	* *Multiplicative Identity*: $\exists 1\in F$ such that $a\cdot 1 = a$
	* $1\ne 0$. 
	* *Additive Inverses* $\forall a\in F, \exists -a \in F$ such that $a+(-a)=0$
	* *Multiplicative Inverses*: $\forall a \in F, \exists a^{-1}\in F$ such that $a\cdot a^{-1} = 1$.
	* *Distributivity* $a\cdot (b+c)=(a\cdot b) + (a\cdot c)$. 

* (*Fraleigh 19.9*) Every field is an [[Integral Domain]]
* (*Fraleigh 19.12*) If $p$ is [[Number Theory|prime]], then $\mathbb{Z}_p$ is a field

* A **subfield** of a field is a subset of the field that is afield under induced operations from the whole fiield. It is a generalization of [[Subgroup]]. 
	* (*Fraleigh e18.49b*) The intersection of subfields of a field $F$ is again a subfield of $F$
	*  A field $E$ is an **extension field** of $F$ if $F\le E$. 

* The following hold for [[Ordered Ring|ordered]] fields with positive set $P$ and the relation $a<b$ defined as $a-b\in P$
	* (*Fraleigh e25.22*) $a,b\in P \implies a/b\in P$
	* (*Fraleigh e25.23*) $0<a<1\implies 1 < 1/a$ 
	* (*Fraleigh e25.24*) $-1<a<0\implies 1/a < -1$.


* (*Fraleigh 27.6*) A field $F$ has exactly $2$ [[Ideal|ideals]] - $\{0\}$ and $F$. 
	* *Proof*: Clearly if we have the non-zero ideal, then let $I$ be the ideal and $a\in I$. Then
	  $$
	  a\in I \implies aa^{-1} \in I \implies 1 \in I \implies \forall x \in F,  1\cdot x =x \in I
	  $$
* (*Fraleigh 27.11*) A commutative ring with unity is a field if and only if it has no proper nontrivial ideals.

* An element $\alpha$ of a field is an **$n$-th root of unity** if $a^n=1$. It is a **primitive $n$-th root of unity** if $a^n=1$ and $a^m\ne 1$ for $0<m < n$. 
# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh|Fraleigh]]