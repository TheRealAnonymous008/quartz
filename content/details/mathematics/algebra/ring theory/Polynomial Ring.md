# Extension from Elementary Algebra
* We say $R[x]$ to mean the set of all polynomials with coefficients in the [[Fundamental Constructs of Ring Theory|ring]] $R$.  $R[x]$ is a ring called the **Polynomial Ring** where addition and multiplication are defined similarly for polynomials.
  
  More formally, a **Polynomial** $f(x)$ with coefficients in $R$ is an infinite formal sum 
  $$
  \sum_{i=0}^\infty a_ix^i  = a_0 + a_1x+\dots +a_nx^n+\dots
  $$
  Where $a_i\in R$ and $a_i=0$ for all but a finite number of values of $i$. We refer to $a_i$ as the **coefficients**. We refer to $x$ as the **indeterminate**.
  
  If for some $i\ge 0$, $a_i\ne 0$, the largest such $i$ is the **degree** of $f(x)$ denoted $\deg f(x)$.
  
  If all $a_i=0$, then $\deg f(x)=-\infty$. 
  
  All polynomials are written as they would be written following the conventions of elementary algebra.

* Let $f(x)=a_0+a_1x+\dots +a_nx^n + \dots$ and $g(x) = b_0 ++b_1 + \dots + b_nx^n + \dots$. Then 
  
  Polynomial addition is defined as 
  $$
  f(x) + g(x) = c_0 + c_1x + \dots + c_nx^n + \dots
  $$
  Where $c_n=a_n + b_n$
  
  Polynomial multiplication is defined as
  $$
  f(x)\cdot g(x) = d_0+ d_ix + \dots + d_nx^n +\dots 
  $$
  Where $d_n = \sum_{i=0}^n a_i b_{n-i}$ 
* More generally, if we have indeterminates $x_1,\dots,x_n$, we denote the polynomial ring in these indeterminates as $R[x_1,\dots,x_n]$.

* (*Fraleigh 22.2*) $R[x]$ is a ring under polynomial addition and multiplication. If $R$ is [[Commutative Ring|commutative]] then so it $R[x]$. If $R$ has a [[Ring with Unity|unity]] $1\ne 0$, then $1$ is also the unity in ring $R[x]$. 
* (*Fraleigh e22.24* ) If $D$ is an [[Integral Domain]] then so is $D[x]$


* (*Fraleigh 22.4*) **The Evaluation Homomorphisms for Field Theory**  [^eval_hom] Let $F$ be a subfield of [[Field]] $E$ and $\alpha\in E$. Let $x$ be the indeterminate. The map $\phi_\alpha: F[x]\to E$ defined by
  $$
  \phi_a(a_0 + a_1x + \dots + a_nx^n) = a_0+a_1\alpha + \dots + a_n\alpha^n
  $$
  For $(a_0+\dots +a_nx^n)\in F[x]$ is a [[Ring Homomorphism|homomorphism]] of $F[x]$ into $E$.
  
  Also $\phi_\alpha(x)=\alpha$ and $\phi_\alpha$ maps $F$ isomorphically by the identity map : $\phi_\alpha(a) = a$ $\forall a\in F$ .
  
  We refer to $\phi_\alpha$ as an **evaluation** at $\alpha$
	* *Intuition*: This generalizes the elementary algebra notion of substituting $\alpha$ in the polynomial and evaluating

* Let $F$ be a subfield of $E$ and $\alpha\in E$   Let $f(x)=a_0+a_1x + \dots + a_nx^n\in F[x]$ and $\phi_\alpha:F[x]\to E$ be the evaluation homomorphism. 
  
  Let $f(\alpha)$ denote
  $$
  f(\alpha) = \phi_\alpha(f(x)) = a_0 + a_1\alpha + \dots + a_n \alpha^n
  $$
  If $f(\alpha)=0$, then $\alpha$ is a **zero** of $f(x)$. 

[^eval_hom]: This theorem holds for commutative rings as well. 


* (*Fraleigh e26.23*) Let $F$ be a field and let $S\subseteq F^n$. The set 
  $$
  N_S = \{f(x_1,\dots,x_n) \in F[x_1,\dots,x_n] \mid (a_1,\dots,a_nn)\in S \text{ is a zero }\}
  $$
  is an [[Ideal]] in  $F[x_1,\dots,x_n]$


* (*Fraleigh 27.24*) If $F$ is a field, every [[Ideal]] in $F[x]$ is principal
* (*Fraleigh 27.25*) An ideal $\braket{p(x)}\ne 0$ of $F[x]$ is maximal if and only if $p(x)$ is irreducible over $F$.
	* *Intuition*: In the forward direction, if the ideal is maximal, it is also prime (since $F[x]$ is a commutative ring with unity).  Any factorization of $p(x)$ must have factors that are multiples of $p(x)$ which cannot be. 
	  
	  In the reverse direction, if we consider the principal ideal of $p(x)$, any hypothetical ideal containing it must also be a principal ideal. This implies $p(x)$ is some multiple of $q(x)$ but this is impossible because it is irreducible.
	  

# Factorization
* (*Fraleigh 23.1*) **Division Algorithm** Let $f(x), g(x)\in F[x]$ with $a_n,b_m\ne 0$ for $f(x)=a_0+\dots + a_nx^n$ and $g(x)=b_0 + \dots + b_mx^m$ and $m>0$. Then there are unique polynomials $q(x)$ and $r(x)$ such that
  $$
  f(x)=g(x)q(x) + r(x)
  $$
  Where either $r(x)=0$ or $\deg (r(x)) < m$
	* *Intuition*: Either the remainder $r(x)=0$ or it is not. If it is not, and assuming $\deg (r(x)) > \deg(g(x))$, it is possible to find a smaller remainder ad infinitum, leading to the contradiction.  
	* (*Fraleigh e23.36*) **Remainder Theorem** Let $f(x)\in F(x)$ where $F$ is a field. Let $a\in F$. Then $f(x)$ divided by $x-a$ has remainder $f(a)$.
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
* (*Fraleigh 23.15*) **Eisenstein Criterion** Let $p\in \mathbb{Z}$ be prime. Suppose that $f(x)=a_nx^n + \dots + a_0\in\mathbb{Z}[x]$. Then $f(x)$ is irreducible over $\mathbb{Q}$ if the following hold:
	* $a_n\not\equiv 0 \text{ mod } p$  
	* $a_i\equiv0 \text{ mod } p$ $\forall i <n$ 
	* $a_0\not\equiv  0 \text{ mod } p^2$. Then $f(x)$ is irreducible over $\mathbb{Q}$. 
* The set of **cyclotonic polynomials** are irreducible over $\mathbb{Q}$ for any prime. They are defined as
  $$
  \Phi_p(x) = \frac{x^p-1}{x-1}=x^{p-1} + x^{p-2}+\dots +x +1
  $$


# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh|Fraleigh]]
* [Abstract Algebra Eisenstein's Criterion by Michael Penn](https://www.youtube.com/watch?v=WEFM0favZv0&t=965s)