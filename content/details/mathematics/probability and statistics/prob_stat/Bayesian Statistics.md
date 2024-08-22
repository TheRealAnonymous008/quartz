* It makes use of the posterior distribution $P(\theta\mid\mathcal{D})$ to summarize all the unknowns about a random variable (compare with [[Frequentist Statistics]])
* It assumes the dataset as fixed, and the parameters unknown.
# Posteriors
### Maximum A Posteriori
* *Make use of a point estimate for the posterior* (via mean, median or mode).
  $$
  \hat{\theta}=\underset{\theta}{\text{argmax}} \ P(\theta\mid\mathcal{D})
  $$
* For MAP estimates, we make use of the mode because of algorithmic efficiency and ease of interpretability.
* Some drawbacks.
	* It is a point estimate so there is no measure of uncertainty. 
		* Solution: Use confidence intervals
	* It overfits as an estimator because we don't capture uncertainties.
	* The mode is a poor choice as a summary statistic since it is prone to extrema or skewed distributions. 
		* Solution: Use Decision Theory-based methods.
	* It is not invariant to reparameterization. Changing from one representation to another equivalent representation changes the MAP estimate.
		* One solution to this is to optimize the following 
		  $$
		  \hat{\theta}=\underset{\theta}{\text{argmax}} \ P(\theta\mid\mathcal{D}) \ P(\theta) \ |I(\theta)|^{-\frac{1}{2}}
		  $$
		  Where $|I(\theta)|$ is the [[Determinant]] of the **Fisher Information Matrix** associated with $P(x\mid\theta)$ which is parameterization independent.
		* Unfortunately, optimizing the above is difficult.

### Credible Intervals
* *We can specify a width measured using a contiguous region* that contains $(1-\alpha)/2$ of the posterior distribution's mass in each tail (either side)
	* Hence why in Normal Distributions, we report $\mu \pm \sigma$. 
	* These are called **credible intervals** since their mass is $(1-\alpha)$. They are **central** if they have $(1-\alpha)/2$ mass on either side.
	* *Credible intervals are not sampling intervals*. Credible intervals act on the posterior distribution.
* We can also use Monte Carlo approximation to draw $S$ samples form the from the posterior
	* Sort the $S$ samples
	* Then, find the entries that rank $\pm \alpha/S$ from the estimator.
* We may also use the **highest posterior density region / interval** which contains the set of most probable points that in total constitute $1-\alpha$ mass. That is, if we find threshold $p^\ast$ such that for 
  $$
  1-\alpha=\int_{\theta : P(\theta\mid\mathcal{D})>p^\ast}P(\theta\mid\mathcal{D})d\theta
  $$
  The HPD is then the set we integrated over 
  $$
  C_{\alpha}(\mathcal{D}) =\{\theta:P(\theta\mid D) \ge p^{\ast}\}
  $$
# Model Selection
* *Problem*: Given a set of models of varying complexities, how should we choose the best model?
### Cross Validation 
* Estimate the generalization error of all the candidate models, and pick the model that seems to be the best. 
* Requires fitting $K$ times. 
### Bayesian Model Selection
* Compute the posterior over models and use the MAP model. That is, calculate 
  $$
  P(m\mid \mathcal{D})= \frac{P(\mathcal{D} \mid m) \ P(m)}{\sum_{m\in\mathcal{M}}P(m,\mathcal{D})}
  $$
  And choose 
  $$
  \hat{m}=\underset{m\in\mathcal{M}}{\text{argmax}} \ P(m\mid\mathcal{D})
  $$
* We can can use the **marginal likelihood** or the **evidence** for model $m$. This is the equivalent of an MLE. Assuming a uniform prior over models, we have 
  $$
  P(\mathcal{D}\mid m)=\int P(D\mid \theta) \ P(\theta\mid m) d\theta
  $$
* The intuition behind the marginal likelihood is that *we want to prevent overfitting by suggesting that more parameters = better performance*. This is **Bayesian Occam's razor**.
	* Complex models which can predict many things must spread its probability mass thinly so that it will not obtain as large a probability as simpler models. This is the **conservation of probability mass**. 

