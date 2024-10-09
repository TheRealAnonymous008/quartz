* Consider the problem of optimizing the function $f(x)$. Our general pipeline from [[Differential Calculus|Calculus]] is to compute for $x$ in our domain of interest such that 
  $$
  f'(x) = 0
  $$

# Approaches
* **Derivative Free Optimization** [^dfo] involves the following steps
	* Pick a starting point $x_0$ and find the value $f(x_0)$.
	* Pick a small step size $\Delta x$.
	* Calculate the objective function at $x+\Delta x$ and $x-\Delta x$. Pick the appropriate point for the next step.
	* Iterate until convergence or termination

[^dfo]: This is essentially a [[Greedy Algorithm|Greedy Algorithm]]. 

* **Gradient Descent / Ascent** is defined as follows
	* Compute the derivative of the function $f'(x)$
	* Pick starting point $x_0$ and control parameter $\alpha$. 
	* Use the rule
	  $$
	  x_{n+1} \gets x_n + \alpha f'(x_n)
	  $$
	  For maximization and
	  $$
	  x_{n+1} \gets x_n - \alpha f'(x_n)
	  $$
	  For minimization
	* Iterate until convergence or termination

* *Gradient Descent involves moving uphill / downhill along the direction of steepest descent.
* For the case of multidimensional data, we replace the update rule of gradient descent as
  $$
  x_{n+1} ]\gets x_n + \alpha \nabla f(x_n)
  $$

* **Monte Carlo Search** involves the following
	* Pick a sample of $N$ points or values.
	* Compute the value of the objective function at each sample point.
	* Keep the $x$ value with the largest or smallest value of the objective function.
	* Iterate as needed. Make sure to compare the value at each iteration.

* **Optimization using [[Root Finding Algorithms|Root Finding]]**
	* Compute $f'(x)$
	* Set the derivative to $0$ and solve using a root finding method.
	* Determine if the critical point or one of the endpoints is the extrema of interest

## Considerations
* The main pitfall is in local extrema where methods get stuck on. 
* Each method has its pros and cons.
	* *Derivative Free Optimization* does not require computing a derivative (which may not exist or be computationally expensive) but it converges slower since it has to check all neighbors without considering something like the gradient to guide search. 
	* *Gradient Descent* tends to be fast since it moves in the direction of steepest ascent / descent.  However, it requires the computation of derivatives and a good choice for starting point and $\alpha$.
	* *Monte Carlo Search* is better suited for noisy objective functions, higher dimensional data, and large sample spaces . It does not require computing derivatives  but it tends to be slower and more computationally expensive
	* *Root Finding* has a good convergence rate near the optimum. However, it requires knowing the derivative of $f$ and an appropriate choice of starting value.
# Links
* [[Numerical Methods -- An Inquiry Based Approach with Python by Sullivan]]
* [[Numerical Differential Calculus]]