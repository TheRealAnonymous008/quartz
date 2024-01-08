* In learning Mathematics, prioritize understanding the definitions first using examples if needed. Then, understand what the theorems are saying. Finally, understand the proofs on why a theorem should be true (analogous to the [[Reading#Three Pass Approach|three pass approach]])
# Topics
* [[Calculus]]
* [[Game Theory]]
* [[Graph Theory]]
* [[Group Theory]]
* [[Information Theory]]
* [[Linear Algebra]]
* [[Real Analysis]]
* [[Probability and Statistics]]
# Unfiled Math Objects
* [The Ansatz Technique](https://en.wikipedia.org/wiki/Ansatz) pertains to solving a problem using an educated guess or assumption  about the solution which may later be verified to be part of the solution.

* A quaternion $w+xi+yj+zk$ can be represented as the rotation corresponding to 
  $$
  \cos{\left(\frac{w}{2}\right)} + \sin{\left(\frac{w}{2}\right)}(x\hat{i}+y\hat{j}+z\hat{k})
  $$

* **Jensen's Inequality** states that for any convex function 
  $$
  f\left(\sum_{k=1}^n \lambda_ix_i\right)\le
  \sum_{k=1}^n\lambda_i f(x_i)
  $$
  Where $\lambda_i\ge 0$ and $\sum_{k=1}^n\lambda_i = 1$.
  
  An alternative formulation is that if we have convex function $f$ and a random variable $X$, we have 
  $$
  f(\mathbb{E}[X])\le \mathbb{E}[f(x)]
  $$
  That is, the output of the average input from $X$ is smaller than the average output from $f(X)$.

* **Brouwer's Fixed Point Theorem** - If $f(x)$ is a continuous function from the domain $[0,1]$ to itself, then there exists at least one value $x^\ast \in [0,1]$ for which $f(x^\ast)=x^\ast$. 

* **Kakutani's Fixed Point Theorem** - A correspondence $C: X\mapsto X$ has a fixed point $x\in C(x)$ if four conditions are satisfied 
	* $X$ is a non-empty, compact, and convex subset of $\mathbb{R}^n$
	* $C(x)$ is non-empty for all $x$
	* $C(x)$ is convex for all $x$
	* $C$ has a closed graph. 

# Links

* [Infinite Napkin by Evan Chen](https://venhance.github.io/napkin/Napkin.pdf) - a comprehensive explainer of high level mathematics targeted to a highschooler
* [Visualizing Quaternions (4d numbers) with stereographic projection](https://www.youtube.com/watch?v=d4EgbgTm0Bg)
* [Jensen's Inequality](https://www.youtube.com/watch?v=u0_X2hX6DWE) - more on the Jensen's Inequality