### Marginal Likelihood
* Computing the Marginal likelihood. 
	
	Let 
	$Q$ be unnormalized distributions
	$Z$ be normalization constants$P(\theta)=Q(\theta)/Z_0$ be the prior
	$P(\mathcal{D}\mid \theta) = Q(\mathcal{D}\mid \theta) / Z_l$ be the likelihood
	$P(\theta\mid\mathcal{D}) = Q(\theta\mid \mathcal{D})/Z_N$ be the posterior.
	
	We have that the marginal likelihood $P(\mathcal{D})$ (the conditioning on $m$ omitted for convenience) is 
$$
\begin{split}P(\theta\mid\mathcal{D})&= \frac{P(D\mid\theta) P(\theta)}{P(\mathcal{D})} \\ 
\frac{Q(\theta\mid\mathcal[D])}{Z_N} &= \frac{Q(\mathcal{D}\mid \theta) Q(\theta)}{Z_l Z_0P(\mathcal{D})} \\ 
P(\mathcal{D}) &= \frac{Z_N}{Z_0Z_l}
\end{split}
$$
* Some useful marginal likelihoods
	* **Beta Prior** 
	  $$
	  P(\mathcal{D})=\frac{B(a+N_1,b+N_0)}{B(a,b)}
	  $$
	  
	* **Dirichlet Prior** 
	  $$
	  \begin{split}P(\mathcal{D}) &= \frac{B(N+\alpha)}{B(\alpha)} \\ 
	  
	  &= \frac{\Gamma(\sum_ka_k)}{\Gamma(N+\sum_ka_k)}\prod_k\frac{\Gamma(N_k+a_k)}{\Gamma(a_k)}\\
	  B(\alpha)&= \frac{\prod_{k=1}^K \Gamma(a_k)}{\Gamma(\sum_ka_k)} \\ 
	  \end{split}
	  $$
	  
	* **Gaussian-Gaussian-Wishart** 
	  $$
	  P(\mathcal{D}) = \frac{1}{\pi^{ND/2}}\left(\frac{\kappa_0}{\kappa_N}\right)^{D/2} \frac{|S_0|^{v_0/2} \Gamma_D(v_N/2)}{|S_N|^{v_N/2} \Gamma_D(v_0/2)}
	  $$

* The **Bayesian Information Criterion** is an approximation for the integral in the marginal likelihood. It is simply of a *penalized log likelihood* form, where the penalty depends on model complexity. That is 
  $$
  \text{BIC}=\log P(\mathcal{D}\mid\hat\theta) -\frac{\text{dof}(\hat\theta)}{2}\log N \approx\log P(\mathcal{D})
  $$
  Where $\hat{\theta}$ is an estimate (MLE / MAP) and $\text{dof}(\hat\theta)$ is the degrees of freedom.
  
  We aim to *maximize the BIC score*.

* We can also define a **BIC-cost** that we *minimize* 
  $$
  \text{BIC-cost} = -2\log P(\mathcal{D}\mid\hat\theta) +\text{dof}(\hat\theta)\log N \approx -2\log P(\mathcal{D})
  $$
  
	* The **minimum description length** principle is tied to this. It says the score of a model is *how well it fits the data minus how complex the model is to define*.
* For complex models, we may use the **Akaike information criterion**. It has *smaller penalty than BIC* 
  $$
  \text{AIC}(m,\mathcal{D}) = \log P(\mathcal{D}\mid\hat{\theta}_\text{MLE}) - \text{dof}(m)
  $$
  
* *The prior has an effect on the marginal likelihood* since it is an average of likelihoods weighted by priors over the parameter. 
	* *When the prior is uncertain, have a prior for the prior.* Usually uninformative priors suffice.
	* We compute 
	  $$
	  P(\mathcal{D}\mid m)=\iint P(\mathcal{D}\mid w) P (w\mid \alpha, m) P(\alpha \mid m)  \ dw \ d\alpha
	  $$
	  
