* A **first order homogeneous linear equation** is an equation of the form
  $$
  \frac{dx}{dt} = f(t) \cdot x
  $$
  This is a special case of an equation with [[Integral Curve|separable variables]]. 

* (*Arnold 3.1.1*) Every solution to a first order homogeneous linear equation can be extended to the entire interval on which $f$ is defined. The solution with initial conditions $(t_0, x_0)$ is given as 
  $$
  x=x_0e^{\int_{t_0}^t f(\xi) d\xi}
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
  f(t + T) = f(t) 
  $$
	* We can define a **monodromy** -- a mapping $A:\mathbb{R}\to\mathbb{R}$ such that we map the value $\varphi(0)$ to the value $\varphi(T)$ of the same solution for $t=T>0$.
	* *Intuition*: We get a homogeneous linear equation with $T$-periodic coefficient when we study the case of **limit cycles**.
	  
	  The linearity comes a monodromy which "unwraps" the limit cycle and maps it onto the real number line.  Since it is cyclic it is periodic with period $T$. Movement along the limit cycle can be encapsulated using the linear ODE above, hence linearity.

	* (*Arnold 3.2.1*) The monodromy operator is linear and is actually multiplication by a number $\lambda$. The behavior of solutions is determined by $\lambda$
	  
	  $$
	  \begin{cases}
	  \lambda > 1 & \text{ solution tends to } \infty \text{ as } t\to \infty \\
	  \lambda = 1 & \text{ solution is bounded} \\
	  \lambda < 1 & \text{ solution tends to } 0 \text{ as } t \to \infty
	  \end{cases}
	  $$
	  In particular, note that for integral curve $\varphi$, we have
	  $$
	  \varphi(NT + S) = \lambda^n \varphi(S)
	  $$
	  For $N\in\mathbb{Z}$, and $S$ serving as the translation term. 
	* The multiplier term is obtained as 
	  $$
	  \ln \lambda = \int_0^T f(\xi) d\xi 
	  $$
	 * The multiplier $\lambda$ characterizes the stability of a limit cycle.
	   $$
	   \begin{cases}
	  \lambda > 1 & \text{ limit cycle is unstable. Phase curves near a cycle diverge}\\
	  \lambda = 1 & \text{ cannot be determined} \\
	  \lambda < 1 & \text{ limit cycle is stable. Phase curves near a cycle wind on the cycle}
	  \end{cases}
	   $$
	   In other words, if $\lambda = 1$, we cannot make judgments about the behavior of limit cycles
		* *Intuition*: Consider the function $\Phi$ such that $\Phi(\varphi(0)) = \varphi(T)$. When linearized, this function can be shown to be a monodromy. Intuitively, this maps one cycle (from $0$ to $T$, say) to another limit cycle. Thus, we can see how much the cycle diverges or stabilizes since $\Phi$ is a monodromy.
		  	  
![[Simple Monodrony.png]]
<figcaption> Monodromy. Image taken from Arnold </figcaption>

* A first order **Inhomogeneous Linear Equation** is of the form 
  $$
  \frac{dx}{dt} = f(t) \cdot x + g(t)
  $$
	* (*Arnold 3.3.1*) If a particular solution of an inhomogeneous equation $x=\varphi_1(t)$ is known, all other solutions have the form 
	  $$
	  x =\varphi_1(t) + \varphi_0(t) 
	  $$
	  Where $\varphi_0$ is the solution to the corresponding homogeneous equation (i.e., $g(t)= 0$).  All such solutions are of this form.
		* *Proof*: See [[Elementary Matrix Operations|Friedberg 3.9]]. Note how the solutions to the homogeneous system forms a vector space (a  null space in fact).
	* (*Arnold 3.3.2*) The solution of the inhomogeneous linear equation with initial condition $x(t_0)=0$ exists, is unique, and is given by
	  $$
	  x = \int_{t_0}^te^{\int_\xi^t f(\zeta)  \ d\zeta}g(\xi) \ d\xi
	  $$
	* *Inhomogeneity typically corresponds to some form of perturbation on the system*.

*  **Superposition Principle** If $\varphi_1$ and $\varphi_2$ are solutions of the inhomogeneous linear equations $A\varphi_1 = g_1$ and $A\varphi_2 = g_2$ then $\varphi_1 + \varphi_2$ is a solution of the equation $A\varphi = g_1 + g_2$
	* We can separate the effects of different dynamics (the $g$'s). when taking into account all possible dynamics.

* The solution of the equation
  $$
  \frac{dx}{dt} = f(t) x + \delta(t-\xi), \ \ \ \xi > 0
  $$
  Where $\delta$ is the [[Dirac Delta Function|Dirac Delta function]]. 
  
  With initial condition $x(0)=0$ is the **influence function of the perturbation** at the instant $\xi$ on the solution at instant $t$. 
  
  We also call this **Green's Function** denoted
  $$
  x = G_\xi (t) 
  $$
	* (*Arnold 3.4.1*) Green's function is given by
	  $$
	  G_\xi(t) = \begin{cases}
	  0 & \text{if } t < \xi \\
	  e^{\int_{\zeta}^t f(\zeta) \ d\zeta} & \text{if } t > \xi
	  \end{cases}
	  $$
		* For $t < \xi$, any inhomogeneity disappears. For $t>\xi$, the solution coincides with some homogeneous solution.
		* The above corresponds to the solution to a homogeneous equation with initial condition $x(\xi)= 1$. 
	* (*Arnold 3.4.2*) The solution of the inhomogeneous equation with inhomogeneity $g$ and with zero initial condition is expressed in terms of the influence function by the formula
	  $$
	  x(t) = \int_0^t G_\xi (t) g(\xi) \ d\xi
	  $$
	  For $t>0$.

* (*Arnold 3.5.1*) If the solution 
  $$
  \frac{dx}{dt} = f(t) \ x + g(t) 
  $$
  With RHS of period $T$ in $x$ is such that the mean value of $f$ over a period is nonzero, then the equation has a solution of period $T$, and exactly one solution.
  
  The solution is stable if the average value is negative
  It is unstable if it is positive. 
	* Such a solution is inhomogeneous and of the form
	  $$
	  \varphi(t) = \lambda \varphi(0) + C
	  $$
	  Where $\lambda$ is the monodromy multiplier.
	* If $\lambda < 1$ then *after a transitory process, the system has an oscillatory behavior*. The oscillations are maintained by the perturbations to the system (i.e., inhomogeneity $g$). 


# Links
* [[Ordinary Differential Equations by Arnold]]