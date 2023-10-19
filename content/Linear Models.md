# Linear Regression
$$E=mc^2$$
## Specifications
* It is a model of the form $$P(y\mid x,\theta)=\mathcal{N}(y\mid w^Tx,\sigma^2)$$Or in another form, we have Gaussian noise $\epsilon$ such that $$y=w^Tx+\epsilon$$
* Under the assumption of iid, by *minimizing the negative log likelihood* and using the [[Probability Distributions Zoo|MVN]] formula, we have a loss function specified by the **residual sum of squares**. $$\text{RSS}(w)=\sum_i^N(y_i-w^Tx)^2=\sum_i^N\epsilon_i^2$$
	* This loss function is convex.
	* We may obtain a solution using the following **normal equation** $$\hat w=(X^TX)^{-1}X^T y$$Under the assumption of invertibility of $X^TX$, where $X$ is the design matrix.
* *Geometrically*: The goal is to find the best fit line in the feature space such that the sum of the residual is minimized.
## Extensions
* We may extend this by changing $x$ with the **basis function expansion** $\phi(x)$ to allow for non-linear features.  $$y=w^T\phi(x)+\epsilon$$
* We may have **robust regression** if the data has many outliers. Here, we replace the distribution of $\epsilon$ to *use a heavy-tailed distribution* such as the Laplace or the Student T-distribution.
	* For a Laplace likelihood, we may choose to minimize the Negative Log Likelihood via Linear Programming. Alternatively, we may use the **Huber Loss** $$\begin{equation}
	  \begin{split}
	  L_H(r,\delta)= \begin{cases}
	  r^2/2 & \text{if } |r|\le 0 \\
	  \delta|r|-\delta^2/2 & \text{if } |r| > 0
	  \end{cases}
	  \end{split}
	  \end{equation}$$
		* The Huber Loss is equivalent to the $L_2$ loss but accounts for outliers in the data.
### Regression
* Regression essentially involves *controlling the distribution of weights* such that the weights end up being "simple" 
* We may use **Ridge Regression** or **weight decay** by using a [[Bayesian Models|Maximum A Posteriori]] estimate with a Gaussian Prior. That is, we have that $$P(w)=\prod_j\mathcal{N}(w_j\mid 0,\tau^2)$$Where $1/r^2$ controls the strength of the prior.
	* The corresponding solution is given as $$w_\text{ridge}=(\lambda I_D +X^TX)^{-1}X^Ty $$Where $\lambda = \sigma^2/\tau^2$. $\sigma^2$ is given by the variance of Gaussian Noise $\epsilon$ (see above). 
	* This also tends to be easier to fit numerically *using a QR decomposition* on a design matrix augmented with the Cholesky decomposition of the precision matrix $\Gamma = 1/\tau^2 I_D$ (see [[$Machine Learning - A Probabilistic Perspective by Murphy|Murphy 7.5.2]])
		* When the dimensions is greater than the number of samples ($D\gg N$), we can perform SVD first for dimensionality reduction.
	* Ridge Regression aims to shrink the principal components with the smallest singular values (and thus have the highest posterior variance. See [[$Machine Learning - A Probabilistic Perspective by Murphy|Murphy 7.5.3]]). 
	* *Ill-determined parameters are reduced towards $0$ through **shrinkage***. 
* We can also use **Principal Components Regression** by applying regression on the principal components. However, this is not as effective as Ridge Regression since it ignores dimensions entirely (compared to Ridge Regression's softening).
### Bayesian Regression
* We may apply [[Bayesian Statistics|Bayesian statistics]] to compute for a posterior distribution of weights and obtain a MAP estimate as follows: $$\hat{w}_\text{MAP}=\underset{w}{\text{argmax}}  \ P(w\mid \mathcal D)= \underset{w}{\text{argmax}} \ P(\mathcal D\mid w)  \ P(w)$$We may then sequentially update the parameters in a Bayesian manner. 

* The effect is the same as that of [Regularization](https://www.youtube.com/watch?v=Z6HGJMUakmc) depending on the choice of prior.
* With a Gaussian prior and Gaussian likelihood, we get a Gaussian posterior with variance as $$\sigma^2_N = \sigma^2+x^TV_Nx$$Where $\sigma^2$ is the variance of the observation noise, and $V_N$ is the variance in the parameters (i.e., how close $x$ is to the training data). *This captures uncertainty as we move away from the training data, allowing the model to capture what is known and what is unknown*.
	* We are unable to capture this kind of uncertainty using a plugin approximation (i.e., MAP) means 

* With unknown variance, and likelihood $$P(y\mid X, w,\sigma^2)=\mathcal N (y\mid Xw,\sigma^2I_n)$$the posterior and the conjugate prior of the joint parameter distribution $P(w,\sigma^2)$ follow a [[Probability Distributions Zoo|Normal Inverse Gaussian]] distribution. (see more at [[$Machine Learning - A Probabilistic Perspective by Murphy|Murphy Ch. 7.6.3]]) 
	* The posterior variance is given by the Wald Distribution
	* The posterior weights follow a T distribution.
	* The posterior predictive distribution $P(\hat y \mid \hat X, \mathcal{D})$ also follows a T distribution
	* We may use a **g-prior** of the form $$\text{NIG}(w,\sigma^2\mid w_0,g(X^TX)^{-1}, 0,0)$$Where $g$ controls the strength of the prior (and has a regularization effect), and we scale on $(X^TX)^{-1}$ so that the posterior is invariant to input scaling.
		* Using a g-prior with $g=N$, where $N$ is the number of samples gives the **unit information prior** which contains as much information as one sample.

* Assuming unknown priors, we can use [[Bayesian Statistics|empirical Bayes]] as an alternative to cross-validation. The goal is to maximize the marginal likelihood by choosing an appropriate $\eta=(\alpha,\lambda)$. $$P(\mathcal{D}\mid m) = \iint P(\mathcal D\mid w,m) \ P(w\mid m,\eta) \ P(\eta\mid m) \ dw d\eta$$

# Logistic Regression

# Links
* [[$Machine Learning - A Probabilistic Perspective by Murphy|Murphy Ch. 7 - 9]]
	* Ch. 7 - Linear Regression, Robust Regression, Ridge Regression, Bayesian Linear Regression.
* [[$Dive into Deep Learning by Zhang, Lipton, Li and Smola|Zhang et. al Ch. 3]] - more on Linear Regression

* [Bayesian Linear Regression: Data Science Concepts](https://www.youtube.com/watch?v=Z6HGJMUakmc)