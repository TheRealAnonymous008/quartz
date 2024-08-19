* All probabilities range from $0$ to $1$.

# Probabilities on Two Events
* The **Joint Probability** is defined as the probability of two events happening together.
  $$
  P(x,y)=P(x\mid y) \cdot P(y)
  $$
  
   
  The **Marginal Distribution** is defined as follows:
  $$
  P(a)=\sum_{b}P(a \mid b) \cdot P(b)
  $$
  
	* This can be extended for continuous variables by evaluating the following integral
	  $$
	  P(a)=\int P(a\mid \theta) \ P(\theta) \ d\theta
	  $$
	  
	* We may interpret the marginal distribution as aggregating all probabilities conditioned on $\theta$. 

* The **Conditional Probability** is defined as the probability of $a$ given $b$ or 
  $$
  P(a\mid b)=\frac{P(a,b)}{P(b)}
  $$
  
	* Conditioning on another variable still gives the same definition as above. That is
	  $$
	  P(a,b\mid c)=P(a\mid b,c)\ P(b\mid c)
	  $$
	  
#  Independence
* Two [[Random Variables and Probability Distributions|random variables]] $X,Y$ are **independent** if the joint probability can be written as 
  $$
  P(A,B)=P(A) \cdot P(B)
  $$
   That is, the two variables do not depend on each other.
* Two random variables $X,Y$ are **conditionally independent** given $Z$ if the conditional joint can be written as a product of conditional marginals, or 
  $$
  P(X,Y\mid Z)=P(X\mid Z)\ \cdot P(Y \mid Z)
  $$
  Alternatively, it can be stated as 
  $$
  P(X\mid Y,Z)=P(X\mid Z)
  $$
  
# Theorems
* The **Chain Rule of Probability**
  $$
  P(X_{1},X_2,\dots,X_n)=P(X_1) \cdot P(X_2\mid X_1)\dots P(X_n \mid X_1,X_2,\dots,X_{n-1})
  $$
  
* **Bayes' Theorem** is defined as 
  $$
  P(x\mid y)= \frac{P(x)\ P(y\mid x)}{P(y)}= \frac{P(x)\ P(y\mid x)}{\sum_{x'}P(x') \ P(y\mid x')}
  $$
  
	* $P(x)$ is the **prior** 
		* A prior is **informative** if it significantly affects the posterior. It is **uninformative** otherwise.
	* $P(y\mid x)$ is the **likelihood**
	* $P(x\mid y)$ is the **posterior**.
		* We say that the prior is a **conjugate prior** if it is of the same form as the posterior. This is done for *mathematical convenience*.
		* In many cases, it is desirable to have distributions that are amenable to being used as a conjugate prior (i.e., Gaussian, Beta, Inverse Wishart)
	* $P(y)$ is the probability of the **evidence**.

* **Boole's Inequality** or the **Union Bound**. Let $A_1,\dots$ be a countable set of events. We have that
  $$
  P\left(\bigcup_{i=1}^\infty A_i\right)\le \sum_{i=1}^\infty P(A_i)
  $$
  
# Links
* [[Machine Learning - A Probabilistic Perspective by Murphy|Murphy Ch. 2]]