* Let $f:M\to N$ be a [[Real Analysis|smooth]] mapping of the domain $M$ of a vector space into a domain $N$ of a [[Vector Space|vector space]]. The **image** of the  vector $v$ with origin $x$ under the mapping $f$ denoted $f_{\ast x}(v)$ is the velocity vector with which the moving point $f(\varphi(t)$ leaves the point $f(x)$ when the moving point $\varphi(t)$ leaves the point $x$ with velocity $v$. Thus
  $$
  f_{\ast x} (v) =\frac{d}{dt} \Big|_{t=0} f(\varphi(t))
  $$
  Such that $\varphi(0) = x$ and also 
  $$
  \frac{d}{dt}\Big|_{t=0} \varphi(t) = v
  $$
	* $f_{\ast x}(v)$ does not depend on the motion $\varphi$ provided $\varphi(t)$ leaves $x$ with velocity $v$. 
		* *Intuition*: This follows from the smoothness of the mapping.

* The set of velocity vectors leaving $x\in M$ is a vector space called the **tangent space**. We denote this as $T_x M$. 
	* The mapping $f_{\ast  x}: T_x M \to T_{f(x)} N$ is [[Linear Transformation|linear]].  In fact  $f_{\ast x}=\partial f/\partial x$.  
	  Furthermore, let $\set{x_1,\dots,x_m}$ and $\set{y_1,\dots,y_n}$ be the bases of $M$ and $N$. Then
	  $$
	  (f_{\ast x} v)_i = \sum_i \frac{\partial f_i}{\partial x_j} v_j
	  $$
	  In other words, $f$ is the [[Differential Calculus|Jacobian]] and applying it to $x\in M$ is equivalent to matrix-vector multiplication. 
	* The set of points 
	  $$
	  \bigg\{x\in M  \ \bigg| \ \frac{\partial f}{\partial x}  v = 0\bigg\}
	  $$
	  Is called the set of **critical points.**. Its image is the set of  **critical values**.

* A **tangent vector** to a domain $M$ at a point $x$ is an [[Relation|equivalence class]] of smooth motions $\varphi: \mathbb{R} \to M$ for which $\varphi(0)=x$.  The equivalence class $\varphi \sim \psi$ is defined as follows: 
  
  The distance between the points $\varphi(t)$a and $\psi (t)$ in any [[Vector Coordinate System|coordinate system]] is $o(|t|)$ as $t\to 0$. or more formally
  $$
  \lim_{t\to 0}|| \varphi(t) -\psi(t) || = o(|t|)
  $$


# Links
* [[Ordinary Differential Equations by Arnold]]
* [[Differential Calculus]]