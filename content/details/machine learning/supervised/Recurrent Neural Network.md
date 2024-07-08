* A **Recurrent Neural Network** is a class of [[Neural Network]] where the computational graph may contain cycles.
	* They are best suited for [[Sequence Based Algorithms|sequential tasks]]

# Architectural Details
* A **hidden state** is a state which is not necessarily observed, but which holds some form of latent representation about the inputs. *Typically ,it is used to aggregate sequential data*.
	* We use hidden states to avoid having to store many parameters since we are looking at the input's values at $t$ time steps away.
	  
	  Let $h_t$ denote the hidden state at time step $t$ and $x_t$ as the input.
	  
	  We calculate the hidden state as
	  $$
	  h_t=f(x_t,h_{t-1})
	  $$
	  That is, for a RNN, we want the current state to be dependent on the previous state. However, unlike the [[Markov Processes in Machine Learning|Markov Property]], we actually do retain some information about all previously seen states so far. 

![[RNN computation.png]]
<figcaption> RNN computation. Image taken from Zhanng et al. </figcaption>

* We make use of **Recurrent Layers**. These are layers which use hidden states obtained from previous computations.
  
  More formally, Let 
  $X_t \in \mathbb{R}^{n\times d}$ be a minibatch of inputs at time step $t$. 
  $H_t\in \mathbb{R}^{n\times h}$ be the hidden layer output  output of time step $t$.
  $\phi(x)$ be an activation function.
  
  We perform the calculation of the output as
  $$
  H_t=\phi(X_tW_{xh}+H_{t-1}W_{hh}+b_h)
  $$
	* We parameterize on the weights of the non-hidden states, the weights of the inputs (as in a fully connected layer) and the bias of the output term.

* Typical training involves using [[Backpropagation through Time]].
# Links
* [[Dive into Deep Learning by Zhang, Lipton, Li and Smola]]