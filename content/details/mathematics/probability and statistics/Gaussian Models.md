# Basics
* *Murphy 4.1.1.*: If we have $N$ iid samples $x_i\sim\mathcal{N}(\mu,\Sigma)$, then the MLE for the parameters is given by the sample mean and covariances. That is 
  $$
  \begin{split}\hat{\mu}_\text{MLE}&=\frac{1}{N}\sum_{i=1}^Nx_i &= \bar{x}\\
  
  \hat{\Sigma}_\text{MLE} &=\frac{1}{N}\sum_{i=1}^N(x_i-\bar{x})(x_i-\bar{x})^T
  
  \end{split}
  $$
  
	* By the Central Limit Theorem, this implies that with more samples, the sampling mean and covariance become better estimates for the true mean and covariance.

* The Gaussian is widely used in modelling since it is *the distribution with the maximum entropy subject having to having a specified mean and covariance*. 
	* *Murphy 4.1.2*. Let $q(x)$ be any density satisfying 
	  $$
	  \int q(x)x_ix_j=\Sigma_{ij}
	  $$
	  Let $p=\mathbb{N}(0,\Sigma)$. Then 
	  $$
	  H(q)\le H(p)
	  $$
	  
* When the covariance matrix is unknown, but the underlying distribution is known to be Gaussian, *we may use the [[Probability Distributions Zoo|Inverse Wishart distribution]] to approximate the covariance matrix.*.
	* The corresponding conjugate prior would be the inverse Wishart as well.
	* For the precision matrix, we can simply use the Wishart distribution.
# Gaussian Discriminant Analysis
* **Gaussian Discriminant Analysis** is a generalization of the [[Naive Bayes]] classifier. It involves the following 
  $$
  P(x\mid y=c,\theta)=\mathcal{N}(x\mid\mu_c, \Sigma_c)
  $$
  
	* It becomes the Naive Bayes classifier if $\Sigma_c$ is diagonal since this implies feature independence.
	* Its MLE for the mean and covariance matrix is equal to the sample mean and covariances for each class (see [[Machine Learning - A Probabilistic Perspective by Murphy|Murphy 4.2.4]])

* The **Nearest Centroids Classifier** is defined as follows: 
  $$
  \hat{y}(x)=\underset{c}{\text{argmax}}(\log{P(y=c\mid\pi ) + \log{P(x\mid\theta_c)}})
  $$
  
* **Quadratic Discriminant Analysis (QDA)** involves using the definition of Gaussian density for the posterior of class labels $P(y=c\mid x,\theta)$. That is 
  $$
  P(y=c\mid x,\theta)=\frac{\pi_c|2\pi\Sigma_c|^{-\frac{1}{2}}\exp\left[-\frac{1}{2}(x-\mu_c)^T\Sigma_c^{-1}(x-\mu_c)\right]}{\sum_{i}\pi_i|2\pi\Sigma_i|^{-\frac{1}{2}}\exp\left[-\frac{1}{2}(x-\mu_i)^T\Sigma_i^{-1}(x-\mu_i)\right]}
  $$
  
	* Notably, we assume that the class conditional densities $P(x\mid y=c,\theta)$ follow Gaussian distributions.
	* The decision boundaries using logs of probabilities follow quadratic curves. 
	* The **discriminant** comes from taking the log of the probability 
	  $$
	  \delta_c(x)=\log\pi_c-\frac{1}{2}\log\left(|\Sigma_c|\right) - \left[\frac{1}{2}(x-\mu_c)^T\Sigma_c^{-1}(x-\mu_c)\right]
	  $$
	  Observe the quadratic form.

* In **Linear Discriminant Analysis (LDA)** simplifies QDA as follows: 
  $$
  \begin{split}
  P(y=c\mid x,\theta)&=\text{softmax}(\eta)_c \\
  \eta &= 
	  \begin{bmatrix} \beta^T_1x+\gamma_1 
	  \\ \vdots \\ 
	  \beta^T_C+\gamma_C
	  \end{bmatrix}\\
  \beta_c &= \Sigma^{-1}\mu_c \\ 
  \gamma_c &= -\frac{1}{2}\mu^T_c \Sigma^{-1}\mu_c+\log{\pi_c}
  \end{split}
  $$
  
	* Considering logs of probabilities gives us linear decision boundaries.
	* LDA is a dimensionality reduction process which aims to maximize the distance between predicted means and minimize variance within each class distribution. That is, it *maximizes separability of data*.

