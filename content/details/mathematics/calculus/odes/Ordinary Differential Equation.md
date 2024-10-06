* An **Ordinary Differential Equation** is defined as follows
  
  Let $I\subseteq \mathbb{R}$ be an [[Real Analysis|open set]] and $x(t):I\subseteq \mathbb{R}^n$ be a continuous $n$-differentiable function. 
  
  Let $F$ be a function of independent variable $t$ and the [[Differential Calculus|derivatives]] of $x$ with respect to $t$. An ODE is an equation of the form
  $$
  F(t,x^{(0)}, \dots x^{(n-1)}) = x^{(n)}
  $$
  We call the above the **explicit form**.
  
  The **implicit form** involves simply setting the above to be equal to $0$. Thus, it is an equation of the form
  $$
  F(t,x^{(0)}, x^{(1)},\dots,x^{(n-1)}) = 0
  $$


* A differential equation is **autonomous** if it does not depend on $t$. That is, it is of the form
  $$
  F(x^{0)}, \dots,x^{(n-1)}) = 0
  $$
	* *Autonomous ODEs correspond to systems that are time independent*.
* A differential equation is **linear** if it can be written as a [[Linear Combination|Linear Combination]] of the derivatives of $t$. Thus
  $$
  0 = \sum_{i=0}^n a_i(t) x^{(i)} + r(t)
  $$
  Where $r(t)$ is called the **source term**. Note that $a_i(t)$ and $r(t)$ are [[Real Analysis|Continuous functions]] of $t$
	* A linear ODE is **homogeneous** if in the above $r(t)=0$
	* A linear ODE is **inhomogeneous** if $r(x)\ne 0$.
	* A linear ODE is **nonlinear** if the above does not hold.

* We can also have a [[Elementary Matrix Operations|System of ODEs]]. In such a case $\psi$ is a vector valued function of $x$ and its derivatives. It is of the following matrix form
  $$
  \begin{bmatrix}
  x_1^{(n)} \\
  \vdots \\ 
  x_m^{(n)}
  \end{bmatrix}
  = 
  \begin{bmatrix}
  F_1(t, x, x^{(1)},\dots,x^{(n-1)}) \\
  \vdots \\
  F_m(t, x, x^{(1)},\dots,x^{(n-1)})
  \end{bmatrix}
  $$

* A function $\varphi : I \to U$ is a **solution** of the ODE $F$ (in implicit form) if it is $n$-times differentiable on $t$ and $\forall t \in I$
  $$
  F(t, \varphi^{(1)},\dots, \varphi^{(n)}) = 0 
  $$
	* A **general solution** of an $n$-th order ODE is a solution containing $n$ arbitrary [[Integral Calculus|constants of integration]]. 
	* A **particular solution** is obtained by setting these constants to particular values. Typically, these constants are *set to satisfy initial or boundary conditions on $\varphi$.* 
	* A **singular solution** is a solution that cannot be obtained by setting definite values to constants in the general solution.
	  

# Topics
* [[ODE - Notation Guide]]
* [[Differential 1-Form]]

* [[Integral Curve|Integral Curve]]
* [[Linear ODE]]


# Links
* [[Ordinary Differential Equations by Arnold]]