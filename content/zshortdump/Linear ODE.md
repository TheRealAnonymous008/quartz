* A **first order homogeneous linear equation** is an equation of the form
  $$
  \frac{dx}{dt} = f(t) \cdot x
  $$
  This is a special case of an equation with [[Integral Curve|separable variables]]. 

* (*Arnold 3.1.1*) Every solution to a first order homogeneous linear equation can be extended to the entire interval on which $f$ is defined. The solution with initial conditions $(t_0, x_0)$ is given as 
  $$
  x=x_0e^{\int_{x_0}^x f(\xi) d\xi}
  $$
* The set of all solutions to a first order homogeneous linear equation form a [[Vector Space|vector space]]. 

* *Homogeneous Linear Equations approximate any ODE by virtue of [[Real Analysis|smooth functions being locally linear]]*. 
* Integral curves map into one another under the action of dilation along the $x$-axis in the extended phase space. 


* A first order homogeneous linear equation with $T$-**periodic** coefficient is defined as an equation of the form
  $$
  \frac{dx}{dt} = f(t) \cdot x 
  $$
  Where
  $$
  f(t + T) \cong f(t) 
  $$
	* We can define a **monodromy** -- a mapping $A:\mathbb{R}\to\mathbb{R}$ such that we map the value $\varphi(0)$ to the value $\varphi(T)$ of the same solution.
	* (*Arnold 3.2.1*) The monodromy operator is linear and is actually multiplication by a number $\lambda$. The behavior of solutions is determined by $\lambda$
	  
	  $$
	  \begin{cases}
	  \lambda > 1 & \text{ solution tends to } \infty \text{ as } x\to \infty \\
	  \lambda = 1 & \text{ solution is bounded} \\
	  \lambda < 1 & \text{ solution tends to } 0 \text{ as } x \to \infty
	  \end{cases}
	  $$

# Links
* [[Ordinary Differential Equations by Arnold]]