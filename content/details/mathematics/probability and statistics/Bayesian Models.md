* Suppose we have a **posterior predictive distribution** that determines if an observed sample $x$ is part of some dataset $\mathcal{D}$. We represent this with $P(x\mid \mathcal{D})$ and describe it with some model $M$.
* We become more certain about this probability distribution with more data.
# Bayesian Components
* We follow **Occam's Razor**, that is we choose to describe $\mathcal{D}$ with the simplest model possible consistent with the dataset. This is quantified using the **likelihood** that the chosen hypothesis is consistent, that is, it is $P(\mathcal{D}\mid M)$
* We can also incorporate beliefs about the space of models using the **prior**. That is, $P(M)$
* Our posterior, then, is obtained as the normalized product of the likelihood and the posterior. *The posterior is the internal belief state about the world*. It is validated via observations about the world.
# Estimates
* In general, when we have enough data, the posterior $P(M\mid D)$ peaks on a single $M$, namely the **Maximum a Posteriori estimate** given by 
  $$
  M_{\text{MAP}}=\underset{M}{\text{argmax}}\ P(M\mid \mathcal{D})
  $$
* Another estimate is the **Maximum Likelihood Estimate** where we choose maximize the likelihood of the data being observed given model $M$ or: 
  $$
  M_{\text{MLE}}=\underset{M}{\text{argmax}} \ P(\mathcal{D}\mid M)
  $$
  
* As the size of the dataset increases, $M_{\text{MAP}}$ converges to $M_\text{MLE}$. With enough data, *the data overwhelms any prior assumptions*.
	* To see this, note that 
	  $$
	  \underset{M}{\text{argmax}}\ P(M\mid \mathcal{D})= \underset{M}{\text{argmax}}\ \log{P(M)}+ \ \log{P(\mathcal{D}\mid M)}
	  $$
	  And $P(\mathcal{D}\mid M)$ scales with more data, whereas $P(M)$ does not.
# Posterior Predictive Distributions
* The posterior predictive distribution can be calculated using **Bayes Model Averaging**  
  $$
  P(y\mid D, x)=\sum_{M}P(y\mid x,M)\ P(M\mid\mathcal{D})
  $$
* It can also be approximated using the **Plugin Approximation** given as 
  $$
  P(y\mid D, x)\approx P(x\mid \hat{M})
  $$
  That is, we can approximate the posterior distribution using a model $\hat{M}$ derived from some estimate (i.e., MLE or MAP)
	* Note: This underestimates the uncertainty.
	* The estimate will certainly be different from using a pure Bayesian approach, but they converge to the same value with more data.
# Extension
* The Bayesian model can be extended for the case of continuous distributions, essentially by replacing sums with integrals and finite sets with spaces.
* To characterize the dataset $\mathcal{D}$, we can use a set of **sufficient statistics** $s(\mathcal{D})$ which describe the dataset fully. That is, if we have $\theta$ as a parameter we get 
  $$
  p(\theta \mid \mathcal{D})=p(\theta\mid s(\mathcal{D}))
  $$
### Beta Binomial Model
* One extension of the above is the **Beta Binomial**, which is applicable for a binary classification task. That is 
  $$
  \text{Beta}(\theta\mid a,b)=\theta^{a-1}(1-\theta)^{b-1}
  $$
  Where $\theta$ is the probability of success.
* Any additional evidence constitutes updating $a$ and $b$ above based on the new successes and failures observed. 
* The posterior of the beta-binomial is convex. The posterior mean is a combination of the prior mean and the MLE
* The posterior variance decreases at a rate of $\frac{1}{\sqrt{N}}$, where $N$ is the number of samples. The variance is maximized when $\hat{\theta}=0.5$ and minimized when $\hat{\theta}=0$ or $1$.
	* This implies, entropy is at a maximum when the probabilities of success and failure are equally likely (see [[Information Theory|here]] for more) 
* On its own, the model highlights the **sparse data problem** wherein our MLE estimate will be close to $0$ when the dataset is small. This approximation is often poor.
	* This can be mitigated with **Laplace's Rule of Succession** wherein we assume a uniform prior and plug in the posterior mean so that $$
	  P(x=1\mid\mathcal{D})=\frac{N_1+1}{N_1+N_0+2}
	  $$Where $N_0$ and $N_1$ are counts for failure and successes respectively. This is called **Add One Smoothing**.
### Dirichlet Multinomial Model
* The **Dirichlet Multinomial Model** is a *generalization of the Beta Binomial model* but for $K$ outcomes instead of two outcomes.
* The update rule for the posterior given new evidence is simply an extension of the rule for the beta binomial model. That is 
  $$
  P(x\mid \mathcal{D})=\text{Dir}(a_1+N_1,a_2+N-2,\dots,a_K + N_K)
  $$
  Where $N_i$ denotes the number of times the $i$-th event occurs, and 
  
  $a_i$ denotes the hyperparameters in the prior. That is, we assume a prior of $\text{Dir}(a_1,\dots, a_K)$
* The MLE (assuming a uniform prior) and MAP estimates are just *extensions of the corresponding estimates for the Beta Binomial.*
* The Posterior Distribution is characterized as an *extension of the posterior distribution of the beta binomial*.


# Links
* [[Machine Learning - A Probabilistic Perspective by Murphy|Murphy Ch. 3.2 - 3.4]]
	* Ch. 3.3 - discussion on the Beta Binomial Model
	* Ch. 3.4 - discussion on the Dirichlet Multinomial Model

* [[Information Theory]] - more on entropy.
* [[Probability Distributions Zoo]] - see more about the Beta and Dirichlet distributions