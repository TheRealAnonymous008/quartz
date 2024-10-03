* The goal of Numerical Integral Calculus is to compute the integral of a function.
# Riemann Sum
* One approximation can be obtained  using the [[Real Analysis|Riemann Integral]].  Let $f:[a,b]\to \mathbb{R}$ be a function. Also let $P=(x_0, \dots, x_n)$ be a partition over this integral such that
  $$
  a = x_0 < x_1 < x_2 < \dots <x_n=b
  $$
  $$
  \int_a^b f(x) \ dx  \approx \sum_{i=1}^n f(x_i^\ast) \cdot h_i
  $$
  Each sample point $x_i$ can be chosen from anywhere in the interval $x_i^\ast \in [x_{i-1},x_i]$ Also we define $h_i = x_i-x_{i-1}$
	* Note that if the intervals are spaced out, we have that
	  $$
	  h = \frac{b-a}{n}
	  $$
* More sample points chosen tends to give better approximations.

* The  **Left Rule** involves choosing 
  $$
  x_i^\ast = x_{i-1}
  $$
  Then 
  $$
  \sum_{i=1}^n f(x_{i-1})  \cdot  h_i
  $$
	  
* The **Right Rule** involves choosing
  $$
  x_i^\ast= x_i
  $$
  Then
  $$
  \sum_{i=1}^n f(x_i) \cdot h_i
  $$

