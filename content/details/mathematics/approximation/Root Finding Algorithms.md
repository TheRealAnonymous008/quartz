* Every algebraic equation of the form
  $$
  l(x) = r(x)
  $$
  Can be translated to the problem of finding the zeros of a function. Namely find all $x$ such that
  $$
  f(x) = l(x) - r(x) = 0 
  $$
## Bisection Method
* One approach to root finding is the **Bisection Method**. [^bisection] Suppose the solution to $f(x)=0$ exists in the interval $[a,b]$. 
	* *Assume*: $f$ is continuous in the interval. 
	* Check if $f(a)$ and $f(b)$ have opposite signs and use the [[Real Analysis|Intermediate Value Theorem]]
		* If $\text{sign} f(a) \ne \text{sign}f(b)$, then the root is somewhere in the interval. 
		* Otherwise , the root might be in the interval, we must sample the interval until we find an interval $[a',b']$ where $\text{sign}f(a') \ne \text{sign}f(b')$ (or until we reach the maximum number of iterations).
	* With the check done, We *assume* that $\text{sign}f(a) \ne \text{sign}f(b)$.  We do the following per iteration (up until we reach the maximum iteration)
		* Calculate the midpoint $c=\frac{a+b}{2}$ 
		* If $f(c) = 0$ or if  $f(c)$ is close enough to $0$.
		* Update $c$ with the following rule
		  $$
		  \begin{cases}
		  a\gets c & \text{sign} f(c) = \text{sign}f(a) \\ 
		  b\gets c & \text{sign} f(c) = \text{sign} f(b)
		  \end{cases}
		  $$

[^bisection]: Note the similarities with this and [[Algorithms|Binary Search]]
* This method works because we cut down the interval search space while ensuring that the endpoints of the interval satisfy the Intermediate Value Theorem (i.e., they contain the root).

* The bisection method only works if $\text{sign}f(a) \ne\text{sign}f(b)$.
* The bisection method is not guaranteed to find the root of any arbitrary function. For example take any $a,b$ such that $\text{sign}f(a) =\text{sign}f(b)$ while also containing the root in the interval.

* (*Sullivan 2.2*) **Convergence Rate of the Bisection Method**. If $f(x)$ is a continuous function with a root $x^\ast$ in the interval $[a,b]$ and the bisection method is used for root finding, then:
	* The error between the actual root and the approximate root $\hat{x}$ will decrease by a factor of $2$ at every iteration. That is for $n$ iterations the approximation error turns out to be.
	  $$
	  |x^\ast - \hat x |  = \frac{|b-a|}{2^{n+1}}
	  $$
	  The convergence rate is therefore $O(\frac{1}2^n)$
	  
	  In fact, it is a first order approximation. That is. Specifically
	  $$
	  \epsilon_n = \frac{1}{2}\epsilon_{n-1}
	  $$
	* If we want the approximate root to be within tolerance $\varepsilon$, then we should do at most
	  $$
	  n = \bigg\lceil{\lg \left(\frac{|b-a|}{\varepsilon}\right) - 1}\bigg\rceil
	  $$
	  Iterations

## Regula-Falsi Method
* The **Regula Falsi Method** [^regula_false] involves trial and error. We test potential roots and then adjust the test value according to the outcome

[^regula_falsi]: Regula Falsi means False Position

