* Let $V$ and $W$ be a [[Vector Space]]. A [[Relation|function]] $T:V\to W$ is called a **linear transformation** from $V$ into $W$ if $\forall x,y\in V$ and $c\in F$  we have
  
  $$
  \begin{split}
  T(x+y) &= T(x) + T(y) \\
  T(cx) &= cT(x)
  \end{split}
  $$
  We refer to $T$ as **linear**
	* If $T$ is linear, then $T(\emptyset) = \emptyset$ 
	* $T$ is linear if and only if $T(ax + y) = aT(x) + T(y)$ for all $x,y\in V$ and $a\in F$
	* $T$ is linear if and only if $x_1,\dots, x_n \in V$ and $a_1,\dots, a_n\in F$ we have
	  $$
	  T\left(\sum_{i=1}^n a_ix_i\right) = \sum_{i=1}^n a_i T(x_i)
	  $$
* The **identity transformation** is defined as $I_V : V\to V$ where $I_V(x) = x$ $\forall x\in V$ 
  
  The **zero transformation** is defined as $T_0 : V\to W$ by $T_0(x)=0$ $\forall x\in V$ 

* A **linear operator** is of the form $T:V\to V$, that is, it is an endomorphism.

* (*Friedberg 2.7*) *The space of linear transformations form a vector space*. More formally, let $T,U:V\to W$ be arbitrary functions and $a\in F$. 
  
  Define $(T+U)(x)=T(x) +U(x)$ and $(aT)(x) = aT(x)$. 
  
  Then $aT + U$ is linear and the collection of linear transformations form a vector space denoted $\mathcal{L} (V,W)$.

# Topics
* [[Dimension Theorem]]
* [[Linear Transformation Matrix Isomorphism]]
* [[Matrix Diagonalization]]

# Misc
* Let $V$ be a vector space and $W_1\le V$. A function $T:V\to V$ is called a **projection** on $W_1$ if
	* There exists $W_2\le V$ such that $V = W_1 \oplus W_2$. [^oplus]
	* For $x=x_1 + x_2$ where $x_1\in W_1$ and $x_2 \in W_2$ we have $T(x)=x_1$
* (*Friedberg e2.1.22*) $T$ is linear
* (*Frieidberg e2.1.23*) If $W_1=R(T)$, then $W_2=N(T)$ so that
  $$
  V = N(T) \oplus R(T)
  $$

* Let $V$ be a vector space and $T:V\to V$ be linear. A subspace $W\le V$ is $T$-**invariant** if $T(x)\in W$ $\forall x\in W$. That is, $T(W)\subseteq W$

[^oplus]: See [[Vector Sum and Direct Sum]]
# Links
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]] - Ch. 2