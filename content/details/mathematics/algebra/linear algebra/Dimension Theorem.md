* Let $V$ and $W$ be [[Vector Space|vector spaces]], and $T:V\to W$ be [[Linear Transformation|linear]]. The **null space** or [[Group Homomorphism|kernel]] $N(T)$ is the set 
  $$
  N(T) = \{x \in V \mid  T(x) = 0\}
  $$
  The  **column space** of $T$ is defined as 
  $$
  R(T) = \{T(x) \mid x\in V \}
  $$

* (*Friedberg 2.1*) Let $V$ and $W$ be vector spaces and $T:V\to W$ be linear. Then $N(T)$ and $R(T)$ are [[Vector Subspace|subspaces]] of $V$ and $W$ respectively.
* (*Friedberg 2.2*) Let $V$ and $W$ be vector spaces and $T:V\to W$ be linear. If $V$ has a [[Linear Combination|basis]] $\beta = \{x_1,\dots, x_n\}$ then 
  
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

* (*Friedberg e2.4.18,  Friedberg 3.3*) Let $T:V\to W$ be a linear transformation from an $n$-dimensional vector space $V$ to an $m$-dimensional vector space $W$. Let $\beta, \gamma$ be ordered bases for $V,W$ respectively. Let $A=[T]_\beta^\gamma$ . Then
  
  $$
  \begin{split}
  \text{rank} (T) &= \text{rank}(L_A) \\
  \text{nullity}(T) &= \text{nullity}(L_A) 
  \end{split}
  $$
	* *Intuition*: This follows because [[Linear Transformation Matrix Isomorphism|linear transformations are isomorphic to matrices]]. Hence, vector subspaces are preserved and so are Null Space and Column Space


# Links
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]]