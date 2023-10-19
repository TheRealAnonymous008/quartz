# Random Variables
* A **random variable** is a function that maps an event in the sample space to a numerical value.
* A **discrete random variable** operates on a countable sample space. That is, it may be quantified using a **probability mass function** $p(x)$ where $$\sum_xp(x)=1$$and $$p(x)=P(X=x)$$
* A **continuous random variable** operates on an uncountable sample space. It can be quantified using a **probability density function** $f(x)$ wherein the probability $P(a\le X \le b)$ is given by $$P(a\le X\le b)=\int_{a}^bf(x) \ dx$$ A corresponding function called the **cumulative distribution function** $F$ is defined such that $$F(a)=P(X\le a)=\int_{-\infty}^a f(x) \ dx$$
* *Change of variables extends to probability distributions* Given $Y=f(X)$ is a continuous random variable from $X$, with probability distribution $p_Y$ and $p_X$, assuming $f$ is an invertible function, we have that $$p_y(y)=p_x(x)\left| \frac{\partial x}{\partial y}\right|$$Where $\frac{\partial x}{ \partial y}$ denotes the Jacobian for multidimensional $f$.
	* If $y$ were discrete, then we simply have $$p_y(y)=\sum_{x : f(x)=y}p_x(x)$$
# Properties of Probability Distributions
* The **Quantile** denoted $Q(a)=x_a$ defined as the value such that $$P(X\le x_a)=a$$
* The **mean** or **expectation** or **expected value**  is defined as the average value of the distribution.  $$\mu = E[X]=\sum_{x\in X} x \ P(x)$$
	* An alternative notation is $E_{P(Y)} [X]$  which is obtained as $$E_{P(Y)}[X]=\sum_{y \in Y}x \ P(y) $$
	* **Linearity of Expectation**. We have that $$E[aX+b]=aE[X]+b$$
* The **variance** is defined as the average spread of the distribution $$\sigma^2 =\text{Var}[X]=E[(X-\mu)^2]$$
	* An important formulation of the variance is as follows: $$\sigma^2=E[X^2]-(E[X])^2$$
	* The **standard deviation** is expressed in the same units of $X$. It is simply $$\sigma=\sqrt{\text{Var}[X]}$$
* The **covariance** between $X$ and $Y$ measure the degree to which they are linearly related. It is defined as $$\text{Cov}[X,Y]=E[(X-E[X]) (Y-E[Y])] =E[XY]-E[X]E[Y]$$We may define a **covariance matrix** $\Sigma$ whose entries contain the pairwise covariances between variables. That is $$\Sigma_{ij}=\text{Cov}[X_i,X_j]$$
	* The Covariance satisfies the following $$\text{Cov}[AX+b]=A \ \text{Cov}[X] \ A^T$$
* The **precision** is the inverse of the variance. It is given by $$p=\frac{1}{\sigma^2}$$The **precision matrix** is given as the inverse of the covariance matrix $$\Lambda=\Sigma^{_1}$$
* The **Pearson Correlation** between $X$ and $Y$ defines a normalized measure of the covariance. It is defined as $$\text{Corr}[X,Y]=\frac{\text{Cov[X,Y]}}{\sqrt{\text{Var}[X] \cdot \text{Var[Y]}}{}}$$
  We may define a **correlation matrix** $R$ where $$R_{ij}=\text{Corr}[X_i,X_j]$$
  In fact, $\text{Corr}[X,Y]=1$ indicates that $Y=aX+b$. Correlation is a measure to the degree in which two variables are linearly related.

# Links
* [[Machine Learning - A Probabilistic Perspective by Murphy|Murphy Ch. 2]]