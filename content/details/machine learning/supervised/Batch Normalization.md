* **Batch Normalization** is a technique used to accelerate the convergence of a learning model during training. 
* We do this by normalizing the inputs of each layer and then multiplying by a scaling coefficient and adding an offset to recover any lost degrees of freedom. We normalize based on batch statistics.
* This is motivated by the following needs 
	* We often want to preprocess before training since we constrain the complexity of the model by putting parameters at a similar scale.
	* Internal Covariate Shift can disrupt convergence. 
	* Deeper networks are more complex and are more prone to overfitting which requires regularization techniques. 

	* Let 
	  $\mathcal{B}$ be a minibatch
	  $x\in \mathcal{B}$ be an input to the batch normalization procedure, denoted $\text{BN}$.
	  
	  Then 
	  $$
	  \text{BN}(x)=\gamma \frac{x-\hat\mu_{\mathcal{B}}}{\sigma_{\mathcal{B}}}+\beta
	  $$
	  Where $\hat{\mu}_\mathcal{B}$ is the batch mean and $\sigma_\mathcal{B}$ the batch standard deviation 
	  
	  $\gamma$ and $\beta$ are hyperparameters learnt during training.
	  
	  Note that the standard deviation is calculated as $$\sigma_{\mathcal{B}}=\sqrt{\text{Var}(\mathcal{B} + \epsilon)}$$We add a small $\epsilon$ to prevent division by 0 and also to introduce noise in the estimates of the mean and variance. 

* Batch normalization appears to be *effective for moderate minibatch sizes* since larger minibatch sizes allow for more stable estimates of the mean and variance, reducing the effect of the $\epsilon$ term above and causing more overfitting. 
* We can define two protocols 
	* During *training mode*, we proceed as normal with minibatch statistics. 
	* During *prediction mode*, rather than use the minibatch statistics, we use the dataset statistics 

* A **Batch Normalized Fully Connected Layer** involves applying batch normalization before feeding to the algorithm .More formally.
  
  $$
  h=\phi(\text{BN}(Wx+b))
  $$


# Layer Normalization 
* An extension of Batch Normalization wherein we *apply batch normalization to one batch at a time. *
* Given $x$,the layer norm $\text{LN}(x)$ is given by 
  $$
  \text{LN}(x)=\frac{x-\mu}{\sigma}
  $$
  Where the scaling and offset are applied coefficient wise, and as with batch normalization we estimate the standard deviation using the variance plus some noise 
* Layer Normalization *prevents divergence since the output of layer normalization is independent of its scale.*
* The training procedure is also independent of the minibatch size, regardless if we are training or testing. 

# Links
* [[Dive into Deep Learning by Zhang, Lipton, Li and Smola|Zhang et. al]] - Ch. 3 - 5