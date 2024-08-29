* (*Fraleigh 23.1*) **Division Algorithm** Let $f(x), g(x)\in F[x]$ with $a_n,b_m\ne 0$ for $f(x)=a_0+\dots + a_nx^n$ and $g(x)=b_0 + \dots + b_mx^m$ and $m>0$. Then there are unique polynomials $q(x)$ and $r(x)$ such that
  $$
  f(x)=g(x)q(x) + r(x)
  $$
  Where either $r(x)=0$ or $\deg (r(x)) < m$
	* *Intuition*: Either the remainder $r(x)=0$ or it is not. If it is not, and assuming $\deg (r(x)) > \deg(g(x))$, it is possible to find a smaller remainder ad infinitum, leading to the contradiction.  
	* (*Fraleigh e23.36*) **Remainder Theorem** Let $f(x)\in F(x)$ where $F$ is a field. Let $a\in F$. Then $f(x)$ divided by $x-a$ has remainder $f(a)$.
	* (*Fraleigh 28.6*) Let $f(x),g(x),r(x),q(x)\in F[x]$ such that $f(x)=g(x)q(x)+r(x)$. The common zeros in $F^n$ of $f(x)$ and $g(x)$ are the same as the common zeros of $g(x)$ and $r(x)$.
	  
	  Also, the common divisors in $F[x]$ of $f(x)$ and $g(x)$ are the same as the same as the common divisors of $g(x)$ and $r(x)$.
	  
* (*Fraleigh 23.3*) **Factor Theorem**. An element $a\in F$ is a zero of $f(x)\in F[x]$ if and only if $(x-a)$ is a factor of $f(x)$ in $F[x]$.
* (*Fraleigh 23.5*) A nonzero polynomial $f(x)\in F[x]$ of degree $n$ can have at most $n$ zeros in field $F$. 

* A nonconstant polynomial $f(x)\in F[x]$ is **irreducible over** $F$ (a.k.a. an **irreducible polynomial over $F$**) if $f(x)$ cannot be expressed as a product $g(x)h(x)$ of two polynomials $g(x),h(x)\in F[x]$ both in lower degree than $f(x)$. 
  
  Otherwise, $f(x)$ is **reducible** 
	* A polynomial can be irreducible in field $F$ but reducible in a larger field $G\ge F$. 
* (*Fraleigh 23.10*) $f(x)$ is reducible over $F$ if and only if it has a zero in $F$.

* (*Frraleigh 23.18, Fraleigh 27.27*) Let $p(x)$ be an irreducible polynomial in $F[x]$. If $p(x)$ divides $r(x)s(x)$ for $r(x),s(x)\in F[x]$ then either $p(x)$ divides $r(x)$ or $p(x)$ divides $s(x)$

* (*Fraleigh 23.19*) If $p(x)$ is irreducible in $F[x]$ and $p(x)$ divides the product $r_1(x)\dots r_n(x)$ for $r_i(x)\in F[x]$ then $p(x)$ divides $r_i(x)$ for at least one $i$

* (*Fraleigh 23.20*) If $F$ is a field, then every nonconstant polynomial $f(x)\in F[x]$ can be factored in $F[x]$ into a product of irreducible polynomials. The irreducible polynomials are unique up to order and non-zero constant factors in $F$. 
 
## Special Cases
* (*Fraleigh 23.11*) **Gauss Lemma** If $f(x)\in\mathbb{Z}[x]$ then $f(x)$ factors into a product of two polynomials of lower degrees $r,s\in\mathbb{Q}[x]$ if and only if it has such a factorization with polynomials of the same degrees $r$ and $s$ in $\mathbb{Z}[x]$. 
* (*Fraleigh 23.12*) If $f(x)=x^n+a_{n-1}x^{n-1}+\dots+a_0\in \mathbb{Z}[x]$ with $a_0\ne0$ and if $f(x)$ has a zero in $\mathbb{Q}$, then it has a zero $m\in\mathbb{Z}$ and $m$ must divide $a_0$.
  
  Another way to say this: *The zeros of a polynomial (in the field of integers) are rational and must divide the constant term*. 
* (*Fraleigh 23.15*) **Eisenstein Criterion** Let $p\in \mathbb{Z}$ be [[Number Theory|prime]]. Suppose that $f(x)=a_nx^n + \dots + a_0\in\mathbb{Z}[x]$. Then $f(x)$ is irreducible over $\mathbb{Q}$ if the following hold:
	* $a_n\not\equiv 0 \text{ mod } p$  
	* $a_i\equiv0 \text{ mod } p$ $\forall i <n$ 
	* $a_0\not\equiv  0 \text{ mod } p^2$. Then $f(x)$ is irreducible over $\mathbb{Q}$. 
* The set of **cyclotonic polynomials** are irreducible over $\mathbb{Q}$ for any prime. They are defined as
  $$
  \Phi_p(x) = \frac{x^p-1}{x-1}=x^{p-1} + x^{p-2}+\dots +x +1
  $$


# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh|Fraleigh]]
* [[Polynomial Ring]]