* The study of efficient data compression, and robust and reliable data transmission.
# Important Quantities
* Let $p$ be a probability distribution. The **entropy** is defined as 
  $$
  H(p)=-\sum_{j}p(j)\ \log{p(j)}
  $$
  
	* It can be interpreted as the *expected amount of surprise* that we may have about a given event. That is, it is the expected amount of information we can gain from the distribution. 
	* This also corresponds to the degree in which the distribution is Uniform.
	* This also corresponds with the amount of uncertainty that we may have about the distribution.

* Let $p$ and $q$ be probability distributions. The **cross entropy** is defined as 
  $$
  H(p,q)=-\sum_{k}p(k) \log{q(k)}
  $$
	* It is a measure of the average number of bits needed to identify an event drawn from the set if a coding scheme used for the set is optimized for an estimated probability distribution $q$ rather than the true distribution $p$.

* The **conditional entropy** is defined as 
  $$
  H(Y\mid X)=\sum_{x}p(x) \ H(Y|X=x)
  $$
  
	* It measures how much entropy $Y$ has remaining given we have learnt the value of $X$.


* The **Pointwise Mutual Information** between two events $x$ and $y$ is defined as 
  $$
  \text{PMI}(x,y)=\log\frac{p(x,y)}{p(x) \ p(y)}=\log \frac{p(x\mid y)}{p(x)}=\log \frac{p(y\mid x )}{p(y)}
  $$
  
	* It measures the discrepancy between these occurring together compared to what would be expected by chance.
	* It is also the amount we learn from updating a [[Bayesian Statistics|prior]] into a posterior.

# Topics
* [[F Divergence]] 
* [[Mutual Information]]

# Miscellaneous
* The **Kozachenko-Leonenko Estimate*** [^kozachenko] for Entropy works as follows. Let $X$ be a continuous random variable with values in some metric space and $\mu(x)$ be the density. The entropy is defined as  
  $$
  H(X) = -\int \mu(x) \log\mu(x) \ dx
  $$
  And estimated using the digamma function $\psi(x)$. Let $\epsilon(i)$ be twice the distance from $x_i$ to its $k$-th nearest neighbor.
  
  Then
  $$
  H(X)\approx -\psi(k) + \psi(N) + \log c_d + \frac{d}{N}\sum_{i=1}^N \log \epsilon(i)
  $$
  Where $d$ is the dimension of $x$ and $c_d$ is the volume of the $d$-dimensional unit ball. 
	* The idea is to estimate $\log \mu(x)$using the probability distribution $P_k(\epsilon)$ between $x_i$ and its $k$-th nearest neighbor -- specifically, $P_k(\epsilon)d\epsilon$, is the probability that a point is within $r\in [\epsilon/2, \epsilon/2 + d\epsilon/2]$ from $x_i$, that there are $k-1$ other points at smaller distances, and $N-k-1$ points at larger distances. 
	  
	  Let $p_i$ be the mass of the $\epsilon$-ball centered at $x_i$.  
	  
	  It can be shown that 
	  $$
	  \mathbb{E}[\log p_i] = \psi(k)-\psi(N)
	  $$
	  If we assume that $\mu(x)$ is constant in the entire $\epsilon$-ball, we have
	  $$
	  p_i(\epsilon) \approx c_d\epsilon^d \mu(x_i)
	  $$
	  And
	  $$
	  \log(\mu(x_i)) \approx \psi(k) - \psi(N) - d\mathbb{E} (\log\epsilon) - \log c_d
	  $$
	* For maximum norm, set $c_d=1$
	* For Euclidean norm, set $c_d=\frac{2^d \pi^{d/2}}{\Gamma(1+d/2)}$
	* The estimator is unbiased if $\mu(x)$ is strictly constant. 
  
[^kozachenko]::  A specification is given in  [Kraskov, Stoegbauer, and Grassberger (2003) Estimating Mutual Information](https://arxiv.org/abs/cond-mat/0305641). The original paper is in Russian. 

# Links
* [[Probability Theory]] - more on probability which is the basis of Information Theory.
* [[Machine Learning - A Probabilistic Perspective by Murphy|Murphy Ch. 2.8]]