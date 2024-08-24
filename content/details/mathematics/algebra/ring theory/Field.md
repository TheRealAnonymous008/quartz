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

* (*Fraleigh 23.6*) If $G$ is a finite subgroup of the multiplicative group $(F,\cdot)$ -- that is, the group from non-zero elements of the field, is [[Cyclic Group|cyclic]].
	* *Proof*: The multiplicative group $F^\ast$ is [[Abelian Group|Abelian]] therefore it can be factored by the Fundamental Theorem of Finitely Generated Abelian Groups  $\mathbb{Z}_{d_1}\times \dots\times\mathbb{Z}_{d_r}$. Let $m=\text{lcm}(d_1,\dots,d_r) \le d_1d_2\dots d_r$. Now for $a_i\in \mathbb{Z}_{d_i}$$a_i^m=1$ since $d_i$ divides $m$. Thus, every element of $G$ is a [[Polynomial Ring|zero]] of $x^m-1$. But also, $m\ge d_1d_2\dots d_r$ since there are at most $m$ zeros. Therefore $m=d_1d_2\dots d_r$  so it is cyclic.

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

# Topics
* [[Prime Field]]

# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh|Fraleigh]]