* One way to fit discriminant analysis to data is to use the MLE estimate, However, this is prone to overfitting. This can be mitigated in the following ways:
	* Use a diagonal $\Sigma$, equivalent to Naive Bayes.
	* Use parameter sharing, have $\Sigma_c=\Sigma$ for all classes $c$, equivalent to LDA
	* Use diagonal covariance LDA
	* Impose a prior and integrate it out. 
	* Use MAP estimates
	* Dimensionality Reduction

* **Regularized LDA** involves the addition of a regularization term making use of the *Wishart Prior* so that the new regularized covariance matrix $\hat{\Sigma}$ is given by 
  $$
  \hat{\Sigma}=\lambda \cdot \text{diag}(\hat{\Sigma}_{\text{MLE}}) +(1-\lambda)\cdot \hat{\Sigma}_{\text{MLE}}
  $$
  Where $\text{diag}$ denotes taking all the diagonal entries and $\lambda$ is the **regularization parameter**. 
	* $\lambda$ is directly proportional to the strength of the Wishart prior used. 
	* The MLE for highly dimensional data can be computed by using Singular Value Decomposition and making use of the empirical covariance matrices instead.

* **Diagonal LDA** involves using a diagonal covariance matrix for each $\Sigma_c$. 
	* This is equivalent to Regularized LDA with $\lambda = 1$.
	* We classify based on the following rule 
	  $$
	  \log P(x,y=c\mid \theta)=-\sum_{j=1}^D \frac{(x_j-\mu_{cj})^2}{2\sigma^2_j}+\log\pi_c
	  $$
	  Where we set $\mu_{cj}=\overline{x}_{cj}$ as the sample mean of the $j$-th feature for data in the $c$ class.
	  
	  $\sigma_j^2$ is set using the pooled empirical variance calculated by 
	  $$
	  \sigma_j^2=\frac{\sum_{c=1}^C\sum_{y_i=c}(x_{cj}-\overline{x}_{cj})^2}{N-C}
	  $$
	  
# Gaussian Inferencing
* *Murphy 4.3.1* Suppose $x=\begin{bmatrix}  x_1 \\ x_2 \end{bmatrix}$ is jointly Gaussian with parameters 
  $$
  \begin{split} \mu&=\begin{bmatrix}  \mu_1 \\ \mu_2 \end{bmatrix} \\ 
  
  \Sigma &= \begin{bmatrix}  \Sigma_{11} & \Sigma_{12}  \\ 
  \Sigma_{21} & \Sigma_{22}
   \end{bmatrix} \\ 
   
   \Lambda = \Sigma^{-1}&= \begin{bmatrix}  \Lambda_{11} & \Lambda_{12}  \\ 
  \Lambda_{21} & \Lambda_{22}
   \end{bmatrix}
  
  \end{split}
  $$
  Then the marginals are given by 
  $$
  \begin{split} P(x_1)&=\mathcal{N}(x_1\mid \mu_1,\Sigma_{11}) \\ 
  P(x_2) &= \mathcal{N}(x_2\mid \mu_1,\Sigma_{22})
   \end{split}
   $$
   And the conditional is given by 
   $$
   \begin{split} P(x_1\mid x_2)&=\mathcal{N}(x_1\mid \mu_{1\mid 2},\Sigma_{1\mid 2}) \\ 
   
  \mu_{1\mid 2} &= \mu_1 + \Sigma_{12}\Sigma_{22}^{-1} (x_2-\mu_2) \\
  &= \mu_1-\Lambda_{11}^{-1}\Lambda_{12}(x_2-\mu_2) \\
  &= \Sigma_{1\mid 2} (\Lambda_{11}\mu_1-\Lambda_{12}(x_2-\mu_2)) \\ 
  
  \Sigma_{1\mid2} &= \Sigma_{11}-\Sigma_{12}\Sigma_{22}^{-1}\Sigma_{21} \\ &=\Lambda_{11}^{-1}
   \end{split}
   $$
   
# Gaussian Interpolation
* The Gaussian part of this comes from the assumption outlined in its prior. *Each entry is the average of its neighbors plus Gaussian noise.*
### Noise-Free Observations
* Problem: We estimate a 1-D function on the interval $[0,T]$ such that $y_i=f(t_i)$ for $N$ observed points $t_i$
* *Assume*: For the points between observations, the function is smooth.
* Start by discretizing. Define 
  $$
  \begin{split}x_j &= f(s_j) \\ s_j &= jh \\ 
  h &=\frac{T}{D} & 1\le j\le D
  \end{split}
  $$
  That is, take evenly spaced samples in the desired interval.
