* An **integral curve** is a line that, at each point, is tangent to a [[Vector Field|vector field]] $F$
* The problem of finding an integral curve can be viewed as a problem of [[Integral Calculus|integrating]] a given continuous function
	* *Intuition*: The integral curve of a vector field in $\mathbb{R}$ is a graph in $\mathbb{R}^2$. Each point in $\mathbb{R}$ has an associated slope, i.e., an associated derivative. The fundamental theorem of calculus then suggests we can find the integral curve via integration
* A necessary and sufficient condition for the graph of function $\varphi$ to be an integral curve is that the following relation hold for interval $I$ 
  $$
  \frac{d\varphi}{dt} = F(t,\varphi (t))
  $$
  The integral line lies in the direct product of the time axis and phase space (called the **extended phase space**)
	* *Integral Curves are solutions to an ODE*. 
	* In fact *Every first order ODE determines a direction field  on the plane*. At $(t,x)$, the slope is $F(t,\varphi(t))$. 
	* **Singular points** also called **Equilibrium points** correspond to points where $F$ vanishes. That is, when
	  $$
	  \frac{d}{dt} \Big | _{t=0}  \varphi(t) =  F(x_0) = 0
	  $$
	  At such points, we have constant functions of the form $\varphi(t)=a$ as solutions. 


* (*Arnold 2.1.1*)  Consider a differential equation of the form
  $$
  \dot x(t) = F(x(t)) 
  $$
  Where $F$ is a [[Real Analysis|smooth function]] defined on $U\subset \mathbb{R}$. That is $F$ is continuously differentiable.
  
  A solution $\varphi(t)$ satisfying the above satisfying the initial condition $\varphi(t_0)=x_0$ can be found as follows
  
  $$
  \begin{split}
  t-t_0 &=  \int_{x_0}^x \frac{d\xi}{F(\xi)} \ \ \ &\text{if } F(x_0) \ne 0 \\
  \varphi(t) &= x_0 \ \ \ & \text{if } F(x_0) = 0 
  \end{split}
  $$
  Note that this also gives an integral curve for $F$. The first equation is called **Barrow's Formula**
  
  Such a solution exists for all $t_0\in\mathbb{R}$ and $x_0\in U$. 
  Such a solution is also unique in the sense that any two solutions with the same condition coincide in some neighborhood to point $t_0$. 
	* *It is the smoothness of $F$ which guarantees the uniqueness of the solution*
	* *Intuition*: It is easy to show that Barrow's Formula holds. What is tricky is showing the uniqueness in the case of $x_0$ being an equilibrium point.
	  
	  Let $\varphi(t_1)$ be an equilibrium position. By definition we have that $F(\varphi(t_1)) = 0$.  
	  
	  Consider an instant $t_2$ infinitesimally close to $t_1$ such that $F(\varphi(t_2))=0$. We now consider the motion from $t_2$ to $t_1$. Observe two things:
	  
	  First, that $F$ is smooth and therefore [[Lipschitz Condition|Lipschitz continuous]] so it is bounded.
	  Second that the motion is locally linear since we assume $t_2$ to be infinitesimally close to $t_1$. 
	  
	  Now use Barrow's formula to find the time it will take to reach $\varphi(t_1)$ from a point $\varphi(t_3) \in [\varphi(t_2),\varphi(t_1)]$. This time, as it turns out, is infinite!
	  
	  In other words, *it takes an infinitely long time to reach the equilibrium position unless we start from the equilibrium position itself.*
 
* (*Arnold 2.4.1*) Let 
  $$
  \begin{split}
  \dot x_1 &= F_1 (x_1), & \ \ \ x_1\in U_1 \\ 
  \dot x_2 &= F_1 (x_2), & \ \ \ x_2\in U_2 \\ 
  \end{split}
  $$
  Be a system of ODEs. 
  
  The solution $\varphi$ of the ODE is a mapping $\varphi:I\to U$ of the form $\varphi(t) = (\varphi_1(t), \varphi_2(t))$ where $\varphi_1$ and $\varphi_2$ are solutions of each individual ODE. 
  
  That is, *if we have a system of ODEs corresponding to that of integral curves, then we can find the solution by solving each independently and concatenating the results*. 
  
  Note that this holds, *provided each of the $F_i$'s are independent of each other. That is, $F_i$ is only dependent on $x_i$*.
  
* An equation with **separable variables** is an equation of the form
  $$
  \frac{dy}{dx} = \frac{f(y)}{g(x)}
  $$
  Where $f$ and $g$ are smooth and do not vanish under the region of interest.
	* (*Arnold 2.6.1*) Consider the system
	  $$
	  \begin{split}
	  \dot x = g(x) \\ 
	  \dot y = f(y)
	  \end{split}
	  $$
	  A curve $\varphi$ is a phase curve of the above if and only if it is also the integral curves of the equation on separable variables
	  $$
	  \frac{dy}{dx} = \frac{f(y)}{g(x)}
	  $$
	* (*Arnold 2.6.2*) A solution to the above with initial conditions $(x_0, y_0)$ exists, is unique (i.e., two solutions coincide when both are defined), and is given by
	  $$
	  \int_{x_0}^x \frac{d\xi}{g(\xi)} = \int_{y_0}^y \frac{d\eta}{f(\eta)}
	  $$

