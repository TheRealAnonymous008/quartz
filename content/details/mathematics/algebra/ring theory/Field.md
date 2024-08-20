* A **field** is a [[Commutative Ring|commutative]] [[Division Ring and Rings with Unity|division ring]]. 

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
* (*Fraleigh 19.11*) Every finite integral domain is a field
	* *Proof*: Let $D$ be an integral domain whose elements are $0,1,a_1,\dots, a_n$. 
	  
	  All elements in $D$ of the form $a1,aa_1,\dots,aa_n$ are distinct because of the cancellation laws. Also, none of these elements is $0$. Therefore, we can map these to $1,\dots,n$ (i.e., $aa_i=1$ for some $a_i$).
* (*Fraleigh 19.12*) If $p$ is [[Number Theory|prime]], then $\mathbb{Z}_p$ is a field

* A **subfield** of a field is a subset of the field that is afield under induced operations from the whole fiield. It is a generalization of [[Subgroup]]. 
	* (*Fraleigh e18.49b*) The intersection of subfields of a field $F$ is again a subfield of $F$

* (*Fraleigh 23.6*) If $G$ is a finite subgroup of the multiplicative group $(F,\cdot)$ -- that is, the group from non-zero elements of the field, is [[Cyclic Group|cyclic]].
	* *Proof*: The multiplicative group $F^\ast$ is [[Abelian Group|Abelian]] therefore it can be factored by the Fundamental Theorem of Finitely Generated Abelian Groups  $\mathbb{Z}_{d_1}\times \dots\times\mathbb{Z}_{d_r}$. Let $m=\text{lcm}(d_1,\dots,d_r) \le d_1d_2\dots d_r$. Now for $a_i\in \mathbb{Z}_{d_i}$$a_i^m=1$ since $d_i$ divides $m$. Thus, every element of $G$ is a [[Polynomial Ring|zero]] of $x^m-1$. But also, $m\ge d_1d_2\dots d_r$ since there are at most $m$ zeros. Therefore $m=d_1d_2\dots d_r$  so it is cyclic.
# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh|Fraleigh]]