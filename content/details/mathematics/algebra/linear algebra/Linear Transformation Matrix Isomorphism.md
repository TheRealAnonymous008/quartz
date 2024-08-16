* Every [[Linear Transformation]] is associated with a [[Matrix]].
* Let $V$ and $W$ be finite-dimensional vector spaces with ordered [[Linear Combination|basis]] $\beta=\{x_1,\dots,x_n\}$ and $\gamma =\{y_1,\dots, y_m\}$.
  
  Let $T:V\to W$ be linear. Then, we have $a_{ij}\in F$ as scalars such that
  
  $$
  T(x_j) = \sum_{i=1}^m a_{ij} y_i
  $$
  
  The $m\times n$ matrix $A$ defined by $A_{ij}=a_{ij}$ is the matrix that represents $T$ in the ordered bases $\beta$ and $\gamma$. We denote this $A=[T]_\beta^\gamma$.
  
  If $V=W$ and $\beta=\gamma$, then we write $A=[T]_\beta$

* (*Friedberg 2.8*) Let $V$ and $W$ be finite dimensional vector spaces with ordered bases $\beta$ and $\gamma$ and $T,U:V\to W$ be linear. Then
	* $[T+U]_\beta^\gamma = [T]_\beta^\gamma + [U]_\beta^\gamma$ 
	* $[aT]_\beta^\gamma = a[T]_\beta^\gamma$

* *We have an [[Group Isomorphism|isomorphism]] between the set of matrices and the set of linear transformations.*

* Composition of linear transformations is analogous to [[Matrix Multiplication]].
	* (*Friedberg 2.9*) Let $V,W,Z$ be vector spaces and $T:V\to W$, $U:W\to Z$ be linear. Then $UT:V\to Z$ is linear. 
	* (*Friedberg 2.10*) Let $V$ be a vector space and $T,U_1,U_2\in \mathcal{L}(V)$. Then
		* $T(U_1 + U_2) = TU_1 + TU_2$
		* $(U_1+U_2)T = U_1T + U_2 T$
		* $T(U_1U_2) = (TU_1)U_2$
		* $TI=IT=T$
		* $a(U_1U_2) = (aU_1)(U_2) = U_1(aU_2)$ $\forall a\in F$.
	* (*Friedberg 2.11*) Let $V,W,Z$ be finite-dimensional vector spaces with ordered bases $\alpha,\beta,\gamma$ respectively. Let $T:V\to W$ and $U:W\to Z$ be linear. Then
	  $$
	  [UT]_\alpha^\gamma = [U]^\gamma_\beta [T]^\beta_\alpha
	  $$
	  
	  An immediate corollary of this if all bases are the same
	  
	  $$
	  [UT]_\beta = [U]_\beta[T]_\beta
	  $$
	* (*Friedberg 2.12*) $[I_V]_\beta = I_n$

* (*Friedberg 2.15*) Let $V$ and $W$ be finite dimensional vector spaces having ordered bases $\beta$ and $\gamma$ respectively and let $T:V\to W$ be linear. Then for each $x\in V$
  
  $$
  [T(X)]_\gamma = [T]_\beta^\gamma [x]_\beta
  $$
	* Another way to say this is
	  $$
	  L_A\phi_\beta = \phi_\gamma T
	  $$

* Let $A\in M_{m\times n}(F)$. We denote $L_A:F^n\to F^m$, defined by $L_A(x)=Ax$ for each $x\in F^n$. We call $L_A$ a **left multiplication transformation**
* (*Friedberg 2.16*) Let $A\in M_{m\times n}(F)$. Then the left-multiplication transformation $L_A: F^n\to F^m$ is linear. Furthermore, if $B$ is any other $m\times n$ matrix with entries from $F$ and $\beta$ and $\gamma$ are the standard ordered bases for $F^n$ and $F^m$ respectively, then
	* $[L_A]_\beta^\gamma = A$
	* $L_A=L_B \iff A =B$
	* $L_{A+B}=L_A + L_B$
	* $L_{aA} = aL_A$ $\forall a \in F$
	* If $T:F^n\to F^m$ is linear, then there exists a unique matrix $C\in M_{m\times n}(F)$ such that $T=L_C$. In fact, $C=[T]_\beta^\gamma$ 
	* If $E\in M_{n\times p}(F)$ then $L_{AE}=L_AL_E$
	* If $m=n$, then $L_{I_n} = I_{F^n}$ 

# Invertibility
* Let $V$and $W$ be vector spaces and let $T:V\to W$ be linear. $T$ has an **inverse** $U:W\to V$ if $TU=I_W$ and $UT=I_V$. The inverse is unique and we denote it as $U=T^{-1}$. We say that $T$ is **invertible** if $T$ has an inverse
  
  The following hold true for invertible functions $T,U$
	* $(TU)^{-1}=U^{-1}T^{-1}$
	* $(T^{-1})^{-1}=T$. $T^{-1}$ is also invertible.

* (*Friedberg 2.18*) Let $V,W$ be vector spaces and $T:V\to W$ be linear and invertible. Then $T^{-1}:W\to V$ is also linear.

 * If $T$ is a linear transformation between vector spaces of equal finite dimension, then being invertible, one-to-one, and onto are equivalent (see *Friedberg 2.5*)

* (*Friedberg 2.19Lem*) Let $V,W$ be finite dimensional and $T:V\to W$ be linear. If $T$ is invertible, then $\dim(V)=\dim W$ 
* (*Friedberg 2.19*) Let $\beta,\gamma$ be finite ordered bases for $V$ and $W$ respectively and $T:V\to W$ be linear. Then $T$ is invertible if and only if $[T]_\beta^\gamma$ is [[Matrix Inversion|invertible]]. In particular
  $$
  [T^{-1}]_\gamma^\beta = ([T]_\beta^\gamma)^{-1}
  $$
* (*Friedberg 2.19.1*) Let $V$ be a finite dimensional vector space with ordered basis $\beta$ and $T:V\to V$ be linear. Then $T$ is invertible if and only if $[T]_\beta$ is invertible. Also
  
  $$
  [T^{-1}]_\beta = [T]_\beta^{-1}
  $$
* (*Friedberg 2.19.2*) Let $A\in M_{n\times n}(F)$. $A$ is invertible if and only if $L_A$ is invertible. Also
  $$
  (L_A)^{-1} = L_{A^{-1}}
  $$
* (*Friedberg 2.21*) Let $V,W$ be finite dimensional vector spaces over $F$ with $\dim(V) = n$ and $\dim(W)=m$. Let $\beta, \gamma$ be ordered bases for $V$ and $W$ respectively. Then the function $\Phi:\mathcal{L}(V,W)\to M_{m\times n}(F)$ defined by 
  $$
  \Phi(T) = [T]_\beta^\gamma
  $$
  for $T\in \mathcal{L}(V,W)$ is an isomorphism.
	 * (*Friedberg 2.21.1*) $\mathcal{L}(V,W)$ is dimensional of dimension $\dim(V) \dim(W)$


# Links
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]]