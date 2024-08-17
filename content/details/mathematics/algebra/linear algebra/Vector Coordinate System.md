* Let $\beta = \{x_1, \dots , x_n\}$ be an ordered [[Linear Combination|basis]] for a finite dimensional [[Vector Space]] $V$. For $x\in V$ we define the **coordinate vector** of $x$ relative to $\beta$ denoted $[x]_\beta$ by 
  $$
  [x]_\beta = 
  \begin{pmatrix}
  a_1 \\
  \vdots \\
  a_n
  \end{pmatrix}
  $$
  where $x = \sum_{i=1}^n a_ix_i$. 
	* (*Friedberg e2.2.7*) Let $V$ be an $n$-dimensional vector space with an ordered basis $\beta$. Define $T:V\to F^n$ by $T(x)=[x]_\beta$. $T$ is [[Linear Transformation|linear]].
	* The **standard representation of** $V$ is denoted $\phi_\beta: V\to F^n$ and is defined by 
	  $$
	  \phi_\beta(x) = [x]_\beta
	  $$
		* For any finite-dimensional vector space $V$ and ordered basis $\beta$, $\phi_\beta$ is an isomorphism.

* Let $V$ and $W$ be finite-dimensional vector spaces with ordered [[Linear Combination|basis]] $\beta=\{x_1,\dots,x_n\}$ and $\gamma =\{y_1,\dots, y_m\}$.
  
  Let $T:V\to W$ be linear. Then, we have $a_{ij}\in F$ as scalars such that
  
  $$
  T(x_j) = \sum_{i=1}^m a_{ij} y_i
  $$
  
  The $m\times n$ [[Matrix]] $A$ defined by $A_{ij}=a_{ij}$ is the matrix that represents $T$ in the ordered bases $\beta$ and $\gamma$. We denote this $A=[T]_\beta^\gamma$.
  
  If $V=W$ and $\beta=\gamma$, then we write $A=[T]_\beta$
# Change of Coordinates
* (*Friedberg 2.23*) Let $\beta$ and $\beta'$ be two ordered bases for a finite dimensional vector space $V$. Let $Q=[I_V]_{\beta'}^\beta$ Then
	* $Q$ is invertible
	* $\forall v\in V$, $[v]_\beta=Q[v]_{\beta'}$
* The matrix $Q=[I_V]_{\beta'}^\beta$ is called the **change of coordinate matrix**. *It changes $\beta$' coordinates into $\beta$ coordinates* 

* (*Friedberg 2.24*) Let $T:V\to V$ be a linear transformation of the finite-dimensional vector space $V$ and let $\beta$ and $\beta'$ be ordered bases for $V$. Let $Q$ be the change of coordinate matrix which changes $\beta'$-coordinates into $\beta$ coordinates. Then
  
  $$
  [T]_\beta=Q^{-1}[T]_\beta Q
  $$
	* (*Friedberg e2.5.7*) Let $T:V\to W$ be a linear transformation from a finite-dimensional vector space $V$ to a finite dimensional vector space $W$. Let $\beta,\beta'$ be ordered bases for $V$ and $\gamma,\gamma'$ be ordered bases for $W$. Then 
	  $$
	  [T]_{\beta'}^{\gamma'} = P^{-1}[T]_\beta^\gamma Q
	  $$
	  Where $Q$ is the  change of coordinates matrix from $\beta'$-coordinates to $\beta$-coordinates
	  
	  And $P$ is the change of coordinates matrix from $\gamma'$-coordinates into $\gamma$ coordinates

* Let $A$ and $B$ be elements of $M_{n\times n}(F)$. We say that $B$ is **similar** to $A$ if there exists an invertible matrix $Q\in M_{n\times n}(F)$ such that
  $$
  B=Q^{-1}AQ
  $$
  Denote $A\sim B$
	* (*Friedberg e2.5.9*) If $A\sim B$ then $\text{tr}(A)=\text{tr}(B)$


* (*Friedberg e2.5.12*) Let $V$ be a finite-dimensional vector space over a field $F$ and $\{x_1,\dots,x_n\}$ be an ordered basis for $V$. Let $Q\in M_{n\times n}(F)$ be an invertible matrix with entries from $F$. Define
  $$
  x_j' = \sum_{i=1}^n Q_{ij}x_j
  $$
  And set $\beta'=\{x_1',\dots,x_n'\}$. $\beta'$ is a basis for $V$ and $Q$ is the change of coordinate matrix changing $\beta'$-coordinates into $\beta$ coordinates
# Links
* [[Linear Algebra by Friedberg Insel and Spence|Friedberg, Insel and Spence]]
* [[Linear Transformation Matrix Isomorphism]]