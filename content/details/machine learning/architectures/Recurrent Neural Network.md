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
	  That is, for a RNN, we want the current state to be dependent on the previous state. However, unlike the [[Markov Chain|Markov Property]], we actually do retain some information about all previously seen states so far. 

![[RNN computation.png]]
<figcaption> RNN computation. Image taken from Zhanng et al. </figcaption>

* In practice, we calculate the hidden states as follows. Let 
  $n$ be the size of a minibatch
  $d$ be the size of each inputs in each example.
  $H_t\in \mathbb{R}^{n\times h}$ be the hidden state. 
  $X_t\in \mathbb{R}^{n\times d}$ be a minibatch of inputs
  $\phi$ be some activation function
  
  Then 
  $$
  H_t=\phi(X_tW_{xh}+H_{t-1}W_{hh}+b_h)
  $$
  
  Where $W_{xh}\in \mathbb{R}^{d\times h}$ and $W_{hh}\in \mathbb{R}^{h\times h}$ are weights ,and $b_h$ is a bias term.

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

* [[The Evolution of Recurrent Neural Networks]]