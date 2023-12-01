* We make use of [[Statistical Estimators]] in Frequentist statistics.
# Frequentist Decision Theory
* We choose any estimator or decision parameter that we want.
* The **risk** of the estimator is defined as
  $$
  \begin{split}R(\theta^\ast,\delta)&=\mathbb{E}_{P(\hat{\mathcal{D}} \mid \theta^\ast)}\left[L(\theta^\ast,\delta(\hat{\mathcal{D}}))\right] \end{split}
  $$
  
* *The risk is not computable* since it relies on $\theta^\ast$. 
* The **Bayes risk** of an estimator is defined as 
  $$
  \begin{split}R_B(\delta)&=\mathbb{E}_{P(\theta^\ast)}\left[R(\theta^\ast, \delta)\right] \end{split}
  $$
  
	* A **Bayes decision rule** minimizes the expected Bayes risk.
	* *Murphy 6.3.1.* A Bayes estimator can be obtained by minimizing the posterior expected loss for each $x$. 
		* Thus, picking the optimal action on a case-by-case basis is optimal on average.
	* *Murphy 6.3.2*. Every admissible decision rule is a Bayes decision rule with respect to some possibly improper, prior distribution. 
		* *Thus, the best way to minimize frequentist risk is to be Bayesian*
* The **maximum risk** of an estimator is defined as 
  $$
  R_{\text{max}}(\delta)=\max_{\theta^\ast} R(\theta^\ast,\delta)
  $$
  
	* The **minimax rule** is one that minimizes the maximum risk 
	  $$
	  \delta_{MM}=\underset{\delta}{\text{argmin}} \ R_\text{max} (\delta)
	  $$
	  
	* The minimax estimator tends to be pessimistic and difficult to compute.
	* *They are equivalent to Bayes estimators under a least favorable prior*.
* Given two estimators $\delta_1$ and $\delta_2$, if $\forall \theta\in\Theta$, 
  $$
  R(\theta,\delta_1)\le R(\theta,\delta_2)
  $$
  then $\delta_1$ **dominates** $\delta_2$ (strictly so if we replace $\le$ with $<$)
* An estimator is **admissible** if it is not strictly dominated by any other estimator.
	* In practice, *the sample median is often better than the sample mean because it is more robust to outliers*. 
	* It is easy to construct an admissible estimator (see [[Machine Learning - A Probabilistic Perspective by Murphy|Murphy Thm. 6.3.3]]. Hence *admissibility is not sufficient for good estimators*.

# Pathologies
* Confidence intervals mean we condition on unknown results, rather than on known results. 
* Hypothesis testing means we favor rejecting the null rather than proving the null hypothesis.
* The $p$-value of frequentist statistics is dependent on when we decide to stop collecting samples. 
* Frequentism violates the **likelihood principle**, which says inference should be based on the likelihood of what is observed rather than hypothetical future data. The likelihood principle follows from two principles
	* The **sufficiency principle** - a sufficient statistic should contain all the relevant information about an unknown parameter.
	* **Weak conditionality** - inferences should be based on what happened rather than what might not have happened.
# Topics
* [[Statistical Estimators]]
* [[Model Performance]] - specifically refer to empirical risk minimization 
# Links
* [[Machine Learning - A Probabilistic Perspective by Murphy|Murphy Ch. 6]]