### Hierarchical Bayes
* In Hierarchical Bayes, we assume uncertainty about the priors. That is, *we put priors on the priors*. That is, for $P(\theta\mid\mathcal{D})$ we put the prior as $P(\theta\mid\eta)$ for hyperparameters $\eta$. 
* In graphical form it is represented as 
  $$
  \eta\to\theta\to\mathcal{D}
  $$
  
* This can be coupled with **parameter tying** wherein we assume that parameters are shared across multiple distributions.
	* In such a case, we assume $\theta$ is drawn from some distribution parameterized by $\eta$.
	* This leads to **multi-task learning**.
### Empirical Bayes
* We may also use **empirical Bayes** or **type II maximum likelihood** or the **evidence procedure**. Where via numerical optimization we optimize 
  $$
  \begin{split}\hat\alpha& =\underset{\alpha}{\text{argmax}} \ P(\mathcal{D}\mid \alpha,m)  \\ 
  &= \underset{\alpha}{\text{argmax}}\int P(\mathcal{D}\mid w) \ P (w\mid \alpha,m) \ dw\\ 
  P(\mathcal{D}\mid m) &\approx \int P(\mathcal{D}\mid w) P(w\mid \hat{\alpha}, m)  \ dw
  \end{split}
  $$
  
* It is a computationally cheap approximation to inference in a hierarchical Bayes model. 
* It makes use of a point estimate for the hyperparameter $\eta$. *Assuming the hyperparameters are smaller in dimensionality, this is less prone to overfitting*.
* For deeper hierarchical models, the shallower the depth we perform empirical Bayes, the more Bayesian the model becomes.
* *This gives a crude framework for why hyperparameter optimization works. We can simply use an estimate instead of integrating over hyperparameter space*.
### Bayes Factors
* The **Bayes Factor** is the *ratio of marginal likelihoods* between $M_0$ and $M_1$. That is 
  $$
  \text{BF}_{1,0}=\frac{P(\mathcal{D}\mid M_1)}{P(\mathcal{D}\mid M_0)} =  \frac{P(M_1 \mid \mathcal{D})}{P(M_0\mid \mathcal{D})} \frac{P(M_0)}{P(M_1)}
  $$
  When $\text{BF}_{1,0} > 1$, prefer $M_1$ else, prefer $M_0$.
