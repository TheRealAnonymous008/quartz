# Parameters in an MVN
* Assume MVN prior for mean, and Inverse Wishart for covariance. We get multivariate T posterior for mean, and Inverse Wishart posterior for covariance.
* The above assumption shows how using the Inverse Wishart simplifies things because it is a [[Probability|conjugate prior]]

### Defining Conjugate Priors
* *Assume* $x_i\sim \mathcal{N}(\mu,\Sigma)$ and the data $\mathcal{D}$ are complete. 
* *Assume* the likelihood and prior of the distribution of $\mu$ are normally distributed.
  $$
  \begin{split}P(\mathcal{D}\mid \mu)&=\mathcal{N}\left(\bar{x}\mid \mu,\frac{1}{N}\Sigma\right) \\ 
  P(\mu)&= \mathcal{N}(\mu\mid m_0,V_0)
  \end{split}
  $$
  
* We have the following *estimate for the posterior mean*, which is normally distributed
  $$
  \begin{split} 
  P(\mu \mid \mathcal{D}, \Sigma) &= \mathcal{N}(\mu\mid m_N,V _N) \\ 
  V_N^{-1} &= V_0^{-1}+N\Sigma^{-1} \\ 
  m_N &= V_N(\Sigma^{-1} (N\bar{x})+ V_0^{-1}m_0)
  \end{split}
  $$
  
* *Assume* the likelihood and the prior of the covariance matrix are distributed based on the inverse Wishart distribution
  $$
  \begin{split}P(\mathcal{D}\mid\mu, \Sigma) &= \text{IW}(\Sigma \mid S_{\mu}, v_0) \\
  \end{split}
  $$
  
* We have the following *estimate for the posterior covariance* which is also inverse Wishart
  $$
  \begin{split} 
  P(\Sigma \mid \mathcal{D}, \mu) &= \text{IW}(\Sigma\mid S_N, v_N) \\ 
  S_N^{-1} &= S_0 +S_\mu \\ 
  v_N &= v_0 +N
  \end{split}
  $$
  
### MAP Estimation
* The *MAP estimate* is given by
  $$
  \Sigma_{\text{map}}=\frac{S_0+S_\mu}{N_0+N}
  $$
  
* If we have a proper informative prior, we can rewrite the MAP estimate as
  $$
  \Sigma_{\text{map}}=\lambda\Sigma_0+(1-\lambda)\Sigma_{\text{mle}}
  $$
  Where $\lambda=\frac{N_0}{N_0+N}$ controls the **shrinkage** towards the prior
* The prior covariance $\Sigma_0$ is determined using the MLE covariance. In obtaining $\Sigma_{\text{MAP}}$ We shrink off diagonal elements towards $0$. This is **shrinkage estimation** or **regularized estimation**.
	* One benefit of this is that the eigenvalues of the MAP estimate are closer to the true matrix rather than the MLE. However, this does not affect eigenvectors.
### Univariate Posterior
* In the univariate posterior, we *make use of the inverse-chi squared distribution* as our posterior and prior distributions. 
* The posterior becomes
  $$
  \begin{split}P(\sigma^2\mid\mathcal{D},\mu)&= \chi^{-2}(\sigma^2\mid v_N, \sigma^2_N ) \\ 
  v_N &= v_0 + N \\ 
  \sigma^2_N&= \frac{v_0\sigma_0^2+\sum_{i=1}^N(x_i-\mu)^2}{v_n}
  \end{split}
  $$
  
* *Assume* the prior and likelihood follow a [[Probability Distributions Zoo|Normal Inverse Chi Squared]] distribution
  $$
  \text{NI}\chi^2(\mu,\sigma^2\mid m_0,\kappa_0,v_0,\sigma_0^2)=\mathcal{N}\left(\mu\mid m_0,\frac{\sigma^2}{\kappa_0}\right) \times \chi^{-2}(\sigma^2\mid v_0, \sigma_0^2)
  $$
  
* The *posterior is simply the Normal Inverse Chi-Squared distribution with updated parameters* 
  $$
  \begin{split}m_N&=\frac{\kappa_0m_0 +N\bar{x}}{\kappa_N} \\ 
  
  \kappa_N&= \kappa_N+N \\ 
  
  v_N &= v_0 + N \\ 
  v_N\sigma_N^2 &=v_0\sigma_0^2 +\sum_{i=1}^N(x_i-\bar{x})^2+\frac{N\kappa_0}{\kappa_0 + N}(m_0-\bar{x})^2
  \end{split}
  $$
  
