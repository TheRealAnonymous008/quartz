* A **diffeomorphism** is a [[Real Analysis|smooth]] [[Group Homomorphism|mapping]] whose inverse is also smooth. 
* A **one parameter diffeomorphism [[Fundamental Constructs of Group Theory|group]]** is a [[Phase Flow|phase  flow]] whose elements are diffeomorphisms satisfying the additional condition that $g^tx$ depends smoothly on both $t$ and $x$.
* A **one parameter group of linear transformations** is a one parameter diffeomorphism group whose elements are [[Linear Transformation|linear transformations]]. 

* Every one parameter diffeomorphism group has an associated [[Ordinary Differential Equation|differential equation]].
* Every diffeomorphism gives a [[Vector Space|vector space]] isomorphism.


# Diffeomorphisms as Actions
* We can interpret a diffeomorphism as a [[Group Action|group action]] that can act on a variety of objects
* The image $g_\ast v$ of the [[Vector Field|vector field]] $v$ in $M$ under a diffeomorphism $g$ of a domain $M$ onto $N$ is the vector field $w$ defined by the formula 
  $$
  w(y) = (g_{\ast x})v (x)
  $$
  Where 
  $$
  x = g^{-1} y
  $$
* A diffeomorphism taking a vector field $v$ to the field $w$ takes the phase curves of the field $v$ to the [[Integral Curve|phase curves]] of the field $w$. 
* (*Arnold 5.4.1*) Suppose that there is a direction field defined in the domain $M$.  Under the action of a diffeomorphism $g:M\to N$, the integral curves of the original direction field on $M$ map into integral curves of the direction field on $N$ obtained by taking the action $g$ on the original fiield. 

## Change of Variables
* $f_{\ast x} : T_xM \to T_{f(x)} N$  (see [[Tangent Space|here]]. is independent of the coordinate system used for both $T_xM$ and $T_{f(x)}N$ provided that both are connected to the Cartesian coordinate system by a diffeomorphic change of variables.
  
  Thus, *diffeomorphisms can be used to transform an [[Ordinary Differential Equation|ODE]] to one we know how to solve through a change in variables*. 


* The vector field on the $x$- axis with a unique component is denoted  $\partial/\partial x$.
	* In general, let $\set{x_1,\dots,x_n}$ be a fixed coordinate system in $\mathbb{R}^n$. Then the basis vector fields are denoted 
	  $$
	  \bigg\{\frac{\partial}{\partial x_1}, \dots, \frac{\partial}{\partial x_n }\bigg\}
	  $$
	  The vector field with components $\set{v_1,\dots, v_n}$ is denoted 
	  $$
	  \sum_{i=1}^n \frac{\partial}{\partial x_i} v_i = \frac{\partial}{\partial x_1} v_ 1 + \dots + \frac{\partial}{\partial x_n} v_n
	  $$
	* Notice that the basis vector fields *represent a change of coordinates matrix*.  If we have a given vector field, we can then obtain the vector fields in this coordinate system using matrix vector multiplication (which produces the sum above).

* (*Arnold 5.3.1*) Let $w$ be the image of the vector field $v$ in $M$ under a diffeomorphism $g$ of a domain $M$ onto a domain $N$ (i.e., $w=g_\ast v$). 
  
  The differential equations
  $$
  \begin{split}
  \dot x &= v(x) & \ \ \ x\in M \\
  \dot y &= w(y) & \ \ \ y\in N
  \end{split}
  $$
  Are equivalent in the sense that if $\varphi : I\to M$ is a solution of the first, then $g\circ \varphi : I \to N$ is a solution of the second equations and conversely. 
  
  Thus, the change of variables $y=g(x)$ maps the first equation onto the second. Similarly, the change of variables$g^{-1}(y)$ maps the second onto the first.
	* *Proof*: Verify that the proposed solutions are solutions
	  $$
	  \frac{d}{dt} g \circ \varphi = g_{\ast x} \dot \varphi(t) = g_{\ast x }v(x) = w(y) 
	  $$
	  With $x=\varphi(t)$, $y=g(\varphi(t))$.

* To solve the differential equation 
  $$
  \frac{dx}{dt} = v(t,x)
  $$
  It suffices to construct a diffeomorphism that maps the direction field of the above to an equation we know how to solve.

* Let $\set{g^t : M\to M}$ be a one parameter diffeomorphism group and $f:M\to N$ be another onto diffeomorphism.
  
  The **image** of the [[Phase Flow|flow]] $\{g^t\}$ under the action of the diffeomorphism $f$ is the flow $\set{h^t : N \to N}$ where $h^t = fg^t f^{-1}$. 
  
  The [[Permutations and Orbits|orbits]] of $\set{g^t}$ are mapped to the orbits of $\set{h^t}$.  We say that  $\set{g^t}$ and $\set{h^t}$ are **equivalent**. 
	* Clearly the image $\set{h^t}$ is also a one-parameter diffeomorphism group.
	* (*Arnold 5.5.1*)  The diffeomorphism $f$ takes the vector field $v$ into the field $w$; Conversely, if a diffeomorphism takes $v$ into $w$, then it takes $\set{g^t}$ to $\set{h^t}$.


# Links
* [[Ordinary Differential Equations by Arnold]]