* The Bayes factor will always favor the simpler model since complex models will have a very small prior.
# Priors
* The **[Jeffreys-Lindley paradox](https://en.wikipedia.org/wiki/Lindley%27s_paradox)** arises from a poor choice of priors. 
* *Priors capture initial assumptions about the world*. 
* **Uninformative Priors** assume that we have no strong beliefs about the parameter $\theta$.
* **Improper Priors** are those that do not integrate to $1$. They are still useful considering we normalize the posterior anyway. Note that *this requires the posterior to be prior*. 
* The **Haldane prior** is defined as the most non-informative prior of a Bernoulli process. It is defined by 
  $$
  \lim_{c\to 0} \text{Beta}(c,c)=\text{Beta}(0,0)
  $$
  It is a mixture of two equal point masses at $0$ and $1$.
* The **Jeffreys prior** is a non-informative prior. It is defined as a probability distribution that is 
  $$
  P(\theta)\propto \sqrt{\det{I(\theta)}}
  $$
  Where ${I}$ is the Fisher information matrix.
	* The idea is that *any reparameterization of an uninformative prior is also uninformative*. Thus, we choose a convenient reparameterization via the Fisher information matrix.
	* The Jeffreys prior is scale and translation invariant.

* **Robust Priors** are those which have heavy tails to avoid forcing things being close to the prior mean. This is done so that *the prior has no effect on the result*.

* **Sensitivity Analysis** can be used to check if the choice of prior was appropriate by *checking how the conclusion changes in response to changes in modeling assumptions*. Insensitivity to priors is desirable.

* An important theorem: *The mixture of conjugate priors is also conjugate*. 
	* Suppose $z=k$ is an indicator variable that $\theta$ comes from mixture component $k$. Then we have a prior 
	  $$
	  P(\theta)=\sum_kP(z=k)P(\theta\mid z= k)
	  $$
	  Where each $P(\theta\mid z= k)$ is conjugate. $P(z=k)$ are the **prior mixing weights**. The posterior is given as 
	  $$
	  P(\theta\mid \mathcal{D})=\sum_k P(z=k\mid \mathcal{D}) \ P(\theta\mid\mathcal{D},z=k)
	  $$
	  Where the **posterior mixing weights** are given by 
	  $$
	  P(Z=k\mid\mathcal{D})=\frac{P(Z=k) \ P(\mathcal{D} \mid Z =k )}{\sum_{k'} P(Z=k') \ P(\mathcal{D}\mid Z=k')}
	  $$
	  Where $P(\mathcal{D}\mid Z=k)$ is the marginal likelihood for the mixture component $k$.
# Bayesian Decision Theory
* *The game*: Based on some unknown label $y\in\mathcal{Y}$, we are given observation $x\in\mathcal{X}$. We then make decision $a\in\mathcal{A}$ and incur an appropriate loss $L(y,a)$ which measures how compatible the action was with the label.
* *The goal*: Make a **decision procedure** $\delta:\mathcal{X}\to\mathcal{A}$ which specifies the optimal action for each input [^1] such that *loss is minimized*. 
  $$
  \delta(x)=\underset{a\in\mathcal{A}}{\text{argmin}} \ \mathbb{E}[L(y,a)] 
  $$
  Or if we specify a **utility function** so that *utility is maximized* 
  $$
  U(y,a)=-L(y,a)
  $$
  we get the equivalent **maximum expected utility principle**
  $$
  \delta(x)=\underset{a\in\mathcal{A}}{\text{argmax}} \ \mathbb{E}[U(y,a)] 
  $$
  
* The expected value $\mathbb{E}[X]$ is interpreted as the expected value of the label given the observations.
* For  Bayesian Decision Theory, we minimize the **posterior expected loss** 
  $$
  \rho(a\mid x) = \mathbb{E}_{P(y\mid x)} [L(y,a) = \sum_{y}L(y,a)P(y\mid x)
  $$
* The **Bayes decision rule** is given as *minimizing the posterior expected loss*
  $$
  \delta(x)=\underset{a\in\mathcal{A}}{\text{argmin}} \ \rho(a\mid x)
  $$

* Some common rules:
	* MAP estimate minimizes the $0,1$-loss.
	* MAP estimate can minimize the case where we include a "don't know" class under specific cases.
	* The posterior mean minimizes $L_2$ loss. This is the **minimum mean squared error**.
	* The posterior median minimizes $L_1$ loss.
* For supervised learning tasks, this rule can be translated to *minimizing generalization error*. Given unknown parameters $\theta$ and action $\delta$ with cost function $l(y,x)$ that determines how far $x$ is from ground truth $y$, we have
  $$
  L(\theta,\delta)=\mathbb{E}_{(x,y)\sim P(x,y\mid \theta)}[l(y,\delta(x)]=\sum_{x}\sum_y L(y,\delta(x)) \ P(x,y\mid \theta)
  $$
  Which is the **generalization error**. 
	* The goal becomes minimizing 
	  $$
	  P(\delta\mid\mathcal{D})=\int P(\theta\mid\mathcal{D})L(\theta,\delta) \ d\theta
	  $$
[^1]: Not unlike [[Reinforcement Learning]]

# Topics 
* [[Model Performance]] - specifically Generalization Error and Confusion Matrices .

# Links
* [[Machine Learning - A Probabilistic Perspective by Murphy|Murphy Ch. 5]]
	* 5.6 - More on Hierarchical and Empirical Bayes
	* 5.7.1 - Bayes estimators for common loss functions
* [The Fisher Information](https://www.youtube.com/watch?v=pneluWj-U-o) - more on the Fisher information. Essentially it measures the amount of information a variable carries about a parameter.

* [[Probability Theory]] - more on the basics of probability. Bayes' theorem is stated [[Fundamental Constructs of Probability Theory|here]].
* [[Bayesian Models]] 
