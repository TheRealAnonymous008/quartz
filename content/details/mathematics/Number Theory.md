* (*Fraleigh 20.1*) **Fermat's Little Theorem**.  If $a\in \mathbb{Z}$ and $p$ is a prime not dividing $a$, then
  $$
  a^{p-1}\equiv 1 \ (\text{mod } p)
  $$
  For all $a\equiv 0 \ \text{mod p}$ 
	* (*Fraleigh 20.2*) If $a\in \mathbb{Z}$ then $a^p\equiv a \ (\text{mod } p)$  for any prime $p$

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
# Notation
* $p,q$ - generic primes
* $\mathbb{Z}$ - the set of integers
* $\mathbb{Z}_n$ - the set of integers modulo $n$
* $a \ \mid b$ - $a$ divides $b$
* $a\perp b$ - $a$ is coprime with $b$
* $\phi(n)$ - Euler's totient function

# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh]] - some theorems in Number Theory can be studied using Abstract Algebra