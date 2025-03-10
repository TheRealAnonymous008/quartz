* (*2011 Philippine Math Olympiad* ) Find all $f:\mathbb{R}\to\mathbb{R}$ such that $\forall x\in \mathbb{R}$
  
  $$
  f(f(x)) + xf(x) = 1
  $$
	* *Solution*: 
	  Consider $x=0$, 
	  $$
	  f(f(0)=1
	  $$
	  Next, consider $x=f(0)$ to get 
	  $$
	  \begin{split}
	  f(f(f(0)))+ f(0) f(f(0)) &= 1 \\
	  f(1) + f(0) &= 1  
	  \end{split}
	  $$
	  Next consider $x=1$ 
	  $$
	  f(f(1)) + f(1) = 1
	  $$
	  Combining with the above, we get $f(f(1))=f(0)$
	  Finally $x=f(1)$ to get
	  $$
	  \begin{split} 
	  f(f(f(1))) + f(1)f(f(1)) &= 1 \\
	  1 + f(1) f(0) &= 1\\
	  f(0) f(1) &= 0
	  \end{split}
	  $$
	* *Solution*: Now either $f(0)=0$ or $f(1)=0$.
	  
	  If $f(0)=0$ then $f(1)=1$ and $f(f(1))=0$ and $f(1)=0$ which is a contradiction
	  
	  If $f(1)=0$ then $f(0)= 1$ and $f(f(0))=f(1)=0$ which is a contradiction
	* *Answer*: No such function exists

* [See here](https://www.youtube.com/watch?v=oNT4iwU6Pew) Find function(s) $f$ such that 
  $$
  f(x) + f\left(\frac{1}{1-x}\right) = x
  $$
	* *Solution*
	  Let $g(x)=\frac{1}{1-x}$ Then $g(g(x))=\frac{1}{1-\frac{1}{1-x}}= \frac{x-1}{x}$.  
	  Then $g(g(g(x)))=\frac{1}{1-\frac{x-1}{x}}=x$.  
	  
	  Using $x=\frac{1}{1-x}$.  
	  $$
	  f\left(\frac{1}{1-x}\right) + f\left(\frac{x-1}{x}\right) = \frac{1}{1-x}
	  $$
	  Using it again gives
	  $$
	  f\left(\frac{x-1}{x}\right) +f(x) = \frac{x-1}{x}
	  $$
	  Combine this with the original equation
	  $$
	  f(x) + f\left(\frac{1}{1-x}\right) = x
	  $$
	  $$
	  \begin{split}
	  2f(x) + f\left(\frac{1}{1-x}\right) + f\left(\frac{x-1}{x}\right) &= x + \frac{x-1}{x} \\
	  2f(x) + \frac{1}{1-x} &= \frac{x^2 + x-1}{x} \\
	  f(x) &= \frac{x^3-x+1}{2x(x-1)}
	  \end{split}
	  $$
	* *Solution*: Another solution is to consider $x=0$ and $x=1$. If $x=0$, then 
	  $$
	  f(0) + f(1) = 0
	  $$
	  So that $f(0)=-f(1)$. Choose any $c\in\mathbb{R}$ such that $f(0)=c$  and $f(1)=-c$ . 