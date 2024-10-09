* An **optimization algorithm** pertains to the way to minimize the [[Loss Function]] to tune specific model parameters. 

# Gradient Descent 
* Let 
  $F$ be some multivariate function 
  $x$ be a vector such that $F(x)$ is defined.
  $\eta$ be a specified learning rate 
  
  **Gradient descent** is performed by updating the value of $x$ as follows 
  
  $$
  x \gets x - \eta \nabla F(x)
  $$

* We may think of this process as going *in the direction of steepest descent so that we reach the minimum faster*. 

* *Limitation*: Even with a good learning, the algorithm may converge slowly for large datasets as it updates on each pass of the dataset. 

* Gradient Descent is technically a [[Numerical Optimization|numerical method for optimization]]. 

# Stochastic Gradient Descent 
* **Stochastic Gradient Descent** -  A variation of Gradient Decent that is optimized for speed. In particular, rather than updating the model after reading the entire dataset, we instead *update on reading every entry in the dataset.*

* Let 
  $w$ be a parameter that we wish to find an optimum for.
  $F_w$ be a multivariate function with hyperparameter $w$ 
  $X$ be a list of vectors corresponding to our dataset
  $\eta$ be a specified learning rate 
  $n$ be the number of samples that we have.
  
  We update the values using the following algorithm: 
	* Shuffle the entries of $X$
	* For each entry, perform the update: $w \gets w - \eta \nabla F_w (X_i)$

* *Limitation*: While the algorithm solves the issue of the model updating too slowly, it has the problem of being computationally slow since we must update the hyperparameter in a serial manner. 
* *Limitation*: Also, we have the issue of this being unusable if we are trying to tune for a function that takes in a sequence of the observations as inputs (i.e., it takes more than one at a time).
# Minibatch Stochastic Gradient Descent 
* **Minibatch SGD** is a compromise between gradient descent and stochastic gradient descent. 
  
  We partition the dataset into minibatches and perform SGD on the minibatches 

* Let 
  $w$ be a parameter that we wish to find an optimum for.
  $F_w$ be a multivariate function with hyperparameter $w$ 
  $X$ be a list of vectors corresponding to our dataset
  $\eta$ be a specified learning rate 
  $b$ be the number of minibatches that we wish to use. 
  $\mathcal{B}$ be the set of batches of $X$.
  
  We update the values using the following algorithm: 
	* Shuffle the entries of $X$
	* $\mathcal{B}$ is the set obtained by batching $X$.
	* Perform the following updates for all batches. $\mathcal{B}_i$ is the $i$-th batch.
	  
	  $$
	  \begin{split}
	  Q_i &\gets \frac{1}{|\mathcal{B}_i|}{\sum_{x\in \mathcal{B}_i}{\nabla F_w(x)}} \\ 
	  w &\gets w - \eta Q_i
	  \end{split}
	  $$