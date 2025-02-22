* A **Recurrent Neural Network** is a class of [[Neural Network]] where the computational graph may contain cycles.
	* They are best suited for [[Sequence Based Algorithms|sequential tasks]] especially since, unlike vanilla neural networks, they do not have limited context i.e., for the same amount of weights as a regular neural network, we can in theory process an infinite length sequence by using hidden states.
	* Note that the context window itself is finite and in practice small. 

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

* We make use of **Recurrent Layers**. These are layers which use hidden states obtained from previous computations.
  
  More formally, Let 
  $x_t \in \mathbb{R}^{d}$ be the input at time step $t$. 
  $h_t\in \mathbb{R}^{h}$ be the hidden layer output  of time step $t$.
  $\phi(x)$ be an activation function.
  
  We perform the calculation of the output as
  $$
  h_t=\phi(W_{xh}x_t+W_{hh}h_{t-1}+b_h)
  $$
	*  Where $W_{xh}\in \mathbb{R}^{d\times h}$ and $W_{hh}\in \mathbb{R}^{h\times h}$ are weights ,and $b_h$ is a bias term.
	* The output is then a function of $h_t$. Let $\psi$ be an activation function, then the output $y_t$ is given by
	  $$
	  y_t = \psi (W_{ho} h_t)
	  $$
	  Where $W_{ho}\in \mathbb{R}^{h\times o}$ where $o$ is the output dimension.

* Typical training involves using [[Backpropagation through Time]].

# Links
* [[Dive into Deep Learning by Zhang, Lipton, Li and Smola]]

* [[The Evolution of Recurrent Neural Networks]]