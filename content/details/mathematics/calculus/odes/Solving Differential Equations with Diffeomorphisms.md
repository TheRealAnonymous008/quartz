# Change of Variables
* $f_{\ast x} : T_xM \to T_{f(x)} N$  (see [[Tangent Space|here]]. is independent of the [[Vector Coordinate System|coordinate system]] used for both $T_xM$ and $T_{f(x)}N$ provided that both are connected to the Cartesian coordinate system by a [[Diffeomorphism|diffeomorphic]] change of variables.
  
  Thus, *diffeomorphisms can be used to transform an [[Ordinary Differential Equation|ODE]] to one we know how to solve through a change in variables*. 


* The [[Vector Field|vector field]] on the $x$- axis with a unique component  $v$ is denoted  $\partial v/\partial x$.  This allows us to *compute a diffeomorphism on a vector field*
	* In general, let $\set{x_1,\dots,x_n}$ be a fixed coordinate system in $\mathbb{R}^n$. Then the basis vector fields are denoted 
	  $$
	  \bigg\{\frac{\partial}{\partial x_1}, \dots, \frac{\partial}{\partial x_n }\bigg\}
	  $$
	  The vector field with components $\set{v_1,\dots, v_n}$ is denoted 
	  $$
	  \sum_{i=1}^n \frac{\partial}{\partial x_i} v_i = \frac{\partial}{\partial x_1} v_ 1 + \dots + \frac{\partial}{\partial x_n} v_n
	  $$
	* Notice that the basis vector fields *represent a change of coordinates matrix*.  If we have a given vector field, we can then obtain the vector fields in this coordinate system using matrix vector multiplication (which produces the sum above).
	* Another way to write this is with the Jacobian Matrix $J$.  Suppose we have functions $f_1,\dots, f_m$ and basis vector fields $v_1,\dots, v_m$ with 
	  $$
	  J  =\frac{\partial(f_1,\dots,f_m)}{\partial(x_1,\dots,x_n)} 
	  $$
	  Define 
	  $$
	  x = \begin{bmatrix}
	  \frac{\partial x_1}{\partial t} \\
	  \vdots  \\ 
	  \frac{\partial x_n}{\partial t}
	  \end{bmatrix}
	  $$
	  Then the change of variables is obtained as
	  $$
	  Jx
	  $$

* (*Arnold 5.3.1*) Let $w$ be the image of the vector field $v$ in $M$ under a diffeomorphism $g$ of a domain $M$ onto a domain $N$ (i.e., $w=g_\ast v$). 
  
  The [[Ordinary Differential Equation|differential equation]]
  $$
  \begin{split}
  \dot x &= v(x) & \ \ \ x\in M \\
  \dot y &= w(y) & \ \ \ y\in N
  \end{split}
  $$
  Are equivalent in the sense that if $\varphi : I\to M$ is a solution of the first, then $g\circ \varphi : I \to N$ is a solution of the second equations and conversely. 
  
  Thus, the change of variables $y=g(x)$ maps the first equation onto the second. Similarly, the change of variables $g^{-1}(y)$ maps the second onto the first.
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
  
  The **image** of the [[Phase Flow|flow]] $\{g^t : M \to M\}$ under the action of the diffeomorphism $f$ is the flow $\set{h^t : N \to N}$ where $h^t = fg^t f^{-1}$.  Alternatively, this can be written as 
  $$
  fh^t = g^t f
  $$
  For any $t$. 
  
  The [[Permutations and Orbits|orbits]] of $\set{g^t}$ are mapped to the orbits of $\set{h^t}$.  We say that  $\set{g^t}$ and $\set{h^t}$ are **equivalent**. 
	* Clearly the image $\set{h^t}$ is also a one-parameter diffeomorphism group.
	* (*Arnold 5.5.1*)  The diffeomorphism $f$ takes the vector field $v$ into the field $w$; Conversely, if a diffeomorphism takes $v$ into $w$, then it takes $\set{g^t}$ to $\set{h^t}$.

# Integration
* (*Arnold 6.2.1.*) Suppose a one-parameter group of symmetries of a direction field on the plane is known. Then the equation defined by this direction field can be integrated explicitly in a neighborhood of each nonstationary point of the symmetry group.
  
  A point is called **nonstationary** for a transformation group if not all transformations of the group leave it fixed

* (*Arnold 6.2.2*) In a neighborhood of every nonstationary point of action of a one parameter group of diffeomorphisms on the plane, one can choose coordinates $(u,v)$ such that the given one-parameter diffeomorphism group can be written in the form of a group of translations
  $$
  g^s(u,v) = (u + s, v)
  $$
  For sufficiently small $|u|, |v|, |s|$. 
  
  That is, $v$ indexes the orbits of a group and $u$ is simply the time of the motion.
	* *Proof*: This comes from the properties of group composition. In particular, consider the rectification below. Using a diffeomorphic mapping $\Phi$, map the $(u,v)$-plane to the figure below such that $\Phi(u,v) = g^u\gamma (v)$. The result then follows 
	  $$
	  g^s(u,v) = g^{s+u}\gamma(v) = g^sg^u \gamma(v) = (u+s, v)
	  $$
![[One Parameter Diffeomorphism Rectification.png|300]]
<figcaption> Rectification of a one-parameter diffeomorphism group. Image taken from  Arnold</figcaption>


* An equation is **homogeneous** if the direction field defining it on the plane is homogeneous; that is it is invariant with respect to the one parameter group of dilations.
  $$
  g^s (x,y)  =e^s (x,y)
  $$
	* If $K$ is an integral curve, then the curve $e^sK$ homothetic to it is also an integral curve. 
	* *Intuition*: An equation is homogeneous if, when all variables are scaled by some constant, the equation remains the same (after cancellation). 

* (*Arnold 6.3.1*) A homogeneous equation 
  $$
  \frac{dy}{dx} = F(x,y)
  $$
  Can be reduced to an equation with separable variables by the substitution $y=xv$ in the domain $x>0$. This performs a change of variables to $(x,v)$ coordinates

* The function $f$ is **homogeneous of degree $r$** if it satisfies
  $$
  f(e^st) = e^{rs} f(t) 
  $$
	* (*Arnold 6.3.2*) **Euler's Theorem**. A function is homogeneous of degree $r$  if and only if it satisfies
	  $$
	  \sum x_i \frac{\partial f}{\partial x_i} = rf
	  $$
	  Another way to say this: *$f$ is an eigenvector of the differentiation operator along the phase velocity field of dilations $e^s$ with eigenvector $r$*. 
		* *Proof*: In the forward direction, calculate $\partial f/\partial s$ at $s=0$. 
		  
		  In the reverse direction, integrate the differential equation with separable variables defined by the Euler relation. That is, using $df/dx = rf/x$. 

	* The homogeneous function of degree $r$ is a common [[Matrix Diagonalization|eigenvector]] of all linear operators $(e^s)^\ast$ with eigenvalues $e^{rs}$. 
	* A necessary and sufficient condition for the direction field of the differential equation $\frac{dx}{dt}=F(t,x)$ to be homogeneous is 
	  $$
	  \sum x_i \frac{\partial f}{\partial x_i} = 0
	  $$ 

* The **$\sigma$-process** also called **inflating $0$** is defined by mapping
  $$
  (x,y) \mapsto
  \begin{cases}
  (x,y/x) & x \ne 0 \\
  (x/y,y) & y \ne 0
  \end{cases}
  $$
	* This allows us to turn any algebraic curve with a singularity at the origin into a curve having no singularities except ordinary self-intersections.

* A **[[Fundamental Constructs of Group Theory|group]] of quasi-homogeneous dilations** of the plane is a one-parameter group of linear transformations
  $$
  g^s (x,y) = (e^{\alpha s} x, e^{\beta s} y)
  $$
  We refer to $\alpha,\beta$ as **weights**, we denote $\alpha = \deg x$, and $\beta = \deg y$. 
* An equation is called **quasi-homogeneous** with weights $\alpha,\beta$ if in the direction field that defines it in, the plane is invariant with respect to the group of quasi-homogeneous dilations
	* (*Arnold 6.4.1*) A quasi-homogeneous equation $\frac{dy}{dx} = F(x,y)$ with weights $\deg \alpha$ and $\deg \beta$ can be reduced to an equation with separable variables by passing the coordinates 
	  $$
	  \left(x,\frac{y^\alpha}{x^\beta}\right)
	  $$
	  in the domain $x>0$
* A function $f$ is called **quasi-homogeneous** of degree $r$ if it satisfies the identity 
  $$
  f(e^{\alpha s} x, e^{\beta s} y) = e^{rs} f(x,y)
  $$
  That is $f$ is a common eigenvector of the operators $(g^s)^\ast$, where $g^s$ is a quasi-homogeneous dilation with, with eigenvalues $e^{rs}$.
	* (*Arnold 6.4.2*) A necessary and sufficient condition for the direction field of the equation 
	  $$
	  \frac{dy}{dx} = F(x,y)
	  $$
	  to be a quasi-homogeneous is that the right-hand side be quasi-homogeneous and its quasi-homogeneous degree be
	  $$
	  \deg F = \deg y - \deg x = \beta - \alpha
	  $$
	* (*Arnold 6.5.1*) Under a quasi-homogeneous dilation $(x,y)\mapsto (e^{\alpha s} x, e^{\beta s} y)$ the graph of the function $y=\varphi(x)$ transforms into the graph of the function $y=\Phi (x)$ for which
	  $$
	  \frac{d^k\Phi}{dx^k}(z_{t+1}) = e^{(\beta -k\alpha)s} \frac{d^k\varphi}{dx^k} (z_t) 
	  $$
	  Thus, $d^ky/(dx)^k$ transforms like $y/x^k$. 

* A **quasi-homogeneous vector field** is defined by the condition 
  $$
  \deg \frac{\partial}{\partial x_i} = -\deg x_i
  $$


#  Links
* [[Ordinary Differential Equations by Arnold|Arnold]]