* In particular, suppose we have the interval $[a,b]$.  Assume like in the [[#Bisection Method]] that $\text{sign}f(a) \ne \text{sign} f(b)$
	* Consider is the secant line passing through $(a,f(a))$ and $(b,f(b))$.  
	  $$
	  y - f(b) = \frac{f(b)-f(a)}{b-a} (x-b)
	  $$
	  Choose $c$ to be the $x$-intercept of this line calculated as 
	  $$
	  c = \frac{af(b)-bf(a)}{f(b) - f(a) }
	  $$
	* The calculation above has a computational advantage since $\text{sign} f(a)\ne \text{sign}(b)$ the numerator and denominator are effectively "additions" which do not lose significant digits unlike subtraction.
	* The algorithm proceeds like the Bisection method except with the choice of $c$ above.

* This method works for the same reasons as the Bisection Method. It is simply that we choose a better point than the middle of the interval since, if $f$ is approximately linear, the root need not be at the midpoint of this interval.
* The main pitfall of Regula Falsi is mainly that the interval being considered does not tend to zero unless the function is nearly linear at the zero. As a result, it may converge slowly or stagnate.
* *For close-to-linear functions, Regula Falsi performs faster than bisection.* In particular, it is a first order approximation method
* The number of iterations to converge is dependent on the function. As such, there is no number of iterations that guarantee convergence.

## Newton's Method
* **Newton's Method** involves using [[Differential Calculus|derivatives]] and in particular tangent lines to find the root.
* We begin with an *initial guess* for the root $x_0$. We assume the function $f$ *is differentiable*. 
* The algorithm proceeds as follows. Let $x_k$ be the approximate root at the $k$-th iteration.
	* Calculate the slope at the $k$-th guess  using $f'(x_k)$.
	* Calculate the $x$ intercept of the tangent line. This becomes $x_{k+1}$
	  $$
	  x_{k+1} \gets x_k -\frac{f(x_k)}{f'(x_k)}
	  $$

* Convergence is guaranteed as long as the initial guess is close to the zero.
* However, this method fails when:
	* $f$ is not differentiable at the interval specified (or it is not differentiable at the root itself)
	* The initial guess is too far from the actual zero. 
	* $f$ or its derivative are too computationally expensive (this is more of a concern for time complexity.)
	* $f'(x_k)$ is significantly large or small [^gradient] or equals zero.

[^gradient]: Similar to [[Pathologies of Deep Learning#Gradients and Learning Rate|Vanishing and Exploding Gradients]].

* Newton's Method is a second order approximation method.
	* *Proof*: We have the following relation between $\epsilon_n$ and $\epsilon_{n-1}$ from the formula of Newton's Method
	  $$
	  \epsilon_{n+1} =\epsilon_{n} + \frac{f(x_n)}{f'(x_n)}
	  $$
	  We use the [[Taylor Series|Taylor Series]] about the root $r$ to compute $f(x_n)$ and $f'(x_n)$. It is easy to show that this gives us
	  $$
	  \begin{split}
	  f(x_n)&= -\epsilon_nf'(r) + \frac 12 \epsilon_n^2 f''(r) +\dots \\
	  f'(x_n) &= f'(r) -\epsilon_nf''(r) + \frac{1}{2}\epsilon_n^2f'''(r) +\dots
	  \end{split}
	  $$
	  Also note that
	  $$
	  f'(x_n) = 1 - \epsilon_n \frac{f''(r)}{f'(r)} + \frac 1 2 \epsilon_n^2 \frac{f'''(r)}{f'(r)} + \dots
	  $$
	  Now substituting we get 
	  $$
	  \begin{split}
	  \epsilon_{n+1} &= \epsilon_{n}+ \frac{-\epsilon_nf'(r) + \frac 12 \epsilon_n^2 f''(r) +\dots}{1 - \epsilon_n \frac{f''(r)}{f'(r)} + \frac 1 2 \epsilon_n^2 \frac{f'''(r)}{f'(r)} + \dots} \\
	  &= \epsilon_{n}+ \left(-\epsilon_nf'(r) + \frac 12 \epsilon_n^2 f''(r) +\dots\right) \left(\frac1{1 - \epsilon_n \frac{f''(r)}{f'(r)} + \frac 1 2 \epsilon_n^2 \frac{f'''(r)}{f'(r)} + \dots}\right)
	  \end{split}
	  $$
	  Note the rightmost term is a geometric form $\frac{1}{1-x}$ which converges provided $|x|<1$. We can substitute this form to obtain the desired bounds as
	  $$
	  \epsilon_{n+1} = -\frac{1}{2}\frac{f''(r)}{f'(r)}\epsilon_n^2 
	  $$
	  Taking absolute values gives us
	  $$
	  |\epsilon_{n+1}| = \frac{1}{2}\frac{f''(r)}{f'(r)} 
	  $$  

## Secant Method
* The **Secant Method** aims to relax Newton's Method. In particular, we avoid using the derivative which could be cumbersome to compute (if not impossible).
* *Rather than use tangent lines to approximate the curve, we use secant lines (approximately tangent).*
* We assume that $f$ is *continuous*. Start with guesses $x_0, x_1$ that are near the root and $x_0$ respectively.  
	* Like the bisection method, we can apply the Intermediate Value Theorem to get a heuristic, that $\text{sign}f(x_0)\ne \text{sign}f(x_1)$. 

* We use the following approximation for the derivative
  $$
  f'(x_n)\approx \frac{f(x_n) - f(x_{n-1})}{x_n-x_{n-1}}
  $$
* We use the approximation as we would in Newton's Method
  $$
  x_{n+1} = x_n -\frac{f(x_n)(x_n-x_{n-1})}{f(x_n) - f(x_{n-1})}
  $$

* The secant method has a super-linear order of convergence. In fact the order of convergence is the golden ratio.
	* *Proof*: The proof proceeds similarly to that of Newton's Method. Let $r$ be the root. From the recurrent form of the Secant Method we can observe the following
	  $$
	  x_n-x_{n-1} = \epsilon_{n-1} - \epsilon_n
	  $$
	  And using the Taylor Series centered around the root, we can get
	  $$
	  f(x_n)-f(x_{n-1}) = (\epsilon_{n-1} -\epsilon_n) \left(f'(r) - \frac 1 2 (\epsilon_{n-1} + \epsilon_n) f''(r) + \dots\right)
	  $$
	  By substitution and using the Taylor series for the geometric sum we get
	  $$
	  \epsilon_{n+1} = -\frac{1}{2}\frac{f''(r)}{f'(r)} \epsilon_{n-1}\epsilon_n + \dots 
	  $$
	  The terms after the first term are smaller. Taking absolute values means we get the [[Recurrence Relation|recurrence relation]]
	  $$
	  |\epsilon_{n+1}| = \frac 1 2\left|\frac{f''(r)}{f'(r)}\right| |\epsilon_{n-1} | | \epsilon_n | 
	  $$
	  We can solve the above using the Ansatz method. In particular using the Ansatz $|\epsilon_{n+1}| = k|\epsilon_n|^p$.  It can be shown that this gives us 
	  $$
	  k^{p+1} |\epsilon_{n-1}|^{p^2}= \frac{k}{2}\left| \frac{f''(r)}{f'(r)}\right||\epsilon_{n-1}|^{p+1}
	  $$
	  Importantly, if we equate coefficients and powers we have the following
	  $$
	  \begin{split}
	  k^p &= \frac{1}{2}\left|\frac{f''(r)}{f'(r)}\right| \\ 
	  p^2 &= p+ 1
	  \end{split}
	  $$


# Topics
* [[Numerical Methods -- An Inquiry Based Approach with Python by Sullivan]]
* [Root Finding Order of Convergence](https://math.libretexts.org/Bookshelves/Applied_Mathematics/Numerical_Methods_(Chasnov)/02%3A_Root_Finding/2.04%3A_Order_of_Convergence) - fills in the proofs for Newton's Method and the Secant Method