
* Because of this training method, RNNs are susceptible to [[Pathologies of Deep Learning|Vanishing and Exploding gradients]].
* RNNs are also more susceptible to local optima.

# Gradient Clipping
* We can mitigate gradient issues in Backpropagation through time with **Gradient Clipping**. 
  
* Assume we have an objective function $f$ that is Lipschitz continuous with constant $L$
  
  We have by definition
  $$
  |f(x)-f(y)|\le L||x-y||
  $$
  Updating parameter values using [[Optimization Algorithms in Machine Learning|Gradient Descent]] means that we have for learning rate $\eta$ and gradient $g$
  
  $$
  |f(x)-f(x-\eta g)|\le L\eta ||g||
  $$
  So that the objective function cannot change by more than the RHS of the inequality above. 
  
  In Gradient Clipping, therefore, we limit $L\eta ||g||$.

* There are a few approaches to this
	* *Limit the learning rate*. The downside is that it will take longer for the model to train since we have a smaller learning rate. This is especially true if the gradient rarely blows up. 
	* The **Gradient Clipping Heuristic** can be used especially if gradient values are rare. 
	  
	  We project the gradient onto a ball of radius $\theta$. That is, in the above, we set $g$ to be 
	  $$
	  g\gets \min\left(1,\frac{\theta}{||g||}\right)g
	  $$
		* This allows us to limit the effect of any given minibatch during training.

* One upside is that we mitigate the problems of exploding and vanishing gradients.
* One downside to clipping is that *we limit the speed at which we reduce the values* of our objective function.
* Another downside is that it is harder to analyze the side effects of applying this technique since we no longer follow the true gradient.


# Truncated BPTT
# Randomized Truncated BPTT


# Links
* [[Recurrent Neural Network]]
* [[Differential Calculus]]
* [[Dive into Deep Learning by Zhang, Lipton, Li and Smola]]