* The study of efficient data compression, and robust and reliable data transmission.
# Important Quantities
* Let $p$ be a probability distribution. The **entropy** is defined as 
  $$
  H(p)=-\sum_{j}p(j)\ \log{p(j)}
  $$
  
	* It can be interpreted as the *expected amount of surprise* that we may have about a given event. That is, it is the expected amount of information we can gain from the distribution. 
	* This also corresponds to the degree in which the distribution is Uniform.
	* This also corresponds with the amount of uncertainty that we may have about the distribution.

* Let $p$ and $q$ be probability distributions. The **cross entropy** is defined as 
  $$
  H(p,q)=-\sum_{k}p(k) \log{q(k)}
  $$
	* It is a measure of the average number of bits needed to identify an event drawn from the set if a coding scheme used for the set is optimized for an estimated probability distribution $q$ rather than the true distribution $p$.

* The **Kullback-Leibler Divergence** is defined as
  $$
  \text{KL}(p\mid\mid q)=\sum_{x}p(x)\log\frac{p(x)}{q(x)}
  $$
	* It measures the coding inefficiency from using a model $q$ to compress the data, when the true distribution is $p$. 
	* It also measures the dissimilarity between $p$ and $q$
	* It can also be formulated as: 
	  $$
	  \text{KL}(p\mid\mid q)=H(p,q)-H(p)
	  $$
	  Formulated this way, the KL divergence is the average number of extra bits needed to encode the data due to the fact we used distribution $q$ rather than the true distribution $p$.
		* This formulation informally motivates the following inequality 
		  $$
		  \text{KL}(p\mid\mid q) \ge 0, \ \ \  \ \ \text{KL}(p\mid\mid q)=0\iff p=q
		  $$
		  
* The **conditional entropy** is defined as 
  $$
  H(Y\mid X)=\sum_{x}p(x) \ H(Y|X=x)
  $$
  
	* It measures how much entropy $Y$ has remaining given we have learnt the value of $X$.


* The **Pointwise Mutual Information** between two events $x$ and $y$ is defined as 
  $$
  \text{PMI}(x,y)=\log\frac{p(x,y)}{p(x) \ p(y)}=\log \frac{p(x\mid y)}{p(x)}=\log \frac{p(y\mid x )}{p(y)}
  $$
  
	* It measures the discrepancy between these occurring together compared to what would be expected by chance.
	* It is also the amount we learn from updating a [[Bayesian Statistics|prior]] into a posterior.

* The **Mutual Information** determines how similar the joint distribution $p(X,Y)$ is to the factored distribution $p(X)p(Y)$. It is defined, therefore as 
  $$
  I(X;Y)=\text{KL}(p(X,Y) \mid\mid p(X)p(Y)) =\sum_{x}\sum_{y}p(x,y)\log{\frac{p(x,y)}{p(x)p(y)}}
  $$
  
	* This determines how much information can be extracted about one random variable given observations on another.
	* It can also be expressed as 
	  $$
	  I(X;Y)=H(X)-H(X\mid Y)=H(Y)-H(Y\mid X)
	  $$
	* It can also be expressed as the expected value of the pointwise mutual information.
	* For continuous random variables, the mutual random variable can be approximated using the **Maximal Information Coefficient**. We define 
	  $$
	  m(x,y)=\frac{\max_{G\in \mathcal{G}(x,y)}  I(X(G);Y(G))}{\log\min(x,y)}
	  $$
	  Where $\mathcal{G}(x,y)$ denotes the set of 2D grids of size $x\times y$ and $X(G),Y(G)$ are discretizations of the variables on this grid. Then, the maximal information coefficient is defined as
	  $$
	  \text{MIC}=\max_{x,y,xy<B}m(x,y)
	  $$
	  Where $B$ is a sample size dependent bound on the number of bins we can use. 
		* A MIC of $0$ represents no relationship between the variables
		* A MIC of $1$ represents a noise-free relationship of any form, not just linear.
# Links
* [[Probability]] - more on probability which is the basis of Information Theory.
* [[Machine Learning - A Probabilistic Perspective by Murphy|Murphy Ch. 2.8]]