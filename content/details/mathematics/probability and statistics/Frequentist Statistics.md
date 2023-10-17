* It makes use of the sampling distribution $P(\mathcal{D}\mid \theta)$ from which we derive the observations (compare with [[Bayesian Statistics]])
* It assumes the dataset as random, and the parameters unknown but fixed. Thus we make use of **parameter estimates**. 
	* An **estimator** $\delta$ is applied to data $\mathcal{D}$ so that the **parameter estimate** $\hat{\theta}$ is obtained by $$\hat\theta=\delta(\mathcal{D})$$
	* The sampling distribution is obtained by sampling many datasets $\mathcal{D}^{(s)}$ and computing parameter estimates. *The sampling distribution is the distribution of $\hat\theta$* 
		* This can be obtained with **bootstrapping** where we sample many datasets and use the empirical distribution to estimate the sampling distribution. *The sampling distribution and the posterior distribution $P(\theta\mid\mathcal{D})$ are similar assuming a weak prior*.
		* Under certain conditions, as the sample size tends to infinity, the sampling distribution of the MLE becomes Gaussian (see more in [[$Machine Learning - A Probabilistic Perspective by Murphy|Murphy 6.2.2]])
# Frequentist Decision Theory
* We choose any estimator or decision parameter that we want.
* The **risk** of the estimator is defined as $$\begin{split}R(\theta^\ast,\delta)&=E_{P(\hat{\mathcal{D}} \mid \theta^\ast)}\left[L(\theta^\ast,\delta(\hat{\mathcal{D}}))\right] \end{split}
  $$
* *The risk is not computable* since it relies on $\theta^\ast$. 
* The **Bayes risk** of an estimator is defined as $$\begin{split}R_B(\delta)&=E_{P(\theta^\ast)}\left[R(\theta^\ast, \delta)\right] \end{split}
  $$
	* A **Bayes decision rule** minimizes the expected Bayes risk.
	* *Murphy 6.3.1.* A Bayes estimator can be obtained by minimizing the posterior expected loss for each $x$. 
		* Thus, picking the optimal action on a case-by-case basis is optimal on average.
	* *Murphy 6.3.2*. Every admissible decision rule is a Bayes decision rule with respect to some possibly improper, prior distribution. 
		* *Thus, the best way to minimize frequentist risk is to be Bayesian*
* The **maximum risk** of an estimator is defined as $$R_{\text{max}}(\delta)=\max_{\theta^\ast} R(\theta^\ast,\delta)$$
	* The **minimax rule** is one that minimizes the maximum risk $$\delta_{MM}=\underset{\delta}{\text{argmin}} \ R_\text{max} (\delta)$$
	* The minimax estimator tends to be pessimistic and difficult to compute.
	* *They are equivalent to Bayes estimators under a least favorable prior*.
