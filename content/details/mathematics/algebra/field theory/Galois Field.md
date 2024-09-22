# Finite Fields
* (*Fraleigh 33.1*) Let $E$ be a [[Extension Field and Polynomials|finite extension]] of degree $n$ over a finite [[Fundamental Constructs of Field Theory|field]] $F$. If $F$ has $q$ elements, then $E$ has $q^n$ elements  
	* (*Fraleigh e29.30*) Let $F\le E$ where $F$ is a finite field with $|F|=q$. Let $\alpha\in E$ be algebraic over $F$ such that $\deg(\alpha, F)=n$. Then 
	  $$
	  |F(\alpha)| = q^n
	  $$
		* *Intuition*: If $\alpha$ is algebraic with degree $n$, then there exists a basis of $n$ elements. Each basis must consist of any of the $q$ elements of $F$. 
* (*Fraleigh 33.2*) If $E$ is a finite field of characteristic $p$ then $E$ contains exactly $p^n$ elements for some $n\in \mathbb{Z}^+$. 
* (*Fraleigh 33.3*) Let $E$ be a field of $p^n$ elements contained in an [[Algebraic Closure|algebraic closure]] $\overline{\mathbb{Z}}_p$  of $\mathbb{Z}_p$. The elements of $E$ are precisely the zeros in $\overline{\mathbb{Z}}_p$ of the polynomial $x^{p^n}-x$ in $\mathbb{Z}_p[x]$.
	* The nonzero elements of a finite field of $p^n$ elements are all $(p^n-1)$-th roots of unity

* (*Fraleigh 23.6*) If $G$ is a finite [[Subgroup|subgroup]] of the multiplicative group $(F,\cdot)$  then $G$ is cyclic.
  (*Fraleigh 33.5*) In particular, the group from non-zero elements of a finite field, is [[Cyclic Group|cyclic]].
	* *Proof*: The multiplicative group $F^\ast$ is [[Abelian Group|Abelian]] therefore it can be factored by the Fundamental Theorem of Finitely Generated Abelian Groups  $\mathbb{Z}_{d_1}\times \dots\times\mathbb{Z}_{d_r}$. Let $m=\text{lcm}(d_1,\dots,d_r) \le d_1d_2\dots d_r$. Now for $a_i\in \mathbb{Z}_{d_i}$$a_i^m=1$ since $d_i$ divides $m$. Thus, every element of $G$ is a [[Polynomial Ring|zero]] of $x^m-1$. But also, $m\ge d_1d_2\dots d_r$ since there are at most $m$ zeros. Therefore $m=d_1d_2\dots d_r$  so it is cyclic.

* (*Fraleigh 33.6*) A [[Algebraic Extension|finite extension]] $E$ of a finite field $F$ is a simple extension of $F$.
	* *Intuition* Any $\alpha$ that generates the cyclic group of nonzero elements of $E$ implies $E=F(\alpha)$.

# Galois Fields
* (*Fraleigh 33.8*) If $F$ is a field of [[Number Theory|prime]] characteristic $p$ with algebraic closure $\overline{F}$, then $x^{p^n}-x$ has $p^n$ distinct zeros in $F$. 
	* *Intuition* $x^{p^n}-x$ factors into linear factors. Let $\alpha$ be the root of one such linear factor. It can be shown that each summand in $\frac{f(x)}{x-a}$ is $\frac{1}{\alpha}$ in $g(\alpha)$. Since the field has prime characteristic, $p^n=1$, it can be shown that $g(\alpha)=-\frac{1}{\alpha} \ne 0$.  Thus $\alpha$ has multiplicity $1$ and there are $p^n$ such $\alpha$.

* (*Fraleigh 33.9*) If $F$ is a field of prime characteristic $p$, then $(\alpha + \beta)^{p^n}=\alpha^{p^n} +\beta^{p^n}$ $\forall \alpha,\beta \in F$ and $\forall n\in\mathbb{Z}^+$. 

* (*Fraleigh 33.10*) The **Galois Field of order $p^n$** denoted $\text{GF}(p^n)$ of $p^n$ elements exists for every prime power. 
	* *Intuition*: It is the set of all zeros of $x^{p^n}-x$ in the algebraic closure $\overline{\mathbb{Z}}_p$.

* (*Fraleigh 33.11*) If $F$ is any finite field, then for every $n\in \mathbb{Z}^+$, there is an irreducible polynomial in $F[x]$ of degree $n$.

* (*Fraleigh 33.12*) Let $p$ be prime and $n\in\mathbb{Z}^+$. If $E$ and $E'$ are fields of order $p^n$ then $E\cong E'$.  
# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh|Fraleigh]]