* If $a,b\ne 0$ are elements of ring $R$ such that $ab=0$, then $a$ and $b$ are called **divisors of $0$** 
	* (*Fraleigh 19.3*) In the ring $\mathbb{Z}_n$ the divisors of $0$ are precisely those non-zero elements that are not relatively [[Number Theory|prime]] to $n$.
	* (*Fraleigh 19.4*) If $p$ is prime, then $\mathbb{Z}$ has no divisors of $0$. 
	* For any ring, the set of elements that are not divisors of $0$ is closed under multiplication.

* An **integral domain** $D$ is a [[Commutative Ring]] with [[Ring with Unity|unity]] $1\ne 0$ and containing no divisors of $0$.

* (*Fraleigh 19.5*) The following **cancellation laws** hold in ring $R$ if and only if $R$ is an integral domain
  
  $$
  \begin{split}
  ab=ac \wedge a \ne 0 & \implies b=c \\
  ba=ca \wedge a\ne 0 & \implies b = c
  \end{split}
  $$
* The [[Direct Product of Rings|direct product]] of two non-zero rings is not an integral domain.


* A **subdomain** of integral domain $D$ is a subset of the domain that is an integral domain under induced operations from the whole integral domain. 
	* (*Fraleigh e19.24*) The intersection of subdomains of $D$ is also a subdomain $D$.
	* (*Fraleigh e19.27*) The characteristic of a subdomain of an integral domain $D$ is equal to the characteristic of $D$.
	* (*Fraleigh e19.28*) $\{n\cdot 1\mid n\in \mathbb{Z}\}\le D$. Furthermore, this subdomain is contained in every subdomain of $D$.
	* (*Fraleigh e19.29*) $\text{char}(D) = 0$ or $\text{char}(D)=p$, where $p$ is prime. 


* (*Fraleigh 19.11*) Every finite integral domain is a [[field]]
	* *Proof*: Let $D$ be an integral domain whose elements are $0,1,a_1,\dots, a_n$. 
	  
	  All elements in $D$ of the form $a1,aa_1,\dots,aa_n$ are distinct because of the cancellation laws. Also, none of these elements is $0$. Therefore, we can map these to $1,\dots,n$ (i.e., $aa_i=1$ for some $a_i$).
* Every integral domain is contained in a field called the [[Quotient Field]] of the integral domain

# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh|Fraleigh]]