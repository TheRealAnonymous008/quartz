# Notation
* We say $X$ is distributed according to distribution $P(\theta)$ with notation $X\sim P(\theta)$ 
* Alternatively, we may notate this as $P(X\mid \theta)$
# Distributions 
* The **Bernoulli** $\text{Ber}(\theta)$ denotes the probability of an experiment succeeding given $\theta$ is the probability of success.

* The **Binomial** $\text{Bin}(n,\theta)$ denotes the probability of an experiment succeeding $k$ times given $n$ trials were conducted and $\theta$ is the probability of success.

* The **Multinomial** $\text{Mul}(x \mid n,\theta)$. $x=(x_1,\dots, x_k)$ is a vector such that $x_j$ denotes the number of times the $j$-th outcome occur and $\theta_j$ denotes the probability of it occurring. The multinomial denotes the probability of $x$ being observed in $n$ trials.

* The **Categorical** $\text{Cat}(x\mid n, \theta)$ is a special case of the Multnomial where $n=1$ and $x$ is a one hot encoded vector.

* The **Poisson** $\text{Pois}(\lambda)$ is the binomial distribution but taken with a large number of trials $n$ and probability of success $\lambda/n$. It denotes the probability of $k$ successes being observed over a long period of time for very unlikely events.

* The **Empirical / Sample** Distribution is a distribution where given a set of data $\mathcal{D}=\{x_1, \dots, x_n\}$, we have the probability of each $x\in\mathcal{D}$ as being $1/n$. It denotes an associated empirical measure of sample.

* The **Geometric** $\text{Geo}(\theta)$ gives the probability that the $k$-th trial is the first success observed given the experiment succeeds with probability $\theta$

* The **Hypergeometric** $\text{Hyp}(N,K, n)$ describes the probability of $k$ successes (i.e., an object is drawn with a desired feature) in $n$ draws without replacement from a population of size $N$ with $K$ objects with that feature.

* The **Negative Hypergeometric** $\text{NegHyp}(N,K,r)$ describes the probability distribution on the number of draws needed before $r$ failures are observed (see Hypergeometric)

* The **Uniform** $U_{[a,b]}$ is a distribution where all events from $a$ to $b$ are equally likely and all other events never occur.

* The **Normal / Gaussian** $\mathcal{N}(\mu, \sigma^2)$ is a distribution following a bell curve whose mean, median and mode are $\mu$ and whose variance is $\sigma^2$. It is of the form 
  $$
  \mathcal{N}(x \mid \mu,\sigma^2)=\frac{1}{\sqrt{2\pi\sigma^2}}e^{-\frac{1}{2\sigma^2}(x-\mu)^2}
  $$
  One interpretation of the above is that it is a limiting distribution of the Binomial Distribution over many trials.

* The **Dirac Function** $\delta(x)$ is a function that is infinite at $x$ and $0$ everywhere else. It is a Gaussian with very low variance.

* The **Student $t$** is a variation of the Gaussian which is more robust to outliers (i.e., it has heavier tails). It is denoted $\mathcal{T}(\mu, \sigma^2, v)$ with mean $\mu$, variance $\sigma^2$ and degrees of freedom $v$. As $n\to \infty$, it becomes the Gaussian.

* The **Cauchy** is a variant of the Student $t$ distribution with $1$ degree of freedom. It has such heavy tails that it does not have a mean. It can be interpreted as the distribution of the quotient of two normal distributions with the same mean.

* The **Laplace** $\text{Lap}(\mu, b)$ is defined as 
  $$
  \text{Lap}(\mu,b)=\frac{1}{2b}\exp\left(-\frac{|x-\mu|}{b}\right)
  $$
  It is robust to outliers and puts more probability density at the center than the Gaussian. 

* The **Gamma** $\text{Gamma}(a,b)$ is a distribution parameterized with shape $a$ and rate $b$. It is the limiting distribution of $\mathcal{N}(ab,a^2b)$