* *Prior*: Assume that each $x_j$ is the average of its neighbors plus Gaussian noise 
  $$
  \begin{split} x_j&=\frac{1}{2}(x_{j-1}+x_{j+1})+\epsilon_j \\ \epsilon_j&\sim\mathcal{N}(0,(1/\lambda)I) \end{split}
  $$
  $\lambda$ controls how much it is believed that the function is smooth (higher = smoother)
  
  This can be encoded in a matrix $L$ so that 
  $$
  P(x)=\mathcal{N}(x\mid 0,(\lambda^2L^TL)^{-1})\propto \exp\left(-\frac{\lambda^2}{2}||Lx||^2_2\right)
  $$
  Assume scaling by $\lambda$. Let 
  $$
  \Lambda=L^TL
  $$
  
* Let $x_2$ be the $N$ noise free observations and 
  
  $x_1$ be the $D-N$ unknowns. 
  
  Partition $L=[L_1, L_2]$ accordingly. Partition $\Lambda$ accordingly as well into a $2\times 2$ block matrix. 
  
  The conditional now becomes 
  $$
  \begin{split} P(x_1\mid x_2)&=\mathcal{N}(\mu_{1\mid 2}, \Sigma_{1\mid 2}) \\
  \mu_{1\mid2} &= -L_1^TL_2 x_2 &= -\Lambda_{11}^{-1}\Lambda_{12}x_2 \\ \Sigma_{1\mid2} &= \Lambda_{11}^{-1} \end{split}
  $$
  
