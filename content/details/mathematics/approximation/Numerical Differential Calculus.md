# Finite Difference Methods
* The key idea for approximating the derivative using **Finite Difference Methods** is as follows:
	* Split the domain into sub-intervals.
	* Define the distance between two points in the partition as $h$.
	* Approximate the derivative at $x$ in the domain as a [[Linear Combination|linear combination]] of $f(x-h)$, $f(x)$, $f(x+h)$ and other points in the partition.
## First Derivatives
* A simple approximation to the derivative of a function can  be made as follows
  $$
  f'(x) \approx \frac{f(x+h) - f(x)}{h }
  $$
  For sufficiently small $h$.
	* The above is a linear approximation of the derivative .
	* Note that this approximation fails when the error terms (as seen in the [[Taylor Series|Taylor Series]])  are non-negligible. 
	* (*Sullivan 3.1*) The approximation above is a first order approximation. That is 
	  $$
	  f'(x) = \frac{f(x+h) - f(x)}{h} + O(h)
	  $$

* We can get a second order approximation as follows using the Taylor Series.
  
  Note that 
  $$
  \begin{split}
  f(x+h) &= \sum_{n=0}^\infty \frac{f^{(n)}(x)}{n!} h^n \\
  f(x-h) &= \sum_{n=0}^\infty (-1)^n \frac{f^{(n)}(x)}{n!}h^n
  \end{split}
  $$
  Observe that 
  $$
  f(x+h) -f(x-h) =\sum_{n=0}^\infty\frac{f^{(2n + 1)}(x)}{(2n + 1)!} 2h^{2n + 1}
  $$
  And we can verify that
  $$
  f'(x)= \frac{f(x+h) - f(x+h)}{2h} + O(h^2)
  $$
  So 
  $$
  f'(x) \approx \frac{f(x+ h) - f(x+h)}{2h}
  $$

## Second Derivatives
* We can obtain approximations for the second derivative using the first degree approximations. In particular, it can be shown that the following three hold (respectively called, central, forward and backward difference approximations)
  $$
  \begin{split}
  f''(x) &= \frac{f(x+h) - 2f(x) + f(x-h)}{h^2} + O(h^2) \\
  &= \frac{f(x+2h) -2f(x+h) + f(x)}{h^2} + O(h) \\
  &= \frac{f(x) - 2f(x-h) + f(x - h)}{h} + O(h)
  \end{split}
  $$

## Higher Order Derivatives
* We can, in general, obtain approximations for higher order derivatives as follows.
* The  **forward approximation** for the $n$-th order derivative is given by
  $$
  f^{(n)}(x) = \sum_{i=0}^{n} (-1)^{n-i}{n\choose i} f(x+ ih) + O(h) 
  $$
* The **backward approximation** is given by
  $$
  f^{(n)}(x) = \sum_{i=0}^n (-1)^i {n\choose i} f(x-ih) + O(h)
  $$
* The **central approximation** is given by
  $$
  f^{(n)}(x) = \sum_{i=0}^n (-1)^i {n\choose i } f\left(x +  \left(\frac n 2 - i\right)h\right)+ O(h^2) 
  $$


# Links
* [[Numerical Methods -- An Inquiry Based Approach with Python by Sullivan]]
* [Finite Difference Formulas by MathLibreText](https://math.libretexts.org/Bookshelves/Scientific_Computing_Simulations_and_Modeling/Scientific_Computing_(Chasnov)/I%3A_Numerical_Methods/6%3A_Finite_Difference_Approximation)
* [[Differential Calculus]]