* The **Exponential** is denoted $\text{Expon}(\lambda)$. Where $\lambda$ is the rate parameter .It describes the distribution of the times between events in a Poisson process.

* The **Erlang Distribution** is denoted $\text{Erlang}(\lambda)$ is defined as the Gamma Distribution $a\in\mathbb{Z}$. It is the distribution of the time until the $k$-th event of a Poisson Process.

* The **Chi-Squared** $\chi^2(v)$ is the distribution of the sum of $v$ squared Gaussian Random Variables 

* The **Inverse Gamma** $\text{IG}(a,b)$ is the distribution of the reciprocal of a random variable following the Gamma Function

* The **inverse chi-squared distribution** is defined as
  $$
  \chi^{-2}(\sigma^2\mid v_0, \sigma^2_0) = \text{IG}\left(\sigma^2\mid \frac{v_0}{2},\frac{v_0\sigma^2}{2}\right)
  $$
  

* The **Beta** $\text{Beta}(a,b)$ is a family of distributions of the form 
  $$
  \text{Beta}(a,b)=\frac{\Gamma(a+b)}{\Gamma(a)\Gamma(b)}x^{a-1}(1-x)^{b-1}
  $$
  Where $a$ denotes the successes, and $b$ the failures.

* The **Pareto** $\text{Pareto}(k,m)$ is used to model long tailed distributions where most items do not occur often. These distributions exhibit power laws. $m$ determines some threshold for which input $x$ is greater, but not by much (determined by $k$)

* The **Multivariate Gaussian / Multivariate Normal** is a generalization of the Gaussian over $D$ random variables. It is defined as 
  $$
  \mathcal{N}(\mu,\Sigma)=\frac{1}{(2\pi)^{D/2}|\Sigma|^{1/2}}\text{exp}\left(-\frac{1}{2}(x-\mu)^T\Sigma^{-1}(x-\mu)\right)
  $$
  
	* The expression in the exponent is the **Mahalanobis distance** between vector $x$ and mean $\mu$.
	* This means that the contours of the probability distribution lie in ellipsoids (see [[Machine Learning - A Probabilistic Perspective by Murphy|Murphy Ch. 4.1.2]]). Informally, this means the distribution involves translating by $\mu$ and rotating by $\Sigma$.
	* The eigenvalues of $\Sigma$ determine how stretched the ellipsoid contours are. The eigenvectors determine the axes of the ellipsoid.

* The **Multivariate Student $t$** is a generalization of the $t$ distribution over $D$ random variables. It is defined as 
  $$
  T(\mu,\Sigma,v)=\frac{\Gamma(v/2 + D/2)}{\Gamma(v/2)}|\pi V|^{-1/2} \times \left[1+(x-\mu)^TV^{-1}(x-\mu\right)]^{-\frac{(v+D)}{2}}
  $$
  where $\Sigma$ is the scale matrix rather than the covariance matrix and $V=v\Sigma$
  
  As with the $t$ distribution, as $v\to \infty$, the distribution tends to the Multivariate Gaussian.

* The **Dirichlet** is a generalization of the Beta Distribution. It has support over the simplex (generalization of triangular surface) given by
  $$
  S_K=\left\{x:0\le x_k \le 1, \sum_{k=1}^Kx_k=1\right\}
  $$
  
  The distribution is defined as 
  $$
  \text{Dir}(\alpha)=\frac{1}{B(\alpha)}\prod_{k=1}^Kx_k^{\alpha_k-1} \mathbb{I}(x\in S_k)
  $$
  And if $\alpha=(a_1,\dots,a_K)$, then
  $$
  B(\alpha)=\frac{\prod_{k=1}^K \Gamma(\alpha_k)}{\Gamma(\alpha_0)}
  $$
  And 
  $$
  \alpha_0=\sum_{k=1}^k\alpha_k
  $$
  $\alpha_0$ controls the strength of the distribution (i.e., how peaked it is) and $\alpha_k$ controls where the peak occurs.

