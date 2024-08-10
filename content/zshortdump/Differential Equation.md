* Differential Equations can be used to study processes that are deterministic, finite-dimensional, and differentiable. 
* The fundamental problem of the theory of differential equations is to determine or study the motion of some system using the [[Vector Field|phase velocity vector field]].  
* *Differential equations arise when the dynamics of a system is described by changes in state rather than explicit state values*. Analysis proceeds by transforming the problem into an analogous [[Geometry|geometric]] one in a vector field

# Ordinary Differential Equations
* An **integral curve** is a line that, at each point, is tangent to a vector field
  
  A necessary and sufficient condition for the graph of function $\varphi$ to be an integral curve is that the following relation hold for interval $I$
  
  $$
  \frac{d\varphi}{dt} = v(t,\varphi (t))
  $$
  A function $\varphi$ is a **solution** of the differential equation if
  $$
  \dot{x} = v(t,x)
  $$
  $\varphi$ satisfies the **initial condition** $(t_0, x_0)$ if $\varphi(t_0) = x_0$  

* Every differential equation determines a direction field in the plane -- the line attached at the point $(t,x)$ has slope $v(t,x)$.  This is called the **direction field** of $v$. 

* (*Arnold 1.1*) For any vector $A$ tangent to the graph of a smooth function $x=\varphi(t)$ the ratio $dx(A)/dt(A)$ is equal to the derivative $dx/dt$ of the function $\varphi$ at the corresponding point.

## Differential 1-forms
* A **differential 1-form** is a function where attached vectors are linear at each given point where they are attached. That is, they can be described using smooth functions $f_i$ and are of the form
  $$
  f_1(x) \  dx_1 + f_2(x) \ dx_2 +\dots f_n(x) \ dx_n
  $$
	* They can be integrated along oriented closed segments of  curves. Let $\Gamma$ be a segment of the curve and $\gamma:I\to \mathbb{R}^2$ be a smooth mapping from the interval $I=[a,b]$. The integral of the form $\omega$ over $\Gamma$ is defined as
	  
	  $$
	  \int_\Gamma \omega = \int_I \omega(\gamma') \ du
	  $$
	  Where $\gamma'=\frac{d\gamma}{du}$ 
	  
	* (*Arnold 1.2*) **Parameter / Coordinate Independence of Differential 1-form**: The Integral of a 1-form over an oriented closed segment of a curve is independent of the parameter for parameters giving the same orientation. When the orientation is reversed, the integral changes sign. 
	* (*Arnold 1.3*) The integral of a 1-form $f(x) dx$ over a segment of a curve on which $x$ can be taken as parameter coincides with the usual definite integral of the function $f$

* The differential manifold is another way to look at generalizing line integrals for manifolds for which the dot product may not be defined. 
  
  The key insight to generalizing line integrals to such manifolds is to "*absorb the dot product into the integrand*". What we get is the definition of the 1-form.

# Partial Differential Equations

# Links
* [Paul's Online Notes - Differential Equations](https://tutorial.math.lamar.edu/classes/de/de.aspx)
* [3B1B - Differential Equations](https://www.youtube.com/watch?v=p_di4Zn4wz4&list=PLZHQObOWTQDNPOjrT6KVlfJuKtYTftqH6&index=1)
* [[Ordinary Differential Equations by Arnold]]

* [[Differential Calculus]]
* [[Integral Calculus]]