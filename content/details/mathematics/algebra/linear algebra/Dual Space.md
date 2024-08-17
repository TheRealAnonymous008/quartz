* For a [[Vector Space]] $V$ over $F$, the **dual space** of $V$ to be the vector space $\mathcal{L}(V,F)$ denoted $V^\ast$.
  In other words, it consists of all the set of [[Linear Transformation|linear]] functionals of the form $\phi:V\to F$ 

* Clearly from the [[Dimension Theorem]]: 
  $$
  \dim(V^\ast) = \dim(V)
  $$
  And $V\cong V^\ast$.

* (*Friedberg 2.25*) Suppose $V$ is a finite-dimensional vector space with the ordered [[Linear Combination|basis]] $\beta=\{x_1,\dots,x_n\}$. Let $f_i$ be the coordinate functions with respect to $\beta$. Let $\beta^\ast=\{f_1,\dots,f_n\}$. 
  
  Then $\beta^\ast$ is an ordered basis for $V^\ast$ and for any $f\in V^\ast$ we have
  $$
  f= \sum_{i=1}^n f(x_i) f_i
  $$
  $\beta^\ast$ is called the **dual basis**

* (*Friedberg 2.26*) Let $V$and $W$ be finite-dimensional vector spaces over $F$ with ordered bases $\beta$ and $\gamma$ respectively. For any linear transformation $T:V\to W$, the mapping $T^T:W^\ast\to V^\ast$ defined by $T^T(g)=gT$  $\forall g\in W^\ast$ is a linear transformation such that
  $$
  [T^T]^{\beta^\ast}_{\gamma^\ast} = ([T]_\beta^\gamma)^T 
  $$
  In fact, $T^T$ is the **transpose** of $T$ (see more [[Matrix|here]])

* (*Friedberg Lemma 2.27*) We define $\hat{x}(f) = f(x)$ 
  
  Let $V$ be a finite-dimensional vector spaces and let $x\in V$. If $\hat{x}(f)=0$ $\forall f\in V^\ast$, then $x=0$. 
* (*Friedberg 2.27*) Let $V$ be a finite-dimensional vector space, and let $\psi:V\to V^{\ast\ast}$ be defined by $\psi(x)=\hat{x}$. Then $\psi$ is an isomorphism.
	* (*Friedberg 2.27.1*) Let $V$ be a finite-dimensional vector space with dual space $V^\ast$. Then every ordered basis $V^\ast$ is the dual basis of some basis of $V$
	* (*Friedberg e.2.6.11*) Let $V$ and $W$ be finite dimensional vector spaces over $F$ and $\psi_1:V\to V^{\ast\ast}$ and $\psi_2:W\to W^{\ast\ast}$ be isomorphisms as defined above. Let $T:V\to W$ be linear rand define $T^{TT}=(T^T)^T$
	  
	  Then 
	  $$
	  \psi_2 T = T^{TT} \psi_1
	  $$

* For finite dimensional vector spaces $V\cong V^\ast$

* (*Friedberg e2.6.9*) Let $T:F^n\to F^m$ be a function. $T$ is linear if and only if there exists $f_1,\dots,f_m\in (F^n)^\ast$ such that $\forall x \in F^n \ \ \ T(x)=(f_1(x),\dots,f_m(x))$  

* The **annihilator** $S^0=\{f\in V^\ast \mid f(x) = 0 \forall x\in S\}$ is defined for a subset $S$ of $V$. 
* (*Friedberg e2.6.13*)
	* $S^0 \le V^\ast$
	* $W\le V$ and $x\notin W$ implies that there exists $f\in W^0$ such that $f(x)\ne 0$
	* $S^{00}= \text{span}(\psi (S))$ (see *Friedberg 2.27*) 
	* $W_1 = W_2 \iff W_1^0 = W_2^0$ where $W_1,W_2\le V$ 
	* $(W_1+W_2)^0 = W_1^0 \cap W_2^0$, where $W_1,W_2 \le V$. 
* (*Friedberg e2.6.14*) 
  $$
  \dim(W) + \dim(W^0) = \dim(V)
  $$
* (*Friedberg e2.6.15*) If $W$ is a finite dimensional vector space over $F$ and $T:V\to W$ is linear. 
  $$
  N(T^T) = (R(T))^0
  $$
* (*Friedberg e2.6.17*) $W$ is $T$-invariant if and only if $W^0$ is $T$-invariant

# Links
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]]