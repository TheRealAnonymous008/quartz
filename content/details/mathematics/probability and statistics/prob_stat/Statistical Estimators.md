* It makes use of the sampling distribution $P(\mathcal{D}\mid \theta)$ from which we derive the observations (compare with [[Bayesian Statistics]])
* It assumes the dataset as random, and the parameters unknown but fixed. Thus we make use of **parameter estimates**. 
	* An **estimator** $\delta$ is applied to data $\mathcal{D}$ so that the **parameter estimate** $\hat{\theta}$ is obtained by
	  $$
	  \hat\theta=\delta(\mathcal{D})
	  $$
	  
	* The sampling distribution is obtained by sampling many datasets $\mathcal{D}^{(s)}$ and computing parameter estimates. *The sampling distribution is the distribution of $\hat\theta$* 
		* This can be obtained with **bootstrapping** where we sample many datasets and use the empirical distribution to estimate the sampling distribution. *The sampling distribution and the posterior distribution $P(\theta\mid\mathcal{D})$ are similar assuming a weak prior*.
		* Under certain conditions, as the sample size tends to infinity, the sampling distribution of the MLE becomes Gaussian (see more in [[Machine Learning - A Probabilistic Perspective by Murphy|Murphy 6.2.2]])

* We use heuristics since we do not have an automatic way of choosing between estimators. 
### Properties of Good Estimators
* An estimator is **consistent** if it eventually recovers the true parameters that generated the data as the sample size goes to infinity. That is
  $$
  \lim_{|\mathcal{D}|\to\infty}\hat\theta(\mathcal{D})=\theta^\ast
  $$
  
* The **bias** of an estimator is defined as
  $$
  \text{bias}(\hat{\theta})=\mathbb{E}_{P(\mathcal{D}\mid\theta^\ast)}\left[\hat\theta(\mathcal D) -\theta^{\ast}\right]
  $$
  
	* An estimator is **unbiased** if its bias is $0$. *This means the sampling distribution is centered on the true parameter*.
	* Another way to say this is if $\mathbb{E}[\hat{\theta}(\mathcal D)] = \theta^\ast$
	* It is the inherent error that you obtain from the model even with infinite training data. This is due to *the model being inherently "biased" towards a particular kind of solution.*
* Another consideration is **minimum variance**. 
	* **Cramer-Rao lower bound**. Let $X_1,\dots, X_n\sim P(X\mid\theta_0)$ and $\hat{\theta}=\hat{\theta}(x_1,\dots, x_n)$ be an unbiased estimator of $\theta_0$. Then under various smoothness assumptions on $P(X\mid\theta_0)$, we have 
	  $$
	  \text{Var}[\hat\theta]\ge \frac{1}{nI(\theta_0)}
	  $$
	  Where $I$ is the Fisher information matrix.
	* The variance is *the degree to which the classifier varies if it is trained on a different dataset*.
* The Maximum Likelihood Estimator is **[[Asymptotic Analysis|asymptotically]] optimal**. It is consistent, biased at the limit, and achieves the Cramer-Rao lower bound.
### Bias-Variance Tradeoff
* If we are using Mean Squared Error, we can show that for a given estimator or model
  $$
  \text{MSE}=\text{Variance}+\text{bias}^2
  $$
  
* In terms of modeling tasks, a high variance means that the model is more flexible and can adapt to noise due to the estimator. However, it is also prone to overfitting as it adapts to all patterns
* A high bias means that the model is less prone to noise, and thus it can generalize well. However, it is also not flexible, and if the bias of the model is too far from the true estimate of the parameters, it will underfit.
* Note for classification with $0-1$ loss, this does not hold.
	* For a correct estimate, the bias will be negative, and it pays to decrease the variance.
	* For an incorrect estimate, the bias will be positive, and it pays to increase the variance.

* Here is a more formal statement of this tradeoff. Suppose we have training dataset $\mathcal{D} = (x^{(i)}, y^{(i)})$. Let $f$ be the true function such that 
  $$
  y = f(x) + \epsilon
  $$
  Where $\epsilon$ is Gaussian noise.
  
  Let $\hat{f}_\mathcal{D}$ be the approximate function to $f(x)$ trained on $\mathcal{D}$. We can then quantify how good $\hat{f}_\mathcal{D}$ is based on the MSE.
  
  The MSE can be framed as
  $$
  \mathbb{E}_{\mathcal{D}, \epsilon}\left[\left(y-\hat{f}_\mathcal{D}(x)\right)^2\right]
  $$
  It can then be decomposed as follows. Let us drop subscript $\mathcal{D}$ for convenience.
  
  $$
  \mathbb{E}[y]=\mathbb{E}[f(x)+\epsilon]=\mathbb{E}[f(x)]+\mathbb{E}[\epsilon]=\mathbb{E}[f(x)]
  $$
  
  $f$ is independent of our choice of $\mathcal{D}$ so $\mathbb{E}[f]=f$
  
  The variance $\text{Var}[y] = \sigma^2$ is computed using the variance of the noise term. This follows because $f$ is independent of noise and is deterministic.

  The MSE then has the following computation 
  $$
  \begin{equation}
  \begin{split}
  \text{MSE} & = \mathbb{E}[(y-\hat{f})] \\& = \mathbb{E}[(f+\epsilon-\hat{f})^2] \\ 
  &=\mathbb{E}[(f+\epsilon-\hat{f}+\mathbb{E}[\hat{f}]-\mathbb{E}[\hat{f}])]\\
  &= \mathbb{E}[(f-\mathbb{E}[\hat{f}])^2] + \mathbb{E}[\epsilon^2] + \mathbb{E}[(\mathbb{E}[\hat{f}]-\hat{f})^2] \\
  &= (f-\mathbb{E}[\hat{f}])^2+\text{Var}[\epsilon]+\text{Var}[\hat{f}]\\
  &= \text{Bias}[\hat{f}]^2 + \sigma^2 + \text{Var}[\hat{f}]
  \end{split}
  \end{equation}
  $$


# Links
* [[Random Variables and Probability Distributions]]