* The **Wishart** is a generalization of the Gamma distribution to positive definite matrices. Its pdf is defined as 
  $$
  \begin{split}\text{Wi}(\Lambda \mid S,v)&=\frac{1}{Z_{\text{Wi}}}|\Lambda|^{(v-D-1)/2}\exp\left(-\frac{1}{2}\text{tr}(\Lambda S^{-1})\right) \\
  \\
  Z_{\text{Wi}}&= 2^{vD/2}\Gamma_D(v/2)|S|^{v/2} \\ 
  \Gamma_D(x) &= \pi^{D(D-1)/4}\prod_{i=1}^D\Gamma(x+(1-i)/2)
  \end{split}
  $$
  Where $Z_{\text{Wi}}$ is simply a normalization constant.

* The **Inverse Wishart** is the generalization of the inverse gamma. It is defined for $v>D-1$ and positive definite $S$ 
  $$
  \begin{split}\text{IW}(\Sigma \mid S,v)&=\frac{1}{Z_{\text{Wi}}}|\Sigma|^{(v+D+1)/2}\exp\left(-\frac{1}{2}\text{tr}(S^{-1}\Sigma^{-1})\right) \\
  \\
  Z_{\text{IW}}&= |S|^{-v/2}2^{vD/2}\Gamma_D(v/2)
  \end{split}
  $$
  
* The **Normal Inverse Wishart** is of the following form 
  $$
  \text{NIW}(\mu,\Sigma\mid m_0,\kappa_0,v_0,S_0)=\mathcal{N}\left(\mu\mid m_0,\frac{1}{\kappa_0}\Sigma\right)\times\text{IW}(\Sigma\mid S_0, v_0)
  $$
  Where
	* $m_0$ is the prior mean for $\mu$
	* $\kappa_0$ is the belief in $m_0$.
	* $S_0$ is proportional for the prior mean for $\Sigma$
	* $v_0$ is the belief in $S_0$

* The **Normal Inverse Chi-Squared** is defined as
  $$
  \text{NI}\chi^2(\mu,\sigma^2\mid m_0,\kappa_0,v_0,\sigma_0^2)=\mathcal{N}\left(\mu\mid m_0,\frac{\sigma^2}{\kappa_0}\right) \times \chi^{-2}(\sigma^2\mid v_0, \sigma_0^2)
  $$
  Where
	* $m_0$ is the prior mean for $\mu$
	* $\kappa_0$ is the belief in $m_0$.
	* $\sigma_0$ is proportional for the prior mean for $\sigma$
	* $v_0$ is the belief in $\sigma_0$

* The **Inverse Gaussian** (or **Wald**) is given by
  $$
  \text{IG}(x\mid \mu,\lambda)= \sqrt{\frac{\lambda}{2\pi x^3}} \exp\left(-\frac{\lambda(x-\mu)^2}{2\mu^2x}\right)
  $$
  Where 
	* $\mu>0$ is the mean
	* $\lambda>0$ is the shape parameter
	* Input $x>0$.
	If the Gaussian describes Brownian motion at fixed time, the Inverse Gaussian describes the time it takes for a Brownian motion to reach a level.

* The **Normal Inverse Gaussian** is defined as
  $$
  \text{NIG}(w,\sigma^2\mid w_0,V_0, a_0,b_0) = \mathcal{N}(w\mid w_0,\sigma^2V_0) \ \text{IG}(\sigma^2\mid a_0,b_0)
  $$
  Where 
	* $w_0$ is the mean of the Normal distribution
	* $V_0$ is a scaling factor to the variance of the Normal Distribution
	* $a_0$ is the mean of the Wald distribution
	* $b_0$ is the shape parameter of the Wald distribution.
# Links
* [Univariate Distribution Relationships](http://www.math.wm.edu/~leemis/chart/UDR/UDR.html) - a graph that shows probability distributions, and how and why they are related to each other.
* [[Machine Learning - A Probabilistic Perspective by Murphy|Murphy Ch. 2]]
* [[Machine Learning - A Probabilistic Perspective by Murphy|Murphy 4.5]] - on the Wishart and Inverse Wishart