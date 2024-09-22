* (*Fraleigh 20.1*) **Fermat's Little Theorem**.  If $a\in \mathbb{Z}$ and $p$ is a prime not dividing $a$, then
  $$
  a^{p-1}\equiv 1 \ (\text{mod } p)
  $$
  For all $a\equiv 0 \ \text{mod p}$ 
	* (*Fraleigh 20.2*) If $a\in \mathbb{Z}$ then $a^p\equiv a \ (\text{mod } p)$  for any prime $p$
	* *Intuition*: The set $\{a,2a,3a,\dots, (p-1)a\} \  \text{mod } p$   is equivalent to $\{1,2,3,\dots,p-1\} \text{ mod } p$ when $a\nmid  p$.   Two facts are key here: First, none of the multiples of $a$ in the set are $0$ (because $a\not\equiv 0 \text{ mod } p$) and second, each multiple is distinct $\text{mod } p$.  
	* *Intuition* The set $\{1,\dots,p-1\}$ forms a [[Fundamental Constructs of Group Theory|group]] under multiplication modulo $p$. Thus from [[Subgroup|Lagrange's Theorem]], $|\text{ord}(z)|$ divides $p-1$. In other words, $z^{p} \equiv z \text{ mod } p$  

* **Euler's Phi Function** is a function $\phi:\mathbb{Z}^+\to \mathbb{Z}^+$ defined as 
  $$
  \phi(n) = \text{\# of numbers less than $n$ coprime to $n$}
  $$
* (*Fraleigh 20.8*) **Euler's Theorem**. If $a$ is an integer relatively prime to $n$. Then
  $$
  a^{\phi(n)} \equiv 1 \ (\text{mod } p)
  $$
	* *Intuition*: The set formed by $1,a,a^2,\dots$ is finite. In fact, it  forms a multiplicative group of order $\phi(n)$. 

* (*Fraleigh 20.10, Fraleigh 20.11*) Let $m\in\mathbb{Z}^+$ and $a\in\mathbb{Z}_m$ be relatively prime to $m$. For each $b\in \mathbb{Z}_m$ the equation $ax=b$ has a unique solution in $\mathbb{Z}_n$.
  
  Another way to interpret this
  
  If $a\perp m$, then for any $b\in \mathbb{Z}$, the congruence
  $$
  ax\equiv b \ (\text{mod } m)
  $$
  has as solutions all integers in precisely one residue class modulo $m$,

* (*Fraleigh 20.12, Fraleigh 20.13*) Let $m\in\mathbb{Z}^+$ and let $a,b\in\mathbb{Z}_m$. Let $\gcd(a,m)=d$. The equation $ax=b$ has a solution in $\mathbb{Z}_m$ if and only if $d\ \mid \ b$.
  
  The equation has exactly $d$ solutions in $\mathbb{Z}_m$.
  
  Another way to interpret this
  
  Let $\gcd(a,m)=d$. The congruence $ax\equiv b \ (\text{mod } m)$ has a solution if and only if $d \ \mid \ b$. When this is the case, the solutions are the integers in exactly $d$ distinct residue classes modulo $m$.   

* An element of $\mathbb{C}$ that is [[Extension Field and Polynomials|algebraic]] over $\mathbb{Q}$ is an **algebraic number**.  A **transcendental number** is an element of $\mathbb{C}$ that is transcendental over $\mathbb{Q}$ 
	* (*Fraleigh 31.13*) The set of all algebraic numbers forms a [[Fundamental Constructs of Field Theory|field]]
		* *Proof*: The set of all algebraic numbers is simply the [[Algebraic Closure]] of $\mathbb{Q}$ in $\mathbb{C}$. 


# Topics
* [[Number Theory -- Notation Guide]]
# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh]] - some theorems in Number Theory can be studied using Abstract Algebra