* For noiseless data, $\lambda$ has no effect on the smoothness of the posterior mean estimate.
* *We can treat each data point as being some random variable*. Imputation can be done by computing for a marginal distribution conditioned on the known variables.
### Noisy Data
* In addition to the above, assume further that $y=Ax+\epsilon$, where $\epsilon\sim\mathcal{N}(0,\Sigma_y)$, and $\Sigma_y=\sigma^2I$, with signal noise $\sigma$, and $A$ is an appropriately sized projection matrix that selects out observed elements.
* *The estimation is similar to that for noiseless data.*
* A strong prior determined by large $\lambda$ causes smooth estimates and small uncertainty.
* A weak prior determined by small $\lambda$ causes rougher estimates and high uncertainty. 
* The posterior mean is given by solving the following optimization problem in a process called **Tikhonov Regularization (aka Ridge / L2 Regression)
  $$
  \underset{f}{\text{min}}\frac{1}{\sigma^2}\int(f(t)-y(t))^2dt +\frac{\lambda}{2}\int[f'(t)]^2dt
  $$
  
* Observe, *the above simply involves adding the loss (MSE) with a penalty term for the roughness of the estimate*. The second term is the regularization term
# Information Form
* Let $x\sim \mathcal{N}(\mu, \Sigma)$. We have that $E[x]=\mu$ and $\text{Cov}[x]=\Sigma$. These are the **moment parameters** of the distribution.
* The **canonical parameters** are 
  $$
  \begin{split} \Lambda&=\Sigma^{-1} \\ \xi &= \Sigma^{-1}\mu \end{split}
  $$
  
* The MVN in **information form** is defined as 
  $$
  \mathcal{N}_c(x\mid\xi,\Lambda)=(2\pi)^{D-2}|\Lambda|^{\frac{1}{2}}\exp\left[-\frac{1}{2}(x^T\Lambda x+\xi^T\Lambda^{-1}\xi -2x^T\xi)\right]
  $$
  
* Marginalization is easier in moment form, and conditioning is easier in information form 
  $$
  \begin{split}P(x_2)&=\mathcal{N}_c(x_2\mid \xi_2-\Lambda_{21}\Lambda_{11}^{-1} \xi_1, \ & \ \Lambda_{22}-\Lambda_{22}\Lambda^{-1}_{11}\Lambda_{12}) \\ 
  P(x_1\mid x_2) &= \mathcal{N}_c(x_1\mid \xi_1-\Lambda_{12}x_2, & \Lambda_{11})
  \end{split}
  $$
  
* In Canonical form, multiplication of two Gaussians is easy 
  $$
  \mathcal{N}_c(\xi_f,\Lambda_f) \cdot\mathcal{N}_c(\xi_g,\Lambda_g)=\mathcal{N}_c(\xi_f+\xi_g,\Lambda_f + \Lambda_g)
  $$
  
# Linear Gaussian Systems
* Let $x\in\mathbb{R}^{D_x}, y\in\mathbb{R}^{D_y}$, where $y$ is a noisy observation of $x$. 
  $$
  \begin{split}P(x)&=\mathcal{N}(x\mid\mu_x, \Sigma_x) \\ P(y\mid x)&= \mathcal{N}(y\mid Ax+b, \Sigma_y)\end{split}
  $$
  Where $A$ is a $D_y\times D_x$ matrix. This is a **linear Gaussian system**, represented by $x\to y$. 
* *Murphy 4.4.1* (Bayes rule for linear Gaussian systems). Given a linear Gaussian system, the posterior $P(x\mid y)$ is given by 
  $$
  \begin{split}P(x\mid y)&=\mathcal{N}(x\mid\mu_{x\mid y}, \Sigma_{x\mid y}) \\ \Sigma _{x\mid y}^{-1}&= \Sigma_x^{-1} +A^T\Sigma_y^{-1} A \\ 
  \mu_{x\mid y} &= \Sigma_{x\mid y}\left[A^T\Sigma_y^{-1} (y-b)+\Sigma_{x}^{-1} \mu_x\right] \\ 
  P(y) &= \mathcal{N}(y\mid A\mu_x+b,\Sigma_y+A\Sigma_xA^T)
  \end{split}
  $$
  
  ### Likelihood-Prior Tradeoff
  * Suppose we have $N$ noisy measurements $y_i$ of some underlying quantity $x$. Suppose, the measurement noise has fixed precision, $\lambda_y=1/\sigma^2$. The likelihood is 
    $$
    P(y_i\mid x)=\mathcal{N}(y_i\mid x,\lambda_y^{-1})
    $$
    The prior is 
    $$
    P(x)=\mathcal{N}(x\mid\mu_0,\lambda_0^{-1})
    $$
    Now, we compute the posterior, assuming each feature is independent ($\Sigma_y^{-1}=\text{diag}(\lambda_y I)$) We have that for $P(x\mid y)$, it is normally distributed with the covariance $\lambda_N^{-1}$ and mean $\mu_N$ 
    $$\begin{split}\lambda_N&=\lambda_0+N\lambda_y \\ 
    \mu&= \frac{N\lambda_y \bar{y} +\lambda_0\mu_0}{\lambda_N}
    \end{split}
    $$
    
    That is, the posterior mean is a compromise between the MLE and the prior. The **signal strength** is determined by $\lambda_0/\lambda_y$, and it gives more weight to the prior.
* We can also analyze *updating the posterior sequentially*. Let $\Sigma_y, \Sigma_0, \Sigma_1$ be the variances of the likelihood, prior, and posterior respectively. Then the updated posterior will have 
  $$
  \Sigma_1=\left(\frac{1}{\Sigma_0}+\frac{1}{\Sigma_y}\right)
  $$
  The posterior mean will become 
  $$
  \begin{split}\mu_1&= \frac{\Sigma_y}{\Sigma_y+\Sigma_0}\mu_0 + \frac{\Sigma_y}{\Sigma_y+\Sigma_0}y \ & \ (\text{conves combination between prior and data}) \\ 
  
  &= \mu_0+(y-\mu_0)\frac{\Sigma_y}{\Sigma_y+\Sigma_0} \ & \ (\text{prior adjusted towards data}) \\ 
  
  &= y-(y-\mu_0)\frac{\Sigma_y}{\Sigma_y+\Sigma_0} \ & \ (\text{data adjusted towards prior mean})
  \end{split}
  $$
  The third quantity above is called **shrinkage**. It is the reduction in the effects of sampling variation.
* The shrinkage can be quantified using the **signal-to-noise** ratio, wherein 
  $$
  \text{SNR}= \frac{E[X^2]}{E[\epsilon^2]} = \frac{\Sigma_0 +\mu_0^2}{\Sigma_y}
  $$
  Where 
	* $x\sim \mathcal{N}(\mu_0,\Sigma_0)$ is the true signal, and 
	* $y=x+\epsilon$ is the observed signal, where 
	* $\epsilon\sim\mathcal{N}(0,\Sigma_y)$
# Links
* [[Machine Learning - A Probabilistic Perspective by Murphy|Murphy Ch. 4]]
	* [Theorem 4.1.2 quadratic form](https://stats.stackexchange.com/questions/194051/prove-that-the-maximum-entropy-distribution-with-a-fixed-covariance-matrix-is-a)
	* 4.2 - more on QDA and LDA

* [[Statistical Models]]
* [[Probability Distributions Zoo]] - More on the Multivariate Gaussian Distribution
* [[Information Theory]] - more on entropy.