* The posterior marginal for $\sigma^2$ follows the Inverse Chi Squared distribution
  $$
  P(\sigma^2\mid\mathcal{D})=\chi^{-2}(\sigma^2\mid v_N,\sigma^2_N)
  $$
  
* The posterior marginal for $\mu$ follows a Student T-distribution
  $$
  P(\mu\mid\mathcal{D})=\mathcal{T}\left(\mu\mid m_N,\frac{\sigma_N^2}{\kappa_N}, v_N\right)
  $$
  
#### Bayesian T-Test
* If we assume an uninformative prior, we get a **derivation for the Student t-test**. We have
  $$
  \begin{split}P(\mu\mid\mathcal{D})&=\mathcal{T}\left(\mu\mid \bar{x}, \frac{s^2}{N}, N-1\right) \\ \text{Var}[\mu\mid\mathcal{D}]&= \frac{s^2}{N}\end{split}
  $$
  Where $s$ is the sample variance.
  
* The test then constitutes computing the probability
  $$
  P(\mu>\mu_0\mid\mathcal{D})=\int_{\mu_0}^\infty P(\mu\mid\mathcal{D}) d\mu
  $$
  We can simplify the posterior further using the **t-statistic** 
  $$
  t=\frac{\bar{x}-\mu}{s/\sqrt{N}}
  $$
  And if $F_v(t)=\mathcal{T}(0,1,v)$, we have
  $$
  P(\mu\mid\mathcal{D})=1-F_{n-1}(t)
  $$
  
* *Note*: Here, we assume that $\bar{x}$ is known, and parameter $\mu$ is unknown. The frequentist approach reverses the roles.
### Multivariate Posterior
* *Assume* the prior follows a [[Probability Distributions Zoo|Normal Inverse Wishart]]distribution 
  $$
  P(\mu,\Sigma)=\text{NIW}(\mu,\Sigma\mid m_0,\kappa_0, v_0, S_0)
  $$
  
* *Assume* the likelihood is given by
  $$
  P(\mathcal{D}\mid \mu,\Sigma)= (2\pi)^{-ND/2}|\Sigma|^{-N/2}\exp\left(-\frac{N}{2}(\mu-\bar{x})\Sigma^{-1}(\mu-\bar{x})\right)\exp\left(-\frac{N}{2}\text{tr}(\Sigma^{-1}S_{\bar{x}})\right)
  $$
  Which is simply the product of the Gaussian and the Inverse-Wishart.
* *The posterior is simply the Normal-Inverse-Wishart distribution with updated parameters*.
  $$
  \begin{split}
  m_N&=\frac{\kappa_0}{\kappa_0+N}m_0+\frac{N}{\kappa_0+N}\bar{x} \\ 
  
  \kappa_N&= \kappa_N+N \\ 
  
  v_N &= v_0 + N \\ 
  
  S_N &= S_0  + S_{\bar{x}} +\frac{\kappa_0N}{\kappa_0+N}(\bar{x} -m_0)(\bar{x}-m_0)^T \\ 
  &= S_0+S+\kappa_0m_0m_0^T-\kappa_Nm_Nm_N^T \\ 
  
  S&= \sum_{i=1}^Nx_ix_i^T
  \end{split}
  $$
  
* The posterior marginal for $\Sigma$ follows the Inverse Wishart distribution.
  $$
  P(\Sigma\mid\mathcal{D})=\text{IW}(\Sigma\mid S_N,v_N)
  $$
  
* The posterior marginal for $\mu$ follows a multivariate Student T distribution 
  $$
  P(\mu\mid \mathcal{D})= \mathcal{T}\left(\mu\mid m_N,\frac{1}{\kappa_N(v_N-D+1)S_N}, v_N-D+1\right)
  $$
  
* The posterior predictive is given by a Student-T distribution
  $$
  P\left(x\mid\mathcal{D})=\mathcal{T}(x\mid m_N,\frac{\kappa_N+1}{\kappa_N(v_N-D+1)}S_N,v_N-D+1\right)
  $$
  
# Links
* [[Machine Learning - A Probabilistic Perspective by Murphy|Murphy Ch. 4.6]]
* [[Gaussian Models]] - more on Gaussian models
* [[Probability Distributions Zoo]] - more on the Gaussian, Wishart, and Inverse Wishart. 