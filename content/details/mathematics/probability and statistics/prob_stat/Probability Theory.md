* Probability can either be interpreted as a *long-run frequency* (Frequentist) or a *measure of belief and uncertainty* (Bayesian)
* **Bayes' Rule** is a good framework for many things. Update conjectures based on supporting evidence that is likely observed.
* The **hyperparameters** of a model refer to the parameters of the distribution of the priors (from a Bayesian Perspective). The hyperparameters encode our beliefs about the distribution.

# Central Limit Theorem 
* *Assumption*: We have $N$ random variables that are independent and identically distributed each with mean $\mu$ and $\sigma^2$.
* The **Central Limit Theorem** states that as $N\to \infty$, then the distribution of the sum approaches the Normal Distribution. 
* Another way to say this is that the sampling distribution tends towards the normal distribution for a large number of samples even if the original variables are not normally distributed.
* The implication is that *analysis using normal distributions are usually sufficient since many distributions tend to this in the limit*.
# Monte Carlo Simulation
* **Monte Carlo** is one approach to approximating a function of a random variable. This is done by approximating the probability distribution of the function by taking many samples and then taking the empirical probability distribution.
* More formally, it approximates 
  $$
  \mathbb{E}[f(x)]=\int f(x)p(x)dx\approx \frac{1}{N}\sum_{n=1}^Sf(x_n)
  $$
  Where $x_n\sim P(X)$. 
* By the Central Limit Theorem, t*he above approximation becomes better with more samples*. This can be quantified using the **standard error** computed as 
  $$
  \sqrt{\frac{\sigma^2}{N}}
  $$
  
# Topics
* [[Fundamental Constructs of Probability Theory]]
* [[Random Variables and Probability Distributions]] 
* [[Probability Distributions Zoo]] - more on probability distributions and what they are measuring
* [[Queueing Theory]]
* [[Measure Theory]] - a more formal treatment of probabilities
* [[Markov Chain]]

# Links
* [[Probability Theory -- Notation Guide]]
* [[Calculus]] - more on calculus, relevant for integrals and derivatives.

* [How To Learn Probability Distributions](https://www.youtube.com/watch?v=mBCiKUzwdMs)
* [[Machine Learning - A Probabilistic Perspective by Murphy|Murphy Ch. 2]]
