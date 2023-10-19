* Probability can either be interpreted as a *long-run frequency* (Frequentist) or a *measure of belief and uncertainty* (Bayesian)
* **Bayes' Rule** is a good framework for many things. Update conjectures based on supporting evidence that is likely observed.
* [Probability Distributions tell a story. Distributions are related to each other in the way they reframe counting samples](https://www.youtube.com/watch?v=mBCiKUzwdMs)
* The **hyperparameters** of a model refer to the parameters of the distribution of the priors (from a Bayesian Perspective). The hyperparameters encode our beliefs about the distribution.
# Probabilities
* All probabilities range from $0$ to $1$.
### Basic Probabilities
* The **Joint Probability** is defined as the probability of two events happening together. $$P(x,y)=P(x\mid y) \cdot P(y)$$
   
  The **Marginal Distribution** is defined as follows: $$P(a)=\sum_{b}P(a \mid b) \cdot P(b)$$
	* This can be extended for continuous variables by evaluating the following integral $$P(a)=\int P(a\mid \theta) \ P(\theta) \ d\theta$$
	* We may interpret the marginal distribution as aggregating all probabilities conditioned on $\theta$. 

* The **Conditional Probability** is defined as the probability of $a$ given $b$ or $$P(a\mid b)=\frac{P(a,b)}{P(b)}$$
	* Conditioning on another variable still gives the same definition as above. That is $$P(a,b\mid c)=P(a\mid b,c)\ P(b\mid c)$$
### Independence
* Two random variables $X,Y$ are **independent** if the joint probability can be written as $$P(A,B)=P(A) \cdot P(B)$$ That is, the two variables do not depend on each other.
* Two random variables $X,Y$ are **conditionally independent** given $Z$ if the conditional joint can be written as a product of conditional marginals, or $$P(X,Y\mid Z)=P(X\mid Z)\ \cdot P(Y \mid Z)$$Alternatively, it can be stated as $$P(X\mid Y,Z)=P(X\mid Z)$$
### Theorems
* The **Chain Rule of Probability** $$P(X_{1},X_2,\dots,X_n)=P(X_1) \cdot P(X_2\mid X_1)\dots P(X_n \mid X_1,X_2,\dots,X_{n-1})$$
* **Bayes' Theorem** is defined as $$P(x\mid y)= \frac{P(x)\ P(y\mid x)}{P(y)}= \frac{P(x)\ P(y\mid x)}{\sum_{x'}P(x') \ P(y\mid x')}$$
	* $P(x)$ is the **prior** 
		* A prior is **informative** if it significantly affects the posterior. It is **uninformative** otherwise.
	* $P(y\mid x)$ is the **likelihood**
	* $P(x\mid y)$ is the **posterior**.
		* We say that the prior is a **conjugate prior** if it is of the same form as the posterior. This is done for *mathematical convenience*.
		* In many cases, it is desirable to have distributions that are amenable to being used as a conjugate prior (i.e., Gaussian, Beta, Inverse Wishart)
	* $P(y)$ is the probability of the **evidence**.
# Central Limit Theorem 
* *Assumption*: We have $N$ random variables that are independent and identically distributed each with mean $\mu$ and $\sigma^2$.
* The **Central Limit Theorem** states that as $N\to \infty$, then the distribution of the sum approaches the Normal Distribution. 
* Another way to say this is that the sampling distribution tends towards the normal distribution for a large number of samples even if the original variables are not normally distributed.
* The implication is that *analysis using normal distributions are usually sufficient since many distributions tend to this in the limit*.
# Monte Carlo Simulation
* **Monte Carlo** is one approach to approximating a function of a random variable. This is done by approximating the probability distribution of the function by taking many samples and then taking the empirical probability distribution.
* More formally, it approximates $$E[f(x)]=\int f(x)p(x)dx\approx \frac{1}{N}\sum_{n=1}^Sf(x_n)$$Where $x_n\sim P(X)$. 
* By the Central Limit Theorem, t*he above approximation becomes better with more samples*. This can be quantified using the **standard error** computed as $$\sqrt{\frac{\sigma^2}{N}}$$
# Topics
* [[Probability Distributions Zoo]] - more on probability distributions and what they are measuring
* [[Random Variables and Probability Distributions]] 
# Links
* [[Calculus]] - more on calculus, relevant for integrals and derivatives.

* [How To Learn Probability Distributions](https://www.youtube.com/watch?v=mBCiKUzwdMs)
* [[Machine Learning - A Probabilistic Perspective by Murphy|Murphy Ch. 2]]
