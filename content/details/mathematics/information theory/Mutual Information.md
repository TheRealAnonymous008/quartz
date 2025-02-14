* The **Mutual Information** determines how similar the [[Random Variables and Probability Distributions|joint distribution]] $p(X,Y)$ is to the factored distribution $p(X)p(Y)$. It is defined, therefore as 
  $$
  \begin{split}
  I(X;Y)&=\text{KL}(p(X,Y) \mid\mid p(X)p(Y)) \\ &=\sum_{x}\sum_{y}p(x,y)\log{\frac{p(x,y)}{p(x)p(y)}}
  \end{split}
  $$
  
* This determines how much information can be extracted about one random variable given observations on another.
* It can also be expressed as 
  $$
  I(X;Y)=H(X)-H(X\mid Y)=H(Y)-H(Y\mid X)
  $$
* It can also be expressed as the expected value of the pointwise mutual information.



# Approximation
* A simple approximation for continuous random variables is to simply bin them (bin sizes need not be the same) and treat them as if they were discrete. 
	* *Limitation*: This does not necessarily work if the underlying distributions aren't smooth. 


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



* [^kraskov_2003] proposes an approximation for mutual information based on [[Clustering|KNN]] distances.  The general idea is to *estimate the entropy using the average distance* to the $k$-Nearest Neighbors for all data points.
	* We use the [[Measure Theory|metric space]] $Z=(X,Y)$ with the [[Inner Product Space|norm]] defined as 
	  $$
	  ||z-z'|| = \max(||x-x'|| , ||y-y'||)
	  $$
	  We also denote $\epsilon(i)/2$ as the distance from $z_i$ to its $k$-th nearest neighbor, and similarly $\epsilon_x(i)/2$ and $\epsilon_y(i)/2$ for the distances between the same points projected in $X$ and $Y$.
	  
	  Further denote $n_x(i)$ as the number of points $x_j$ whose distance from $x_i$ is strictly less than $\epsilon(i)/2$  
	  
	  We take inspiration from the [[Information Theory|Kozachenko-Leonenko Estimate for Entropy]] and use the same notation defined there. 
	* The first estimator $I^{(1)}(X;Y)$ is given by
	  $$
	  I^{(1)}(X_1; X_2; \dots; X_m) = \psi(k) + (m-1) \psi(N) - \braket{\psi(n_{x_1}) + \dots + \psi(n_{x_m})}
	  $$
		* The approximation is derived using the entropy estimator 
		  $$
		  \hat{H}(X,Y) = \psi(k) - \psi(N)- \log(c_{d_X} c_{d_Y}) - \frac{d_X +d_Y}{N} \sum_{i=1}^N\log\epsilon(i)
		  $$
		* To approximate each marginal distribution, we use 
		  $$
		  \hat{H}(X) = \frac{1}{N} \sum_{i=1}^N \psi(n_x(i) + 1) - \psi(N) -\log c_{d_X} -\frac{d_X}{N} \sum_{i=1}^N \log \epsilon(i) 
		  $$
		  Where the approximation is derived by supposing one of the $k$-th neighbor has distance $\epsilon(i)/2$. 
		* *Limitation*:  The derivation uses the Kozachenko-Leonenko estimator correctly in one direction. 
	* The second approximation $I^{(2)}(X;Y)$ is given by using hyperrectangles instead of hypercubes.  The approximation is given by
	  $$
	  I^{(2)}(X_1;\dots;X_m) = \psi(k) - \frac{m-1}{k} + (m-1)\psi(N) -\braket{\psi(n_{x_1}) + \dots + \psi(n_{x_m})}
	  $$
		* The general idea is to replace $P_k(\epsilon)$ in the Kozachenko-Leonenko approximation with the following. Denote $q_i$ as the mass of the rectangle of size $\epsilon_x,\epsilon_y$ centered at $(x_i,y_i)$ and $p_i$ is the mass of the mass of the square of size $\epsilon=\max(\epsilon_x, \epsilon_y)$
		  $$
		  \begin{split}
		  P_k(\epsilon_x,\epsilon_y) &= P_k^{(b)} (\epsilon_x, \epsilon_y) + P_k^{(c)}(\epsilon _x,\epsilon_y) \\ 
		  P_k^{(b)} (\epsilon_x, \epsilon_y) &= {N-1\choose k} \frac{d^2 [q_i^k]}{d\epsilon_x d \epsilon_y} (1-p_i)^{N-k-1} \\ 
		  P_k^{(c)}(\epsilon_x,\epsilon_y) &= (k-1)  \ P_k^{(b)}(\epsilon_x, \epsilon_y)
		  \end{split}
		  $$
		* *Caveat*: The above is technically valid only for approximating the entropy of the joint distribution. The entropy of the joint marginals require corrections on the order $O(1/n_{x_i})$ for $X_i$

[^Kraskov_2003]: Kraskov, Stoegbauer, and Grassberger (2003) [Estimating Mutual Information](https://arxiv.org/abs/cond-mat/0305641)


# Links
* [[Machine Learning - A Probabilistic Perspective by Murphy|Murphy Ch. 2.8]]
* [[Probability Theory]] - more on probability which is the basis of Information Theory