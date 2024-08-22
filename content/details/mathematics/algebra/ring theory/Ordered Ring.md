* An **ordered ring** is a [[Fundamental Constructs of Ring Theory|ring]] with a nonempty subset $P\subseteq R$ (called the set of **positive** elements) satisfying two properties
	* **Closure**: $\forall a,b\in P$, $a+b\in P \wedge ab\in P$
	* **Trichotomy**: $\forall a\in R$ one and only one of the following holds:
	  $$
	  \begin{split}
	  a\in P \ \ \ \ \ a = 0 \ \ \ \ \ -a\in P 
	  \end{split}
	  $$

* Rules for multiplying positives and negatives hold: 
	* If $p\in P$ and $n\notin P$ where $p,n\ne 0$, then $p\cdot n \notin P$.
	* If $n_1,n_2\notin P$ where $n_1,n_2\ne 0$, then $n_1\cdot n_2 \in P$

* (*Fraleigh e25.26*) If $R$ is an ordered ring with $P$ as positive elements and $S\le R$, then $P\cap S$ satisfies the requirements for a set of positive elements in the ring $S$. $P\cap S$ gives an ordering of $S$. 

* (*Fraleigh 25.3*) Let $R$ be an ordered ring, all squares of nonzero elements in $R$ are positive. $\text{char}(R)=0$ and there are no zero divisors
	* *Proof*: Trichotomy gives $a\in P$ or $(-a)\in P$. Closure gives $a^2\in P$ and $(-a)^2\in P$ 
	* Thus, no finite ring can be ordered since the characteristic of an ordered ring is $0$.

* (*Fraleigh 25.4*) $\mathbb{Z}$ can be considered as embedded in any ordered ring $R$. The induced ordering from $\mathbb{Z}$ from $R$ is the natural ordering of $\mathbb{Z}$ (i.e. $P$ is the set of positive integers). 

* (*Fraleigh 25.5*) Let $R$ be an ordered ring with set $P$ of positive elements. Let $<$ (is less than) be a [[Relation|relation]] defined by
  $$
  a<b \iff (b-a) \in P
  $$
  For $a,b\in R$. Then $<$ has the following properties $\forall a,b,c\in R$ 
	* **Trichotomy**: One and only one of the following holds: 
	  $$
	  a < b \ \ \ \ \ a =  b \ \ \ \ \ a > b
	  $$
	* **Transitivity**: 
	  $$
	  a<b \wedge b < c \implies a < c
	  $$ 
	* **Isotonicity**: 
	  $$
	  \begin{split}
	  b< c&\implies a + b < a + c \\ 
	  b < c \wedge 0 < a &\implies ab < ac \wedge ba < ca
	  \end{split}
	  $$
	Conversely, given a relation $<$ on a nonzero ring $R$ satisfying the above, the set $P=\{x\in R \mid 0 < x\}$ satisfies the criteria for a set of positive elements. 
	* $1\in P$ and in fact $0 < 1$. 
	* (*Fraleigh e25.18*) $a\in P\implies 0 < a$
	* (*Fraleigh e25.19*) $a,b\in P \wedge ac = bd \implies c=d=0 \vee cd\in P$ 
	* (*Fraleigh e25.20*) $a<b\implies -b<-a$
	* (*Fraleigh e25.21*) $a<0\wedge 0<b \implies ab <0$

* An ordering of a ring $R$ with the property that $\forall a, b\in R$, there exists a positive integer $n$ such that
  $$
  n\cdot a > b
  $$
  is called an **Archimedean ordering**

* (*Fraleigh 25.10*) Let $R$ be an ordered ring with set $P$ of positive elements and let $\phi:R\to R'$ be a [[Ring Homomorphism|ring isomorphism]]. The subset $P'=\phi[P]$ gives a set of positive elements of $R'$. 
  
  Also, the ordering relation given by $P'$  (denoted $<'$) gives us 
  $$
  \phi(a) <'\phi(b) \iff a < b
  $$
  That is, *isomorphism between ordered rings preserves the ordering*.
  
  The ordering $<'$ is called the **ordering induced by** $\phi$


# Link
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh|Fraleigh]]