* Let $A$ and $B$ be sets. A **Relation** $R$ between $A$ and $B$ is a subset of $A\times B$. 
  
  If two objects are in a relation we denote it as $(a,b)\in R$ (read as $a$ is in an $R$-relation with $b$ or $aRb$) 
  
  The order of the tuple in the relation is important

* An **equivalence relation** is a relation on the set $X$ such that the following properties are true $\forall x,y,z\in X$ 
	* *Reflexivity*: $(x,x)\in R$
	* *Symmetry*: $(x,y)\in R \iff (y,x)\in R$
	* *Transitivity*: $(x,y)\in R \wedge (y,z)\in R \implies (x,z)\in R$
* An **equivalence class** of $a$ with respect to an equivalence relation $R$ on the set $X$ is a set $A$ such that 
  
  $$
  A = \{x\in X\mid (x,a)\in nR\}
  $$
  It allows us to cluster different elements of the set $A$ into families.
# Functions 
* A **function** is a mapping between two sets $X$ and $Y$ that associates each element in $X$ to one element in $Y$. This is denoted $f:X\to Y$.  
	* $X$ and $Y$ are called the **domain** and **codomain** respectively.
	* We denote $x\in X$ and $f(x)\in Y$ such that $x\mapsto f(x)$. This defines a **mapping**
	* The **image / range** of $f$ under a subset $A \subseteq X$ is defined as the set 
	  $$
	  f(A) = \{f(x)\in Y \mid x\in A\}
	  $$
	  If $A$ contains a single element $x$, we denote the image of $x$ as $f(x)$
	* The **pre-image** of $f$ under a subset $B\subseteq Y$ is defined as the set 
	  
	  $$
	  f^{-1}(B) = \{x\in X \mid f(x) \in B\}
	  $$
	  If $B$ contains a single element $y$, then we say that $y$ is a pre-image of $x$ where $y=f^{-1}(x)$. 
	* We say that the pre-image of $f$ in its entirety is $f^{-1}(Y)$
	  
	  Likewise the image of $f$ is $f(X)$. 


* A function is **injective** if every element of the domain is mapped to at most one element in the codomain. More formally
  
  $$
  \forall x_1,x_2\in X, f(x_1)=f(x_2)\implies x_1=x_2
  $$

* A function is **surjective** if every element of the codomain is the image of at least one element in the domain. More formally
  
  $$
  \forall y\in Y,\exists x\in X, f(x)=y
  $$
* A function is **bijective** if it is both injective and surjective.  Specifically, every element in the domain is mapped to one and only one element in the codomain.

* Let $f:A\to B$ and $g: B\to C$. The **composition** of $g$ with $f$ is a function defined as $h:A\to C$ where
  
  $$
  \forall x \in A \ \ \ h(x) = g(f(x))
  $$
  We denote this as $h=g\circ f$. 
	* The composition of two injections is an injection
	* The composition of two surjections is a surjection
	* The composition of two bijections is a bijection.
# Theorems
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