* Given two estimators $\delta_1$ and $\delta_2$, if $\forall \theta\in\Theta$, $$R(\theta,\delta_1)\le R(\theta,\delta_2)$$then $\delta_1$ **dominates** $\delta_2$ (strictly so if we replace $\le$ with $<$)
* An estimator is **admissible** if it is not strictly dominated by any other estimator.
	* In practice, *the sample median is often better than the sample mean because it is more robust to outliers*. 
	* It is easy to construct an admissible estimator (see [[$Machine Learning - A Probabilistic Perspective by Murphy|Murphy Thm. 6.3.3]]. Hence *admissibility is not sufficient for good estimators*.
# Choosing Estimators
* We use heuristics since we do not have an automatic way of choosing between estimators. 
### Properties of Good Estimators
* An estimator is **consistent** if it eventually recovers the true parameters that generated the data as the sample size goes to infinity. That is $$\lim_{|\mathcal{D}|\to\infty}\hat\theta(\mathcal{D})=\theta^\ast$$
* The **bias** of an estimator is defined as $$\text{bias}(\hat{\theta})=E_{P(\mathcal{D}\mid\theta^\ast)}\left[\hat\theta(\mathcal D) -\theta^{\ast}\right]$$
	* An estimator is **unbiased** if its bias is $0$. *This means the sampling distribution is centered on the true parameter*.
* Another consideration is **minimum variance**. 
	* **Cramer-Rao lower bound**. Let $X_1,\dots, X_n\sim P(X\mid\theta_0)$ and $\hat{\theta}=\hat{\theta}(x_1,\dots, x_n)$ be an unbiased estimator of $\theta_0$. Then under various smoothness assumptions on $P(X\mid\theta_0)$, we have $$\text{Var}[\hat\theta]\ge \frac{1}{nI(\theta_0)}$$Where $I$ is the Fisher information matrix.
* The Maximum Likelihood Estimator is **asymptotically optimal**. It is consistent, biased at the limit, and achieves the Cramer-Rao lower bound.
### Bias-Variance Tradeoff
* If we are using Mean Squared Error, we can show that for a given estimator or model $$\text{MSE}=\text{Variance}+\text{bias}^2$$
* In terms of modeling tasks, a high variance means that the model is more flexible and can adapt to noise due to the estimator. However, it is also prone to overfitting as it adapts to all patterns
* A high bias means that the model is less prone to noise, and thus it can generalize well. However, it is also not flexible, and if the bias of the model is too far from the true estimate of the parameters, it will underfit.
* Note for classification with $0-1$ loss, this does not hold.
	* For a correct estimate, the bias will be negative, and it pays to decrease the variance.
	* For an incorrect estimate, the bias will be positive, and it pays to increase the variance.
# Empirical Risk Minimization
* We reframe the problem as follows. Let $L(y,\delta(x))$ be a loss function with $y$ being the true response, and $\delta(x)$ the prediction given the input $x$. Thus, we are *predicting observable quantities*
* The **risk** is now defined as $$\begin{split}R(p_\ast,\delta)&=E_{(x,y)\sim p_\ast}\left[L(y,\delta(x)\right] \\ 
  &= \sum_x\sum_yL(y,\delta(x)) p_\ast(x,y)
  \end{split}$$Where $p_\ast$ represents the true distribution approximated by real data through the empirical distribution.
* The **empirical risk** is then defined as $$\begin{split}R_\text{emp}(\mathcal D, \mathcal D) &=R(p_{emp}, \delta) \\ &= \frac{1}{N}\sum_{i=1}^N L(y_i,\delta(x_i))\end{split}$$That is, it is the risk when we use the empirical distribution instead of the true distribution (in other words, average loss over the dataset).
* The goal, then becomes to minimize the empirical risk.
### Regularization
* Minimizing the empirical risk will usually result in overfitting. *This is because of our assumption that the true distribution is equal to the empirical distribution* (which is not necessarily true due to sampling errors)
* Hence we **regularize** by adding a penalty $C$ weighted with $\lambda$ $$R'(\mathcal D, \delta)= R_{\text{emp}} (\mathcal D, \delta) + \lambda C(\delta)$$
### Choosing $\lambda$
* We cannot use the training set to approximate the true risk. 
* We use the **structural risk minimization principle**. Where $$\hat{\lambda}=\underset{\lambda}{\text{argmin}} \ \hat{R}(\hat\delta_\lambda)$$Where $\hat R(\delta)$ is an estimate of the risk.
* We model the uncertainty of our estimates via standard error. The **one-standard error rule** is a heuristic where we choose the simplest model (Occam's razor) that is no more than one standard error from the mean.
#### Cross Validation
* Let
  $N=|\mathcal D|$ be the data number of data cases.
  $\mathcal{D}_k$ be the kth data fold, and all the other data by $\mathcal{D}_{-k}$. 
  $\mathcal{F}$ be a learning algorithm which outputs a parameter vector given a dataset and some model indices (i.e., hyperparameters). $$\hat\theta_m=\mathcal F(\mathcal D,m)$$
  $\mathcal{P}$ be a prediction function that takes an input and a parameter vector and returns a prediction  $$\hat y=\mathcal P(x,\hat\theta)$$The fit predict cycle is denoted as $$f_m(x,\mathcal D)=\mathcal P(x,\mathcal F(\mathcal D, m)))$$
* The $K$-fold CV estimate of the risk is defined as $$R(m,\mathcal D, K)=\frac{1}{N}\sum_{k=1}^N\sum_{i\in \mathcal D_k} L(y_i, \mathcal{P} (x_i, \mathcal F(\mathcal D_{-k}, m)))$$
* We then call the fitting algorithm once per fold. Let $$f^k_m(x)=\mathcal P (x,\mathcal F(\mathcal D_{-k},m)))$$ be the function that was trained on all data except for the test data in fold $k$. The estimate then becomes $$R(m,\mathcal D, K)=\frac{1}{N}\sum_{i=1}^NL(y_i , f_m^{k(i)}(x_i))$$Where $k(i)$ is the fold in which $i$ is used as test data.
* In summary: divide the dataset into $K$ folds, each fold will be used as a validation set for one of $K$ models not trained on this data. 
	* The empirical risk is then the average loss across all $K$ folds.
* If $K=N$, this is **leave one out cross validation**. 

#### Theoretical Upper Bounds
* *Murphy 6.5.1* For any data distribution $p_\ast$, and any dataset $\mathcal{D}$ drawn from $p_\ast$, the probability that our estimate of the error rate will be more than $\varepsilon$ wrong in the worst case, is upper bounded as follows: $$P\left(\max_{h\in\mathcal{H}}|R_{emp}(\mathcal{D},h)-R(p_\ast,h)|>\epsilon\right)\le2 \dim(\mathcal{H})e^{-2|\mathcal{D}|\varepsilon^2}$$Where $\mathcal{H}$ denotes the (finite) hypothesis space so that $\dim(\mathcal H)=|\mathcal{H}|$ 
	* Training error increases with a larger hypothesis space, and decreases with a larger dataset. *This is the key insight of statistical learning theory*. 
	* For infinite dimensional hypothesis spaces, we use the **Vapnik Chervonenkis dimension** in place of $|\mathcal{H}|$
# Pathologies
* Confidence intervals mean we condition on unknown results, rather than on known results. 
* Hypothesis testing means we favor rejecting the null rather than proving the null hypothesis.
* The $p$-value of frequentist statistics is dependent on when we decide to stop collecting samples. 
* Frequentism violates the **likelihood principle**, which says inference should be based on the likelihood of what is observed rather than hypothetical future data. The likelihood principle follows from two principles
	* The **sufficiency principle** - a sufficient statistic should contain all the relevant information about an unknown parameter.
	* **Weak conditionality** - inferences should be based on what happened rather than what might not have happened.
# Links
* [[$Machine Learning - A Probabilistic Perspective by Murphy|Murphy Ch. 6]]