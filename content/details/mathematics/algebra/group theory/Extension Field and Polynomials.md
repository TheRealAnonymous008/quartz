* (*Fraleigh 29.3*) **Kronecker's Theorem** Let $F$ be a [[Fundamental Constructs of Field Theory|field]] and $f(x)$ be a nonconstant polynomial in $F[x]$. Then there exists an extension field $E$ of $F$ and an $\alpha\in E$ such that 
  $$
  f(\alpha) = 0
  $$
	* *Proof*: Consider an [[Factorization of Polynomials|irreducible]] polynomial $p(x)$ that divides $f(x)$. The extension field is the [[Factor Ring|factor ring]] $F[x]/\braket{p(x)}$, which is a field because $\braket{p(x)}$ is a maximal ideal by *Fraleigh 27.25*.  Clearly $F[x]\le E$ since we can take the additive coset $\set{a+\braket{p(x)} \mid a \in F}$  as our representation for $F$ so $E$ is indeed an extension field.
	  
	  Finally, we can find $\alpha=x+\braket{p(x)}\in E$. The evaluation homomorphism $\phi_\alpha : F[x]\to E$ evaluated at $p(x)$ can be computed using $x$ as a representative of the additive coset which gives us
	  $$
	  p(\alpha) = p(x) + \braket{p(x)} = \braket{p(x)} = 0 + \braket{p(x)}
	  $$
	  Which is precisely $0\in E$.  

* An element $\alpha$ of an extension field $E$ of a field $F$ is **algebraic** over $F$ if $f(\alpha)=0$ for some nonzero $f(x)\in F[x]$. 
  
  Otherwise, $\alpha$ is **transcendental** over $F$.
  
  In other words, *$\alpha$ is algebraic over $F$ if it is the zero of some [[Polynomial Ring|polynomial]] over $F$*, where $F\le E$.  
	* From a structural viewpoint, a transcendental element over $F$ behaves as though it were an indeterminate over $F$.

* (*Fraleigh 29.12*) Let $F\le E$ and let $\alpha\in E$. Let $\phi_\alpha:F[x]\to E$ be the evaluation [[Ring Homomorphism|homomorphism]] of $F[x]$ into $E$ such that $\phi_\alpha(a)=a$ for $a\in F$.  and $\phi_\alpha(x)=\alpha$. 
  
  Then $\alpha$ is transcendental over $F$ if and only if $\phi_\alpha$ gives an isomorphism of $F[x]$ with a subdomain of $E$ (i.e., if $\phi_\alpha$ is a one-to-one map)
	* *Proof*: $\alpha$ is transcendental over $F$ if and only if $f(\alpha)\ne 0$ for all nonzero $f(x)\in F[x]$ 
	  if and only if $\phi_\alpha(f(x))\ne 0$ for all nonzero $f(x)\in F[x]$ 
	  if and only if $\text{Ker}({\phi_\alpha})=\{0\}$ 
	  if and only if $\phi_\alpha$ is a one-to-one map.

* (*Fraleigh 29.13*) Let $F\le E$ and $\alpha\in E$, where $\alpha$ is algebraic over $F$. Then there is an irreducible polynomial $p(x)\in F[x]$ such that $p(\alpha)=0$.  This polynomial is uniquely determined up to a constant factor in $F$ and is a polynomial of minimal degree $\ge 1$ in $F[x]$ having $\alpha$ as a zero.
  
  If $f(\alpha)=0$ for $f(x)\in F[x]$ with $f(x)=0$, then $p(x)$ divides $f(x)$.
	* Another way to say the theorem is that: *Every algebraic element $\alpha\in E$ has a corresponding unique monic polynomial in $F$[x]*. 
	* *Intuition*: $\text{Ker}(\phi_\alpha)$ is a principal ideal generated by some $p(x)$ such that $\alpha$ is a zero of this polynomial.  Any $f(x)$ with $\alpha$ as a zero must be in $\braket{p(x)}$. If $p(x)$ is of minimal degree, then any other polynomial of the same degree must be a constant multiple of $p(x)$. 
	* The unique monic polynomial $p(x)$ is called the **irreducible polynomial for $\alpha$ over $F$** denoted $\text{irr}(\alpha, F)$. The degree of $\text{irr}(\alpha, F)$ is the **degree of $\alpha$ over $F$** denoted $\deg(\alpha, F)$.   That is
	  $$
	  \deg (a,F) = \deg(\text{irr}(\alpha, F))
	  $$


* An extension field $E$ of $F$ is a **simple extension** of $F$ if $E=F(\alpha)$ for some $\alpha\in E$
	* $F(a) = \phi_a(F[x])$ 
	* If $\alpha$ is algebraic over $F$, then the subfield $F(\alpha)$ is the smallest subfield containing $F$ and $\alpha$. We find it as follows
	  $$
	  F(\alpha) = \phi_\alpha(F[x])\le E \cong  F[x]/\braket{irr(\alpha, F)} 
	  $$
	  The RHS follows because $\ker(\phi_\alpha)=\braket{\text{irr}(\alpha, F)}$ which is a maximal ideal of $F[x]$.
	* If $\alpha$ is transcendental over $F$, then $\phi_\alpha[F[x]]$ is an [[Integral Domain]] denoted $F[\alpha]$. We then define $F(\alpha)$ using the [[Quotient Field]]
	  $$
	  F(\alpha) = \text{Quot}(F[\alpha])
	  $$
	*  In either case, an element in $F(\alpha)$ can be expressed as a quotient of polynomials in $F[\alpha]$.
	* Also *$F(\alpha)$ is the smallest field in $E$ containing both $F$ and $\alpha$*

	* (*Fraleigh e29.29*) Let $F\le E$ and $\alpha, \beta \in E$. If $\alpha$ is transcendental over $F$ but algebraic over $F(\beta)$, then $\beta$ is algebraic over $F(\alpha)$.
	* (*Fraleigh e29.33*) Let $F\le E$ and $\alpha\in E$ be transcendental over $F$. Every element in $F(\alpha)$ not in $F$ is also transcendental over $F$

	* We can generalize $F(\alpha)$ to more than one element. Let $\alpha_1,\dots,\alpha_n\in E$. Then the smallest extension field of $F$ containing all $\alpha_i$ is denoted $F(\alpha_1,\dots,\alpha_n)$

* (*Fraleigh 29.18*) Let $\alpha$ be algebraic over $F$. Let the degree of $\text{irr}(\alpha, F)=n\ge 1$. Then $\forall \beta\in F(\alpha)$, we can uniquely express $\beta$ in the form
  $$
  \beta = b_0 + b_1\alpha + \dots + b_{n-1}\alpha^{n-1}
  $$
  Where $b_i\in F$

* (*Fraleigh 30.23*) Let $E$ be an extension field of $F$ and $\alpha\in E$ be algebraic over $F$. If $\deg(\alpha,F)=n$ then $F(\alpha)$ is an $n$-dimensional [[Vector Space]] over $F$ with [[Linear Combination|basis]] 
  $$
  \set{1,\alpha,\dots,\alpha^{n-1}}
  $$
  Also, every element $\beta\in F(\alpha)$ is algebraic over $F$ and
  $$
  \deg(\beta,F) \le \deg(\alpha, F)
  $$

# Topics
 * [[Algebraic Extension]]
 * [[Algebraic Closure]]
# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh|Fraleigh]]