* Both the left and right Riemann sum have an error bound that is $O(h)$
	* *Proof*: Let $L$ and $R$ be the left and right sums respectively. Observe that
	  $$
	  |R-L| = |f(b) - f(a)| \cdot h
	  $$
	  Also note that this is an upper bound for both the left and the right sums. In particular, one sum will overestimate and one will underestimate so that if the true integral is $I$, we have without loss of generality
	  
	  $$
	  L\le I \le R
	  $$
	  So that both $|I-L|\le |R-L|$ and $|I-R|\le |R-L|$. 
	  
	  Therefore the error for both is $O(h)$.
	* *Proof*: An alternate proof obtains the precise bound. Let $M$ be the maximum of the first derivative in the interval.  Assume $f$ is continuous and $f'$ well defined over the interval.
	  
	  We proceed for the left Riemann sum but the proof is the same for the right.
	  $$
	  \begin{split}
	  \int_{x_i}^{x_{i+1}} f(x)\ dx - f(x_i) &= \int_{x_i}^{x_{i+1}}(f(x) - f(x_i)) \ dx \\
	  &= \int_{x_i}^{x_{i+1}} \left(f(x_i ) +f'(\xi _i) (x-x_i) \right) \\
	  &= f'(\xi_i)\int_{x_i}^{x_{i+1}} (x-x_i) \\
	  &= \frac{f'(\xi _i) h^2}{2}
	  \end{split}$$
	  In the above, $\xi_i$ is the value such that $f(\xi_i)$ is the average value of $f$ in the interval $[x_i,x_{i+1}]$. We can take sums of the above to get the following
	  
	  $$
	  \sum_{i=1}^n \frac{f'(\xi_i) h^2}{2}=\frac{h(b-a)}{2}\left(\frac{1}{n}\sum_{i=1}^n f'(\xi_i)\right) \le \frac{Mh(b-a)}{2}
	  $$


* The **Midpoint Rule** involves choosing
  $$
  x_i^\ast = \frac{x_i + x_{i-1}}{2}
  $$
  Then
  $$
  \sum_{i=1}^n f\left(\frac{x_{i}+x_{i-1}}{2}\right) \cdot h_i
  $$
	* Suppose $f$ is continuous over $[a,b]$ and the second derivative  is $f''(x)$ with maximum absolute value $M$. Then the midpoint rule has an error bound that is $O(h^2)$. 
		* *Proof*: To be more precise, the error $\epsilon$ is bounded by
		  $$
		  \epsilon \le \frac{M(b-a)^2}{24}h^2
		  $$
		  
		  Let $c_i=x_i^\ast$. 
		  If we start with a single interval and use the Taylor Series expansion
		  $$
		  \begin{split}
		  \int_{x_i}^{x_{i+1}} f(x)\ dx - f(c_i) &= \int_{x_i}^{x_{i+1}}(f(x) - f(c_i)) \ dx \\
		  &= \int_{x_i}^{x_{i+1}}\left(f(c_i) + f'(c_i) (x-c_i) + f''(\xi_i) \frac{(x-c_i)^2}{2!} - f(c_i)\right) \ dx \\
		  &= \frac{f''(\xi_i)}{2} \int_{x_i}^{x_{i+1}} (x-c_i)^3 \ dx \\ 
		  &=\frac{f''(\xi_i)  h^2}{24}
		  \end{split}
		  $$
		  In the above, $\xi_i$ is the point such that by the [[Real Analysis|Mean Value Theorem]], $f''(\xi_i)$ is the average of all $f''$ in the interval. 
		  
		  The proof follows by taking the sum of the above over all intervals. The bound is obtained by considering the maximum absolute value of $f''(x)$ over the interval.  In particular
		  $$
		  \sum_{i=1}^n \frac{f''(\xi_i) h^3}{24} = \frac{h^2(b-a)}{24}\left(\frac 1 n \sum_{i=1}^n f''(\xi_i)\right) \le M \cdot \frac{h^2(b-a)}{24}
		  $$



* The **Lower rule** involves choosing
  $$
  f(x_i^\ast ) = \inf f([x_{i-1}, x_i])
  $$
  Thus
  $$
  \sum_{i=1}^n  \inf f([x_{i-1}, x_i]) \cdot h_i
  $$
* The **Upper rule** involves choosing
  $$
  f(x_i^\ast ) = \sup f([x_{i-1}, x_i])
  $$
  Thus
  $$
  \sum_{i=1}^n  \sup f([x_{i-1}, x_i]) \cdot h_i
  $$

## Curve Approximation
* The **Trapezoid Rule** approximates the Riemann sum using trapezoidal cuts. In particular, we  make use of secant lines to approximate the shape of the curve. 
  
  Given interval $[x_{i-1},x_i]$, the area of the trapezoid in the region is defined as 
  $$
  A_i =\frac{1}{2}(f(x_i) + f(x_{i-1})) \cdot h_i 
  $$
  And the integral is approximated as
  $$
  \sum_{i=1}^n A_i
  $$
	* Suppose $f$ is continuous over $[a,b]$ and the second derivative  is $f''(x)$ with maximum absolute value $M$. Then the trapezoid rule has an error bound that is $O(h^2)$. 
		* *Proof* The proof proceeds similarly to the proof in the Midpoint Rule. We can use the same proof sketch to show that the Midpoint rule has error bound 
		  $$
		  \epsilon \le \frac{M(b-a)^2}{12}h^2
		  $$
		  Where $M$ is the maximum absolute value of $f''(x)$. 

* **Simpson's Rule** uses quadratic approximations of the curve to obtain the integral. It is like the Trapezoidal rule but using tangent quadratic curves rather than tangent lines. It also uses three points for the approximation
  
  Given interval $[x_{i-1},x_i]$, the area of the trapezoid in the region is defined as 
  $$
  A_i =\frac{1}{6}\left[f(x_i) + 4f\left(\frac{x_i + x_{i-1}}{2}\right) + f(x_{i-1})\right] 
  $$
  The integral is then approximated as 
  $$
  \sum_{i=1}^n A_i
  $$
	* Simpson's Rule gives a fourth order approximation. That is, the error bound is $O(h^4)$. 
		* *Proof*: We prove a related result. Simpson's rule is found by taking the weighted average of the Midpoint Rule approximation and the Trapezoid Rule Approximation. Denote these by $M$ and $T$ respectively. Then the Simpson Rule approximation is given by
		  $$
		  \frac{2M+T}{3}
		  $$
		  Expanding this weighted average gives us the desired fourth order approximation term. 
# Links
* [[Numerical Methods -- An Inquiry Based Approach with Python by Sullivan]]
* [[Integral Calculus]]