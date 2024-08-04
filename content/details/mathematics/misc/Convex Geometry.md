* **Jensen's Inequality** states that for any convex function 
  $$
  f\left(\sum_{k=1}^n \lambda_ix_i\right)\le
  \sum_{k=1}^n\lambda_i f(x_i)
  $$
  Where $\lambda_i\ge 0$ and $\sum_{k=1}^n\lambda_i = 1$.
  
  An alternative formulation is that if we have convex function $f$ and a [[Random Variables and Probability Distributions|random variable]] $X$, we have 
  $$
  f(\mathbb{E}[X])\le \mathbb{E}[f(x)]
  $$
  That is, the output of the average input from $X$ is smaller than the average output from $f(X)$.