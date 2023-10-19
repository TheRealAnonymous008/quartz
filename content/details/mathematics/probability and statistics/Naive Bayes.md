* The goal is to classify vectors of discrete-valued features via a generative approach. That is $$P(y\mid x,\theta)=P(x\mid y,\theta) \ P(y\mid \theta)$$ Let $x^{(i)}\in\mathbb{R}^D$. We define a **generative classifier** using the following equation $$P(y=c\mid x,\theta)=\frac{P(y=c\mid\theta) \ P(x\mid y=c,\theta)}{\sum_{c'} P(y=c'\mid\theta) \ P(x\mid y=c',\theta)}$$
	* We refer to $P(x\mid y=c)$ as the **class conditional density**  (that is, the *likelihood of generating $x$ given $y=c$*.
	* We refer to $P(y=c\mid\theta)$ as the **class prior** The class prior is usually denoted as $\pi_c$.  So $$\pi_c=P(y=c\mid \theta)$$It captures the *prior assumptions about the label distribution*.

* *Assume*: The features are conditionally independent (this is technically a naive assumption). That is, $$P(x\mid y=c, \theta)=\prod_{j=1}^DP(x_j\mid y=c,\theta_{jc})$$Where $c\in C$ is the value of the label $y$.
  Note that the distributions in the RHS can be substituted to whatever we want (i.e., a Gaussian or a Bernoulli).
* We estimate $\hat{\theta}$ from the dataset $\mathcal{D}$. Then, given $x$, compute $$\hat{y}=\underset{c\in C}{\text{argmax}} \ P(y\mid x,\hat{\theta}) = \underset{c\in C}{\text{argmax}} \ P(x\mid y,\hat{\theta}) \ P(y\mid\hat\theta)$$
# Bayesian Naive Bayes
 * The Prior becomes: $$P(\theta)=P(\pi)\prod_{j=1}^D\prod_{c=1}^DP(\theta_{jc})$$
  This follows from the rule of product. 

* Correspondingly, the posterior becomes $$P(\theta\mid\mathcal{D})=P(\pi\mid\mathcal{D})\prod_{j=1}^D\prod_{c=1}^DP(\theta_{jc}\mid\mathcal{D})$$Where $\pi$ is a  parameter for the distribution of $y$.
	
	Also, the conditionals on the RHS are determined as needed (i.e., they can be Dirichlet or Beta, for example).
  
  *It is of the same form as the prior, except conditioned based on evidence seen from the dataset*. 

* We can analyze the likelihood as follows:  For a single datapoint, $$P(x^{(i)},y^{(i)}\mid \theta)=P(y^{(i)} \mid \pi)  \prod P(x_{j}^{(i)}\mid\theta_j)$$ We also have $$\log{P(\mathcal{D}\mid \theta)=\sum_{c=1}^C \big( N_c\log{\pi_c}}+\sum_{j=1}^D\sum_{c\in C}\sum_{y_i=c} \log{P(x_{j}^{(i)}\mid \theta_{jc})}\big)$$
* At testing, the goal is $$P(y=c\mid x, \mathcal{D})\propto P(y=c\mid \mathcal{D})\prod_{j=1}^DP(x_j\mid y=c,\mathcal{D})$$Note that to actually compute the above in a Bayesian Manner, we must integrate over $\pi$ and $\theta$ to get the marginal distribution: $$\left[ \int P(y=c\mid \mathcal{D}) \ P(\pi\mid\mathcal{D}) \ d\pi \right] \prod_{j=1}^D \left[\int P(x_j\mid y=c,\mathcal{D}) \ P(\theta_{jc}\mid \mathcal{D}) \ d\theta_{jc}\right]$$
# Filtering
* Since we assume the features are conditionally independent, we need to choose the appropriate features. 
* One way to select the features is through **variable filtering**, that is by taking the top $K$ features that are relevant for the problem.
* One way to do this is to measure the mutual information  between feature $X_j$ and label $Y$.
# Links
* [[Machine Learning - A Probabilistic Perspective by Murphy|Murphy Ch. 3.5]]