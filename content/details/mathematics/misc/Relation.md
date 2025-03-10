* Let $A$ and $B$ be sets. A **Relation** $R$ between $A$ and $B$ is a subset of $A\times B$. 
  
  If two objects are in a relation we denote it as $(a,b)\in R$ (read as $a$ is in an $R$-relation with $b$ or $aRb$) 
  
  The order of the tuple in the relation is important
	* We denote the set of relations between $A$ and $B$ as 
	  $$
	  \text{Rel(A,B)} = \mathcal P(A,B)
	  $$

* An **equivalence relation** is a relation on the set $X$ such that the following properties are true $\forall x,y,z\in X$ 
	* *Reflexivity*: $(x,x)\in R$
	* *Symmetry*: $(x,y)\in R \iff (y,x)\in R$
	* *Transitivity*: $(x,y)\in R \wedge (y,z)\in R \implies (x,z)\in R$
* An **equivalence class** of $a$ with respect to an equivalence relation $R$ on the set $X$ is a set $A$ such that 
  
  $$
  A = \{x\in X\mid (x,a)\in nR\}
  $$
  It allows us to cluster different elements of the set $A$ into families.

* The **diagonal relation** is defined as the relation from $S\to S$ such that 
  $$
  \Delta_S = \set{(x,x)\mid x\in S}
  $$

* A **partial ordering** is a relation $\le$ defined for pairs of elements of $S$ such that the following are true for certain elements.
	* *Reflexivity*: $\forall a\in S, a\le a$. 
	* *Antisymmetry*:  $a\le b \wedge b\le a \implies a = b$ 
	* *Transitivity*: $a\le b \wedge b\le c \implies a\le c$

# Functions 
* A **function** is a mapping between two sets $X$ and $Y$ that associates each element in $X$ to one element in $Y$. This is denoted $f:X\to Y$.  
	* $X$ and $Y$ are called the **domain** and **codomain** respectively.
	* We denote $x\in X$ and $f(x)\in Y$ such that $x\mapsto f(x)$. This defines a **mapping**. We say that $f(x)$ is the **value** of the function at $x$.
	* The **graph** of a function $f: X\to Y$ is the set of ordered pairs 
	  $$
	  \set{(x,f(x))\mid x \in X}
	  $$
	  Thus, *the graph of a function defines a relation with the functional property* that there is one and only one $y\in Y$ such that $(x,y)$ is in the graph. 
	* The domain, codomain, and graph of a function uniquely determine the function.  Conversely, the function uniquely determines the domain, codomain and graph.  

* *Most functions in mathematics preserve some kind of structure*. 


* The **image / range** of $f$ under a subset $A \subseteq X$ is defined as the set 
  $$
  f(A) = \{f(x)\in Y \mid x\in A\}
  $$
  If $A$ contains a single element $x$, we denote the image of $x$ as $f(x)$ [^not_1]
  
  If we do not specify $A$, we implicitly assume we have $A=X$ so that the image of $f$ in this case is
  $$
  f(X)=\set{f(x)\in Y \mid x\in X}
  $$

* The **pre-image** of $f$ under a subset $B\subseteq Y$ is defined as the set 
  
  $$
  f^{-1}(B) = \{x\in X \mid f(x) \in B\}
  $$
  If $B$ contains a single element $y$, then we say that $y$ is a pre-image of $x$ where $y=f^{-1}(x)$. 
* We say that the pre-image of $f$ in its entirety is $f^{-1}(Y)$
  
  Likewise the image of $f$ is $f(X)$. 

[^not_1]: We sometimes notate this as $f[A]$ if the context is unclear

* A function is **injective / one-to-one** if every element of the domain is mapped to at most one element in the codomain. More formally
  
  $$
  \forall x_1,x_2\in X, f(x_1)=f(x_2)\implies x_1=x_2
  $$
  Or the contrapositive
  $$
  \forall x_1,x_2\in X, x_1 \ne x_2\implies f(x_1)\ne f(x_2)
  $$

* A function is **surjective / onto** if every element of the codomain is the image of at least one element in the domain. More formally
  
  $$
  \forall y\in Y,\exists x\in X, f(x)=y
  $$
  Equivalently, a function is surjective if 
  $$
  f(X) = Y
  $$
