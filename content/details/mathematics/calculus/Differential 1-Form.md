* Every differential equation determines a direction field in the region $V\subseteq \mathbb{R}\times\mathbb{R}^n$ -- the line attached at the point $(t,x)$ has slope $v(t,x)$.  This is called the **direction field** of $v$. 
  
  Every integral curve of the direction field satisfies
  $$
  \dot x = v(t,x)
  $$

* (*Arnold 1.1*) For any vector $A$ tangent to the graph of a smooth function $x=\varphi(t)$ the ratio $dx(A)/dt(A)$ is equal to the derivative $dx/dt$ of the function $\varphi$ at the corresponding point.
  
  Here $dx(A)$ means multiplying $dx$ with the component of $A$ corresponding to $x$.

* A **differential 1-form** is a [[Relation|function]] where attached vectors are linear at each given point where they are attached. That is, they can be described using smooth functions $f_i$ and are of the form
  $$
  \omega = f_1(x) \  dx_1 + f_2(x) \ dx_2 +\dots f_n(x) \ dx_n
  $$
	* They can be integrated along oriented closed segments of  curves. Let $\Gamma$ be a segment of the curve and $\gamma:I\to \mathbb{R}^n$ be a smooth mapping from the interval $I=[a,b]$. The integral of the form $\omega$ over $\Gamma$ is defined as
	  
	  $$
	  \int_\Gamma \omega = \int_I \omega(\gamma') \ du
	  $$
	  Where $\gamma'=\frac{d\gamma}{du}$ 
	  
	* (*Arnold 1.2*) **Parameter / Coordinate Independence of Differential 1-form**: The Integral of a 1-form over an oriented closed segment of a curve is independent of the parameter for parameters giving the same orientation. When the orientation is reversed, the integral changes sign. 
	* (*Arnold 1.3*) The integral of a 1-form $f(x) dx$ over a segment of a curve on which $x$ can be taken as parameter coincides with the usual definite integral of the function $f$

* The differential manifold is another way to look at generalizing line integrals for manifolds for which the dot product may not be defined. 
  
  The key insight to generalizing [[Integral Calculus|line integrals]] to such manifolds is to "*absorb the dot product into the integrand*". What we get is the definition of the 1-form.

# Links
* [[Ordinary Differential Equations by Arnold|Arnold]] - Ch. 1