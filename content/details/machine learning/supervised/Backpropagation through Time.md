
* Because of this training method, RNNs are susceptible to [[Pathologies of Deep Learning|Vanishing and Exploding gradients]].
* RNNs are also more susceptible to local optima.
# Analysis of Gradients
* Let 
  $h_t$ be a hidden state
  $x_t$ be an input 
  $o_t$ be an output for time step $t$ of some sequential data
  
  Also let
  $W_{hx} \in \mathbb{R}^{h\times d}$ , $W_{hh} \in \mathbb{R}^{h\times h}$, $W_{qh} \in \mathbb{R}^{q \times h}$  be the weight parameters
  $l(o_t, y_t)$ be the loss.

* By the recursion we have that
  
  $$
  \begin{equation} \begin{split}
  h_t &= W_{hx}x_t+W_{hh}h_{t-1} \\
  o_t &= W_{qh}h_t
  \end{split}\end{equation}
  $$
* The loss function can be evaluated as 
  $$
  L=\frac{1}{T}\sum_{t=1}^T l(y_t, o_t)
  $$

![[BPTT.png]]
<figcaption> BPTT flow. Image taken from Zhang et al. </figcaption>

* Performing BPTT will involve calculating 
  $$
  \frac{\partial L}{\partial o_t}=\frac{\partial l(o_t,y_t)}{T\cdot\partial o_t}
  $$
  
  Next, from the above we recall that $o_t=W_{qh}h_t$. We have 
  $$
  \frac{\partial L}{\partial W_{qh}}=\sum_{t=1}^T{\frac{\partial L}{\partial o_t}\frac{\partial o_t}{\partial W_{qh}}} =
  \sum_{t=1}^T \frac{\partial L}{\partial o_t} h_t^\top
  $$
  
  Next, we compute for $\frac{\partial L}{\partial h_t}$. If $t=T$ then the chain rule simplifies since $h_T$ only depends on $o_T$ so
  $$
  \frac{\partial L}{\partial h_T}=\frac{\partial L}{\partial o_T} \frac{\partial o_T}{\partial h_T} = W_{qh}^\top \frac{\partial L}{\partial o_T}
  $$
  If $t<T$, then $L$ depends on $h_t$ via $h_{t+1}$ and $o_t$. Now, by chain rule, we can recursively compute the gradient as
  $$
  \begin{equation} \begin{split}
  \frac{\partial L}{\partial h_t} &= \frac{\partial L}{\partial h_{t+1}} \frac{\partial h_{t+1}}{\partial h_t} + \frac{\partial L}{\partial o_t} \frac{\partial o_t}{\partial h_t} \\
  &= W^\top_{hh} \frac{\partial L}{\partial h_{t+1}} + W^\top_{qh} \frac{\partial L}{\partial o_{t}}
  \end{split}\end{equation}
  $$
  
  And condensing the above by flattening the recursion, we may obtain
  $$
  \frac{\partial L}{\partial h_t}=\sum_{i=t}^T(W_{hh}^\top)^{T-i}W_{qh}^T \frac{\partial L}{\partial o_{T+t-i}}
  $$
  
  Finally, we get 
  $$
  \frac{\partial L}{\partial W_{hx}}= \sum_{t=1}^T\frac{\partial L}{\partial h_t} \frac{\partial h_t}{\partial W_{hx}} =  \sum_{t=1}^T\frac{\partial L}{\partial h_t} x^\top
  $$
  
  And
  
  $$
  \frac{\partial L}{\partial W_{hh}}= \sum_{t=1}^T\frac{\partial L}{\partial h_t} \frac{\partial h_t}{\partial W_{hh}} =  \sum_{t=1}^T\frac{\partial L}{\partial h_t} h_{t-1}^\top
  $$

* Note that $\frac{\partial L}{\partial h_t}$ is *both numerically unstable and expensive to compute*

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
* **Truncated BPTT** is a variation of BPTT where, when applying the chain rule to the recurrence in an RNN, we *stop the calculation* once we reach $\frac{\partial h_{t-\tau}}{\partial w_h}$  where $h_t$ denotes a hidden state and $w_h$ denotes the corresponding weights.
* This leads to an approximation of the gradient
* The model becomes more stable since it focuses only on short term influences rather than long term consequences.
# Randomized Truncated BPTT
* **Randomized Truncated BPTT** extends [[#Truncated BPTT]].
* The algorithm initially follows truncated BPTT. However, after a certain point, we replace the calculation of  $\frac{\partial h_{t}}{\partial w_h}$ with a [[Random Variables and Probability Distributions|random variable]] whose expectation matches that of the gradient.
* We do this with a sequence $\xi_t$ with predefined values $0\le \pi_t \le 1$. Where
  $$
  \begin{equation} \begin{split}
  P(\xi_t = 0) &= 1 - \pi_t \\
  P(\xi_t=\pi_t^{-1}) &= \pi_t
  \end{split}\end{equation}
  $$
  
  That is, we choose either a value $0$ or $\frac{1}{\pi_t}$ at time step $t$, and $\pi_t$ also determines the probability of choosing $\pi_t$. 
  
  The effect is that we randomly truncate the calculation of the gradient, and at the same time we calculate a weighted sum of sequences where long sequences are appropriate overweighted.
  
  We then calculate the gradient as 
  $$
  z_t=\frac{\partial f(x_t,h_{t-1}, w_h)}{\partial w_h} +\xi_t \frac{\partial f(x_t,h_{t-1}, w_h)}{\partial h_{t-1}}\frac{\partial h_{t-1}}{\partial w_h}
  $$

# Teacher Forcing
* **Teacher Forcing** is a training technique which involves feeding the observed sequence values back to the RNN after each step. This forces the RNN to stay close to the ground truth sequence.
* *Intuition*: Rather than having the model commit mistakes that accumulate, for each entry in the sequence, we tell the model if it was correct, and regardless, we give it the correct answer. 

# Links
* [[Recurrent Neural Network]]
* [[Differential Calculus]]
* [[Dive into Deep Learning by Zhang, Lipton, Li and Smola]]