* A function is **bijective / one-to-one correspondence** if it is both injective and surjective.  Specifically, every element in the domain is mapped to one and only one element in the codomain.


* Let $f:A\to B$ and $g: B\to C$. The **composition** of $g$ with $f$ is a function defined as $h:A\to C$ where
  
  $$
  \forall x \in A \ \ \ h(x) = g(f(x))
  $$
  We denote this as $h=g\circ f$. 
	* The composition of two injections is an injection
	* The composition of two surjections is a surjection
	* The composition of two bijections is a bijection.

* The **inclusion map** is the function $i:A\to B$ that sends $x\in A$ to $x$, treated as an element of $B$. 

* If $X_1,\dots,X_n$ are sets, then the cartesian product $X= X_1\times \dots\times X_n$ has associated **projection functions** denoted $\text{proj}_i : X_1\times\dots\times X_n\to X_i$ where if $x_i\in X_i$ then 
  $$
  \text{proj}_i(x_1,\dots, x_n) = x_i
  $$
  That is, we disregard all but the $i$-th element in the ordered tuple. 

* Let $X,Y,Z$ be sets and $f:X\to Y, g: X\to Z$ be functions. The function  $\braket{f,g} : X\to Y\times Z$ is defined by
  $$
  \forall x \in X : \braket{f,g}(x) =(f(x),g(x))
  $$
* Let $X,Y,A,B$ be sets and $f:X\to A, g:Y\to B$ be functions. Then the **Cartesian product** of two functions is $f\times g: X\times Y\to A\times B$ is defined by
  $$
  (f\times g)(x,y) = (f(x),g(y))
  $$

* Let $f:X\to Y$ and $A\subseteq X$. The **restriction** of $f$ to $A$, denoted $f|_A: A\to F$ is the function defined as
  $$
  \forall x\in A : \ f|_A(x) = f(x)
  $$
  It can also be described as the composite $f\circ i$ where $i: A\to X$ is the inclusion function. 
  
  We say that $f$ **extends** $f|_A$.
* If $Y\subseteq B$ Then $f:X\to Y$ is called the **corestriction** of the function $j\circ f : X\to B$ to $Y$ where $j:Y\to B$ is the inclusion function.
* A function's *restriction makes the domain smaller*. A function's *corestriction makes the codomain smaller*.
  
# Theorems
* If $A\subseteq B$, then $f(A)\subseteq f(B)$.
	* *Proof:* Take  $x\in f(A)$. Then $\exists a\in A$ such that $f(a)=x$ But also $a\in B$ since $A\subseteq B$. Therefore $f(a)\in f(B)$ as well.

* (**Schroeder-Bernstein Theorem**) Let $X$ and $Y$ be sets. If there exists injective mappings $f:X\to Y$ and $g:Y\to X$, then there exists a bijective mapping $h:X\to Y$. 
  
  *Proof (Konig)*:  
  
  Assume without loss of generality that $X$ and $Y$ are disjoint otherwise we may label some of the elements of $X$ and $Y$  to make them different.  
  
  Consider the sequence for $x\in X$ and $y\in Y$. 
  $$
  \dots, f^{-1}g^{-1}(x),g^{-1}(x), x,f(x),g(f(x)), \dots
  $$
  We show that each $x\in X$ and $y \in Y$ appears exactly once in this sequence. 
  
  It follows that if $x\in X$ or $y\in Y$ appeared in more than one such sequence, all elements to their left and to their right must be the same (by the injectivity of $f$ and $g$). As such, these sequences form a partition of $X$ and $Y$. Call this sequence a family of $x$.
  
  This implies, that we only need to consider a bijective mapping for each family.  
  
  Let $\{x\}$ be a family. Now, for each element in this sequence, any of these cases may happen. Define the bijection $h$ according to these cases.
1. The sequence ends with an element in $X$. In which case, define $h=f$ .
2. The sequence ends with an element in $Y$. In which case define $h=g$
3. The sequence has the same endpoints (i.e., it will eventually lead back to $x$). In which case, either $f$ or $g$ will do for $h$.
4. The sequence is infinitely long. In which case, either $f$ or $g$ will do.

# Links
* [[Set Theory]]
* [[Category Theory for Computing Sciences by Barr and Wells]]