* An **$f$-Divergence** is a function $D_f(P\|Q)$ which measures the distance between two [[Random Variables and Probability Distributions|probability distributions]] $P$ and $Q$. 


* All $f$-divergences with [[Differential Calculus|differentiable]] $f$ look like KL divergence up to second order when $q$ close to $p$. Specifically
  $$
  D_f(P_0, p_\theta) = \frac{f''(1)}{2}\theta^T F\theta + O(\theta^3)
  $$
  Where $F$ is the Fisher Information matrix for $p_\theta$ calculated at $p_\theta = p_0$.


# Specific Types
## KL-Divergence
* The **Kullback-Leibler Divergence** is defined as
  $$
  \text{KL}(p\mid\mid q)=\sum_{x}p(x)\log\frac{p(x)}{q(x)}
  $$
* It measures the coding inefficiency from using a model $q$ to compress the data, when the true distribution is $p$. 
* It also measures the dissimilarity between $p$ and $q$
* It can also be formulated as: 
  $$
  \text{KL}(p \ \| \ q)=H(p,q)-H(p)
  $$
  Formulated this way, the KL divergence is the average number of extra bits needed to encode the data due to the fact we used distribution $q$ rather than the true distribution $p$.
	* This formulation informally motivates the following inequality called **Gibb's Inequality**
	  $$
	  \text{KL}(p\mid\mid q) \ge 0, \ \ \  \ \ \text{KL}(p\mid\mid q)=0\iff p=q
	  $$
* **Schulman's Approximation** The KL-divergence can be [estimated](http://joschu.net/blog/kl-approx.html) as follows. Assume we have access to sample points $x$ but we cannot analytically compute the sum. Let $r(x)=p(x)/q(x)$. Then 
  $$
  \begin{split}
  \text{KL}(p \ \| \ q) &= \mathbb{E}_{x\sim q} \left[r(x)\log r(x) - r(x) - 1\right] \\ 
  
  \text{KL}(q \ \| \ p) &= \mathbb{E}_{x\sim q} \left[r(x) - 1 - \log r(x)\right] \\ 
  \end{split}
  $$

## JS-Divergence
* The **Jensen-Shannon Divergence** is a symmetric and smoothed version of the KL divergence defined as
  $$
  \text{JSD}(p\ \| \ q) = \frac{\text{KL} (p \ \| \ m) + \text{KL}(q \ \| \ m)}{2} 
  $$
  Where 
  $$
  m = \frac{p+q}{2}
  $$
  is a mixture distribution.

* It can also be written as follows
  $$
  \text{JSD}(p \ \| \ q)  = H(m) - \frac{H(p) + H(q)}{2}
  $$
* In the general case, we may use weighting parameters $\pi_i$ such that 
  $$
  \text{JSD}_{\pi_1,\dots,\pi_n} (p_1,\dots,p_n) = \sum_i \pi_i  \text{KL}(p_i \ \| \ m)
  $$
  where 
  $$
  m = \sum_{i=1}^n \pi_i p_i
  $$
	* Alternatively
	  $$
	  \text{JSD}_{\pi_1,\dots,\pi_n} (p_1,\dots,p_n) = H(m) - \sum_{i=1}^n \pi_i H(p_i)
	  $$

* The JSD is bounded assuming the use of base $b$ for logarithms. 
  $$
  0\le \text{JSD}(p\ \| \ q) \le \log_b(2)
  $$
  In general
  $$
  0 \le \text{JSD}_{\pi_1,\dots,\pi_n} (p_1,\dots,p_n) \le \log_b n 
  $$

