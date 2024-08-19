* We may apply [[Bayesian Statistics|Bayesian statistics]] to compute for a posterior distribution of weights and obtain a MAP estimate as follows:
  $$
  \hat{w}_\text{MAP}=\underset{w}{\text{argmax}}  \ P(w\mid \mathcal D)= \underset{w}{\text{argmax}} \ P(\mathcal D\mid w)  \ P(w)
  $$
  We may then sequentially update the parameters in a Bayesian manner. 
* Under the assumption of Conditional Independence, we have
  $$
  \begin{equation}
  \begin{split}
  P(\mathcal{D} \ | \ w)&=\prod_{1\le i\le |\mathcal{D}|} P(\mathcal{D}^{(i) } \ | \ w) \\ &= \prod_{1\le i\le |\mathcal{D}|} \frac{1}{\sigma\sqrt{2\pi}}e^{-\frac{\left(y^{(i)} - w \cdot x^{(i)}\right)^2}{2\sigma^2}} \\ \ln(P(\mathcal{D} \ | \ w\ ))&= \sum_{1\le i\le |\mathcal{D}|} {\ln\left(\frac{1}{\sigma\sqrt{2\pi}}\right) - \frac{1}{2\sigma^2}\left(y^{(i)}-w\cdot x^{(i)}\right)^2} \\
  \ln(P(\mathcal{D} \ | \ w\ ))&\propto-\sum_{1\le i\le |\mathcal{D}|} { \frac{1}{2\sigma^2}\left(\mathcal{D}^{(i)}-w\cdot x^{(i)}\right)^2}
  \end{split}
  \end{equation}
  $$
  Taking the negative of the log above gives us the Mean Square Error
  
  $$
  -\ln (P (\mathcal{D}\mid w)) \propto \sum_{1\le i\le |\mathcal{D}|} { \frac{1}{2\sigma^2}\left(\mathcal{D}^{(i)}-w\cdot x^{(i)}\right)^2} \propto \text{MSE} 
  $$

# Regularization using Priors
* The effect is the same as that of [Regularization](https://www.youtube.com/watch?v=Z6HGJMUakmc) depending on the choice of prior.
## Gaussian
* With a Gaussian prior and Gaussian likelihood, we get a Gaussian posterior with variance as
  $$
  \sigma^2_N = \sigma^2+x^TV_Nx
  $$
  Where $\sigma^2$ is the variance of the observation noise, and $V_N$ is the variance in the parameters (i.e., how close $x$ is to the training data). *This captures uncertainty as we move away from the training data, allowing the model to capture what is known and what is unknown*.
	* We are unable to capture this kind of uncertainty using a plugin approximation (i.e., MAP) means 

* With unknown variance, and likelihood 
  $$
  P(y\mid X, w,\sigma^2)=\mathcal N (y\mid Xw,\sigma^2I_n)
  $$
  the posterior and the conjugate prior of the joint parameter distribution $P(w,\sigma^2)$ follow a [[Probability Distributions Zoo|Normal Inverse Gaussian]] distribution. (see more at [[Machine Learning - A Probabilistic Perspective by Murphy|Murphy Ch. 7.6.3]]) 
	* The posterior variance is given by the Wald Distribution
	* The posterior weights follow a T distribution.
	* The posterior predictive distribution $P(\hat y \mid \hat X, \mathcal{D})$ also follows a T distribution
	* We may use a **g-prior** of the form
	  $$
	  \text{NIG}(w,\sigma^2\mid w_0,g(X^TX)^{-1}, 0,0)
	  $$
	  Where $g$ controls the strength of the prior (and has a regularization effect), and we scale on $(X^TX)^{-1}$ so that the posterior is invariant to input scaling.
		* Using a g-prior with $g=N$, where $N$ is the number of samples gives the **unit information prior** which contains as much information as one sample.

* If weights are sampled from $w\sim\mathcal{N}(0,\tau^2)$
  $$
  -\ln(P(w)) \propto \frac{\sigma^2}{\tau^2} ||w||^2 
  $$
  Which is the regularization term in *L2-regularization* with $\lambda = \frac{\sigma^2}{\tau^2}$. 
	* $w$  favors values closer to $0$, and it takes strong evidence to update it to become larger. Hence, all components in $w$ tend to be roughly the same and small, effectively regularizing.

## Laplacian Prior
* If weights are sampled [[Probability Distributions Zoo|from]] $w\sim \text{Lap}(0, b)$ then 
  
  $$
  -\ln(P(w)) \propto \frac{1}{b} ||w|| 
  $$
  Which is the regularization term in *L1-regularization.*

* While it also favors values of $w$ closer to 0, it also does not take as much evidence to update $w$ to be something large. 
* Since we are minimizing, however, this means that few components of $w$ will actually have a large value, while the rest will be smaller.

## Empirical Bayes
* Assuming unknown priors, we can use [[Bayesian Statistics|empirical Bayes]] as an alternative to cross-validation. The goal is to maximize the marginal likelihood by choosing an appropriate $\eta=(\alpha,\lambda)$. 
  $$
  P(\mathcal{D}\mid m) = \iint P(\mathcal D\mid w,m) \ P(w\mid m,\eta) \ P(\eta\mid m) \ dw d\eta
  $$

# Links
* [[Linear Models]]
* [[Machine Learning - A Probabilistic Perspective by Murphy|Murphy Ch. 7]]
*  [[Dive into Deep Learning by Zhang, Lipton, Li and Smola|Zhang et. al Ch. 3]] - more on Linear Regression
* [Bayesian Linear Regression: Data Science Concepts](https://www.youtube.com/watch?v=Z6HGJMUakmc)