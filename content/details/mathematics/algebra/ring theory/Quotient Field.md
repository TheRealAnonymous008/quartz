* Every [[Integral Domain]] is contained in a [[Field]] -- the **field of quotients of the integral domain**
* (*Fraleigh 21.2*) The relation $(a,b)\sim (c,d)\iff ad=bc$ is an equivalence [[Relation]].  Where $b\ne 0$ and $d\ne 0$
	* *Intuition*: A more suggestive way to say this is that 
	  $$
	  \frac{a}{b} = \frac{c}{d} 
	  $$
	  $(a,b)$ is defined such that $a$ is the numerator and $b$ is the denominator. 
* (*Fraleigh 21.3*) The following give well-defined operations of addition and multiplication on $F$ where $F=D\times D$ 
  $$
  \begin{split}
  (a,b) + (c,d) &= (ad+bc,bd) \\
  (a,b)(c,d) &= (ac,bd)
  \end{split}
  $$
  We must show that using the relation in (*Fraleigh 21.2*) $(a',b')\sim (a,b)$ and $(c',d')\sim (c,d)$, then
  $$
  \begin{split}
  (ad+bc,bd) &\sim (a'd' + b'c',b'd') \\
  (a'c',b'd')  &\sim (ac,bd)
  \end{split}
  $$
	* *Intuition:* A more suggestive way to view this is as the product of two fractions.
	  $$
	  \begin{split}
	  \frac{a}{b} + \frac{c}{d} &= \frac{ad +bc}{bd} \\
	  \frac{a}{b} \cdot \frac{c}{d} &= \frac{ac}{bd}
	  \end{split}
	  $$
	
* (*Fraleigh 21.4*) The map $i:D\to F$ given by $i(a)=\{(a,1)\}$ is an isomorphism of $D$ with a subring of $F$.
* (*Fraleigh 21.5*) Any integral domain can be enlarged to a field $F$ such that every element of $F$ can be expressed as a quotient of two elements of $D$. We call this field the **field of quotients** of $D$. We denote this as $\text{Quot}(D)$ 
	* *Intuition*: A suggestive example: $\mathbb{Z} \subset \mathbb{Q}$ . In other words, the set of integers (integral domain) is contained in the set of possible quotients (field of quotients). In particular $a=a\cdot 1^{-1}$. 
	* *The field of quotients is the minimal field containing $D$*. This follows since a field containing $D$ must satisfy the property of multiplicative inverses
* (*Fraleigh 21.6*) Let $F$ be a field of quotients of $D$ and $L$ be any field containing $D$. Then there exists a map $\psi:F\to L$ that gives an isomorphism of $F$ with a subfield of $L$ such that $\psi(a)=a$ $\forall a \in D$
  
  In fact such a map $\psi$ can  be defined using the quotient of $a,b\in D$ over $F$ (denoted $a/_F \ b$) 
  $$
  \begin{split} 
  \psi(a)&= a \\
  \psi(a/_F  \ b) &= \psi(a) \ /_L \ \psi(b) 
  \end{split}
  $$
  This division operator is defined such that
  $$
  a \ /_F \ b = c \ /_F \ d \iff ad = bc 
  $$
  Where $b, d\ne 0$  
* (*Fraleigh 21.8*) Every field $L$ containing an integral domain $D$ contains a field of quotients of $D$. 
* (*Fraleigh 21.9*) Any two fields of quotients of an integral domain $D$ are isomorphic

# Localization of a Ring
* In general a [[Commutative Ring]] that is not an integral domain can be enlarged to a field.
  
  Let $R$ be a nonzero commutative ring and $T\subseteq R$ be a non-empty subset of $R$ closed under multiplication and containing neither $0$ nor divisors of $0$. 
  
  Using the same enlargement for the quotient field of an integral domain, we can enlarge $R$ to a partial ring of quotients $Q(R,T)$.  
	* (*Fraleigh e21.12a*) $Q(R,T)$ has [[Division Ring and Rings with Unity|unity]] even if $R$ does not.
	* (*Fraleigh e21.12b*) In $Q(R,T)$, every nonzero element of $T$ is a unit.
# Links
* [[A First Course in Abstract Algebra 7th Edition by Fraleigh|Fraleigh]] 