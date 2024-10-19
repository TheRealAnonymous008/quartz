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
* (*Arnold 5.4.1*) Suppose that there is a direction field defined in the domain $M$.  Under the action of a diffeomorphism $g:M\to N$, the integral curves of the original direction field on $M$ map into integral curves of the direction field on $N$ obtained by taking the action $g$ on the original field. 

* A diffeomorphism $g:M\to M$ is a **symmetry** of the vector field $v$ on $M$ if it maps the field into itself. That is 
  $$
  g_\ast v  = v
  $$
  We say that the vector field $v$ is **invariant** with respect to the symmetry $g$. 
	* A diffeomorphism $g:M\to M$ is a **symmetry** of a direction field on $M$ if it maps the direction field into itself. The direction field is **invariant** with respect to the symmetry  *Integral Curves map onto one another* 
	* A field is **invariant** with respect to a group of diffeomorphisms if it is invariant with respect to each transformation of the group. We say that the field **admits** the symmetry group.
	* *All [[Symmetric Group|symmetries]] of a given field form a group.* 


# Links
* [[Ordinary Differential Equations by Arnold]]