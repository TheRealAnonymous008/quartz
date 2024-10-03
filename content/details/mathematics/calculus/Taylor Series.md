* The **Taylor Series**  is defined as
  $$
  f(x) = \sum_{n=0}^\infty \frac{f^{(n)}(a)}{n!} (x-a)^n
  $$
  Where $f^{(n)}$ is the $n$-th [[Differential Calculus|derivative]] of $f$ and $f^{(0)}= f$. 

* When $a=0$ in the above, we call it a **Maclaurin Series**. 
* Partial sums are called **Taylor Polynomials**. This gives a $k$-th order approximation. Typically, we then have, assuming Taylor polynomial $T(x)$ 
  $$
  f(x) \approx T(x) 
  $$
  To be more precise
  $$
  f(x) = T(x) + \epsilon
  $$
  Where $\epsilon$ is the error term obtained from the rest of the sequence. 
  
  We denote the order with [[Asymptotic Analysis|Big Oh Notattion]]
  $$
  f(x) \approx c + O(x^k)
  $$
  Where $c$ is the constant, and $k$ is the order of the approximation. 

* Every Taylor Series has a **domain of convergence** within which it gives good approximations. 
# Common Maclaurin Series
* The Exponential Function
  $$
  e^x = \sum_{n=0}^\infty \frac{x^n}{n!}= 1 + x+\frac{x^2}{2!} + \frac{x^3}{3!} + \cdots
  $$
* The Natural Logarithm (first equation) and the **Mercator Series** (second equation)
  $$
  \begin{split}
  \ln(1-x) &= -\sum_{n=1}^\infty \frac{x^n}{n!} &= -x-\frac{x^2}{2} - \frac{x^3}{3}\cdots \\
  \ln(1+ x) &= \sum_{n=1}^\infty (-1)^{n+1}\frac{x^n}{n} &= x-\frac{x^2}{2} +\frac{x^3}{3}-\cdots
  \end{split}
  $$

* The geometric series
  $$
  \frac{1}{1-x} = \sum_{n=0}^\infty x^n
  $$
* The binomial series
  $$
  (1+x)^\alpha =\sum_{n=0}^\infty {{\alpha}\choose{n}}x^n 
  $$
  Where
  $$
  {\alpha\choose n} = \prod_{k=1}^n \frac{\alpha-k+1}{k} = \frac{\alpha(\alpha-1)\cdots(\alpha-n+1)}{n!}
  $$
  If we want $g(x)=x^\alpha$ we can use the above as 
  $$
  g(x)= g(x_0)\cdot g\left(1+\frac{x-x_0}{x_0}\right)
  $$

* The square root and its inverse 
  $$
  \begin{split}
  (1+x)^{\frac 1 2} &= 1 + \frac{1}{2} x  - \frac{1}{8}x^2 + \frac{1}{16}x^3 - \frac{5}{128}x^4 + \frac{7}{256}x^5-\cdots &= \sum_{n=0}^\infty \frac{(-1)^{n-1} (2n)!}{4^n (n!)^2 (2n-1)}x^n \\ 
  
  (1-x)^{\frac 1 2} &= 1 - \frac{1}{2} x  + \frac{3}{8}x^2 - \frac{5}{16}x^3 + \frac{35}{128}x^4 - \frac{63}{256}x^5-\cdots &= \sum_{n=0}^\infty \frac{(-1)^{n} (2n)!}{4^n (n!)^2}x^n \\ 
  \end{split}
  $$

* The Sine and Cosine functions
  $$
  \begin{split}
  \sin x &= \sum_{n=0}^\infty \frac{(-1)^n}{(2n+1)!}x^{2n+1} &= x-\frac{x^3}{3!} + \frac{x^5}{5!}-\cdots \\
  
  \cos x &= \sum_{n=0}^\infty \frac{(-1)^n}{(2n)!} x^{2n} &= 1-\frac{x^2}{2!} + \frac{x^4}{4!} - \cdots
  \end{split}
  $$

* The Inverse Sine and Cosine functions for $|x|\le 1$
  $$
  \begin{split}
  \arcsin x &= \sum_{n=0}^\infty \frac{(2n)!}{4^n (n!)^2 (2n+1)}x^{2n+1} &= x+\frac{x^3}{6} +\frac{3x^5}{40} + \cdots \\
  \arccos x &= \frac \pi 2 - \arcsin x &= \frac \pi 2 -x-\frac{x^3}{6} -\frac{3x^5}{40} -\cdots
  \end{split}
  $$
* The inverse tangent function for $|x|\le 1$
  $$
  \arctan x = \sum_{n=0}^\infty \frac{(-1)^n}{2n+1}x^{2n+1} = x-\frac{x^3}{3} + \frac{x^5}{5}-\cdots
  $$

* The hyperbolic sine and cosine
  $$
  \begin{split}
  \sinh x &= \sum_{n=0}^\infty \frac{x^{2n+1}}{(2n+1)!} &= x + \frac{x^3}{3!} + \frac{x^5}{5!} + \cdots  \\
  \cosh x &= \sum_{n=0}^\infty \frac{x^{2n}}{(2n)!} &= 1+\frac{x^2}{2!} + \frac{x^4}{4!} + \cdots \\
  \end{split}
  $$
* The inverse hyperbolic functions for $|x|\le 1$
  $$
  \begin{split}
  \text{arcsinh} \ x &= \sum_{n=0}^\infty \frac{(-1)^n (2n)!}{4^n (n!)^2(2n+1)}x^{2n+1} &= x-\frac{x^3}{6} + \frac{3x^5}{40} -\cdots \\
  
  \text{arctanh} \ x&= \sum_{n=0}^\infty \frac{x^{2n+1}}{2n+1} &= x+\frac{x^3}{3}+\frac{x^5}{5} + \cdots 
  \end{split}
  $$

# Links
* [Active Calculus -- Taylor Series](https://activecalculus.org/single/sec-8-5-taylor.html)