* When we are only concerned with the order of growth of a [[Relation#Functions|funnction]] at large input, we are studying the **asymptotic efficiency**.  [^asymptotic_1] [^asymptotic_2] [^asymptoic_3]
* For a given function $g(n)$, the **asymptotic tight bound** denoted $\Theta(g(n))$  is defined as
  
  $$
  \Theta(g(n)) = \{f(n) \mid \exists c_1, c_2, n_0 \ \text{ such that} \ \ \ \ \  0 \le c_1\ g(n) \le f(n) \le c_2 \ g(n)  \ \ \forall n\ge n_0\}
  $$

* For a given function $g(n)$, the **asymptotic upper bound** denoted $O(g(n))$ is defined as 
  
  $$
  O(g(n)) = \{f(n) \mid \exists c n_0 \ \text{ such that} \ \ \ \ \  0 \le f(n) \le c \ g(n)  \ \ \forall n\ge n_0\}
  $$
* For a given function $g(n)$, the **asymptotic lower bound** denoted $\Omega(g(n))$  is defined as
  
  $$
  \Omega(g(n)) = \{f(n) \mid \exists c, n_0 \ \text{ such that} \ \ \ \ \  0 \le c\ g(n) \le f(n)  \ \ \forall n\ge n_0\}
  $$

* For a given function $g(n)$, the **strict asymptotic upper bound** denoted $o(g(n))$ is defined as 
  
  $$
  o(g(n)) = \{f(n) \mid \exists c n_0 \ \text{ such that} \ \ \ \ \  0 \le f(n) < c \ g(n)  \ \ \forall n\ge n_0\}
  $$
  Here $f(n)$ becomes infinitesimally small relative to $g(n)$ as $n\to \infty$.

* For a given function $g(n)$, the **strict asymptotic lower bound** denoted $\omega(g(n))$  is defined as
  
   $$
  \Omega(g(n)) = \{f(n) \mid \exists c, n_0 \ \text{ such that} \ \ \ \ \  0 \le c\ g(n) < f(n)  \ \ \forall n \ge n_0\}
  $$
  Here $f(n)$ becomes arbitrarily large relative to $g(n)$ as $n\to \infty$.

* An alternative definition can be formulated by considering $L = \lim_{n\to\infty} \frac{f(n)}{g(n)}$.
	* $f(n) = o(g(n)) \iff L = 0$
	* $f(n) = \omega(g(n)) \iff L = \infty$ 
	* $f(n)=O(g(n)) \iff L \ne \infty$
	* $f(n)= \Omega(g(n)) \iff L \ne 0$ 
	* $f(n) = \Theta(g(n)) \iff L\ne 0, \infty$ 

* *CLRS 3.1* For any two functions $f(n)$ and $g(n)$ we have that
  
  $$
  f(n)=\Theta(g(n)) \iff f(n) =\Omega(g(n)) \ \wedge \ f(n) = O(g(n)) 
  $$
* *The asymptotic functions above define equivalence on the space of functions*

* Some additional rules
  $$
  \begin{split}
  f=O(g) &\iff g = \Omega(f) \\ 
  f= o(g) &\iff g = \omega(f) \\ 
  f = o(g) & \implies f = O(g) \\ 
  f = \omega(g) &\implies f= \Omega(g) 
  \end{split}
  $$

![[Asymptotic Analysis.png]]
<figcaption> Asymptotic Analysis. Image taken from Cormen, Leiserson, Rivest, and Stein </figcaption>

[^asymptotic_1]: These can be used to analyze other functions as well. However, do note that we implicitly assume that for large enough $n$, the function becomes non-negative. 
[^asymptotic_2]: When we say $f(x)=O(g(x))$ we implicitly mean $f(x) \in O(g(x))$. 
[^asymptoic_3]: Another way to read the definitions is that the only way for $g$ to compare to $f$ is if it is scaled by an appropriate constant $c>0$.

# Links
* [[Introduction to Algorithms by Cormen, Leiserson, Rivest, and Stein|CLRS]]