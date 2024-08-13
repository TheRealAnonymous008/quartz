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

# Dimension Theorem
* Let $V$ and $W$ be vector spaces, and $T:V\to W$ be linear. The **null space** or [[Group Homomorphism|kernel]] $N(T)$ is the set 
  $$
  N(T) = \{x \in V \mid  T(x) = 0\}
  $$
  The  **range** of $T$ is defined as 
  $$
  R(T) = \{T(x) \mid x\in V \}
  $$

* (*Friedberg 2.1*) Let $V$ and $W$ be vector spaces and $T:V\to W$ be linear. Then $N(T)$ and $R(T)$ are subspaces of $V$ and $W$ respectively.
* (*Friedberg 2.2*) Let $V$ and $W$ be vector spaces and $T:V\to W$ be linear. If $V$ has a basis $\beta = \{x_1,\dots, x_n\}$ then 
  
  $$
  R(T) = \text{span} \{ T(x_1) ,\dots , T(x_n)\}
  $$

* If $N(T)$ and $R(T)$ are finite dimensional, then we define the **Nullity** of $T$ and the **Rank** of $T$ as  
  
  $$
  \begin{split}
  \text{nullity} ( T) &= \dim (N(T)) \\ 
  \text{rank} (T) &= \dim (R(T))
  \end{split} 
  $$
* (*Friedberg 2.3*) **Dimension Theorem**.  Let $V$ and $W$ be vector spaces and let $T:V\to W$ be linear. If $V$ is finite dimensional then 
  $$
  \text{nullity}(T) + \text{rank} (T) = \dim (V)
  $$
	* Extending the [[Linear Combination#Span and Basis|basis]] of $N(T)$ yields elements which, when applying the linear transformation, are in the span of $R(T)$. In fact, they form a basis of $R(T)$
* (*Friedberg 2.4*) $T$ is one to one if and only if $N(T) = \{0\}$ 
* (*Friedberg 2.5*) Let $V$ and $W$ be vector spaces of equal finite dimension and $T:V\to W$ be linear. Then $T$ is one-to-one if and only if $T$ is onto.
* (*Friedberg 2.6*) Suppose $V$ is finite-dimensional with basis $\beta = \{x_1,\dots,x_n\}$.  For any vectors $y_1,\dots,y_n\in W$, there exists exactly one linear transformation $T: V\to W$ such that $T(x_i) =y_i$ for $i=1,\dots,n$
  
  In other words: *The effect of a linear transformation is completely determined by its effect on the basis of the domain.*
	* (*Friedberg 2.6.1*) Let $V,W$  be vector spaces and suppose $V$ has a finite basis $\{x_1,\dots, x_n\}$. If $U,T:V\to W$ are linear, and $U(x_i)=T(x_i)$ for $i=1,\dots, n$ then $U=T$.
	* (*Friedberg e2.1.27*) Let $V,W$ be possibly infinite-dimensional spaces over a common field and $\beta$ be a basis for $V$. For Any function $f:\beta \to W$, there exists exactly one linear transformation $T:V\to W$ such that $T(x)=f(x)$ $\forall x\in B$

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