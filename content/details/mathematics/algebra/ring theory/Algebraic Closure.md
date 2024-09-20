*  The **algebraic closure** of $F$ in $E$, $F\le E$ is the set
  $$
  \overline{F}_E = \set{\alpha\in E \mid \alpha \text{ is algebraic over } F}
  $$

* (*Fraleigh 31.12*) Let $F\le E$. Then
  $$
  \overline{F}_E \le E
  $$

* A [[Field|field]] is **algebraically closed** if  every nonconstant [[Polynomial Ring|polynomial]] in $F[x]$ has a zero in $F$.

* (*Fraleigh 31.15*) A field $F$ is algebraically closed if and only if every nonconstant polynomial in $F[x]$ [[Factorization of Polynomials|factors]] in $F[x]$ into linear factors. 
	* *Proof*: In the forward case, let $f(x)$ be a polynomial. If $\alpha$ is a zero of $f(x)$, then  $\alpha \in F$ by algebraic closure and so $(x-\alpha)$ is a factor of $f(x)$
	  
	  Conversely, if $ax-b$ is a factor of $f(x)$, then $b/a$ is a zero in $f(x)$ which implies algebraic closure  

* (*Fraleigh 31.16*) An algebraically closed field has no proper [[Algebraic Extension|algebraic extensions]] $F < E$.

* (*Fraleigh 31.17*) Every field $F$ has an algebraic closure, that is an algebraic extension $\overline{F}$ that is algebraically closed.
	* *Intuition*:  An order relation exists for the set of all algebraic extension fields since they can contain one another. 
	  
	  Every chain in this set has an upper bound formed by taking the union of each element in the chain. 
	  
	  Zorn's Lemma applies: $\overline{F}$ is the [[Set Theory|Maximal Element]] in the set of all algebraic extensions of $F$. It can then be shown that $\overline{F}$ is algebraically closed by maximality. 

* (*Fraleigh 31.18*) **Fundamental Theorem of Algebra** - $\mathbb{C}$ is an algebraically closed field.

* (*Fraleigh 31.32*) Every $\alpha\in E$ that is not in the algebraic closure $\overline{F}_E$ of $F$ over $E$ is transcendental over $\overline{F}_E$. 

* (*Fraleigh 31.35*) No finite field of odd characteristic is algebraically closed. 
# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh|Fraleigh]]

* [[Extension Field and Polynomials]]