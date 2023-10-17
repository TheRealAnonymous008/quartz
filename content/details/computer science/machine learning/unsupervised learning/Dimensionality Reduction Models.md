* The motivation behind this technique is that although the data may appear high dimensional, there may only be a small number of degrees of variability.
* **The Curse of Dimensionality** is a phenomenon where an increase in dimensionality also increases the sparsity of the data. 
	* For parameterized models, this means tuning more parameters to create a model.
	* For datasets, this implies obtaining more data to get more reliable results.
# Factor Analysis
* From a dataset with high dimensionality, reduce the dimension by assuming the data were distributed based on some multivariate normal distribution (at the limit) parameterized by:
	* Mean vector $\mu$ 
	* **Loading matrix** $W$ multiplied with $L$-dimensional **factors** $z$. 
	* A diagonal covariance matrix $\psi$ which models observed noise in each dimension.
* More formally, for data point $x$, we have $$x\sim \mathcal{N}(Wz+\mu, \psi)$$
* The factors $z$ are latent variables which are not observed but used to formulate the model. If these were averaged out, we get that $$x\sim\mathcal{N}(\mu,WW^T + \psi)$$
### Learning
* $\mu$ is simply the average of the observed data.
* $W$ and $\psi$ are iteratively estimated from each other using SVD with the goal of maximizing log-likelihood.
# Principal Component Analysis
* A special case of factor analysis wherein we assume the variance across all dimensions is the same.
* This only requires performing one SVD step.
* The result yields a model operating on a smaller space. 
* It should be noted that there will be some data loss on account of compressing the data. This is quantified using the **explained variance**.
# Links
* [Factor Analysis and Probabilistic PCA](https://www.youtube.com/watch?v=lJ0cXPoEozg)