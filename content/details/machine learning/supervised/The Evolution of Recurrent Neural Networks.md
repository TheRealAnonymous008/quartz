# Elman RNN
* An **Elman RNN** is the most basic RNN architecture consisting only of recurrent layers and no more modifications.

![[Elman Network.png]]
<figcaption> Elman Network </figcaption>

# LSTM
* **Long Short Term Memory (LSTM)** is an RNN architecture that improves over the Elman Network. *We replace each recurrent node with an LSTM memory cell*
* The term "long short-term memory" comes from the fact that standard recurrent neural networks have *long term memory* because of their weights. These weights change slowly during training, which encodes general knowledge about the data. RNNs also have *short term memory* because of their activations 
	* In other words: *LSTMs decouple two things that RNNs do* -- make decisions based on short-term memory and retain information via long-term memory. 
	* We balance short-term and long-term memory not by designing the neural architecture but by letting the model learn how to manage both.
* *LSTMs are better than standard RNNs at dealing with [[Pathologies of Deep Learning|Vanishing and exploding gradients]]*.

*  Let
  $h$ be the number of hidden units and
  $d$ the number of inputs. 
  $x_t\in \mathbb{R}^{d}$  denotes the inputs in the current time step
  $h_{t-1}\in \mathbb{R}^{h}$ denotes the hidden states in the previous time step
  $\sigma$ - the sigmoid activation function

* An **LSTM Memory Cell** features an internal state with a number of *multiplicative gates*. 
	* **Input Gate** - determines *how much of the input node's value should be added to the current value* of the internal state of the memory cell
	  
	  The input gate $i_t\in \mathbb{R}^{ h}$ is determined by
	  $$
	  i_t=\sigma(W_{xi} x_t+W_{hi}h_{t-1}+b_i)
	  $$
	  Where $W_{xi}\in \mathbb{R}^{h\times d}$ and $W_{hi}\in\mathbb{R}^{h\times h}$ are weight parameters and $b_i$ a bias parameter

	* **Forget Gate** - determines *whether we should keep the current state of the cell or "forget" it (flush it to $0$).*
	  
	  The forget gate $f_t\in \mathbb{R}^{h}$ is determined by
	  $$
	  f_t=\sigma(W_{xf}x_t+ W_{hf}h_{t-1}+b_f)
	  $$
	  Where $W_{xf}\in \mathbb{R}^{h\times d}$ and $W_{hf}\in\mathbb{R}^{h\times h}$ are weight parameters and $b_f$ a bias parameter

	* **Output Gate** - determines *whether a memory cell should influence the output at the current time step*.
	  
	  the output gate $o_t\in \mathbb{R}^{h}$ is determined by
	  $$
	  o_t=\sigma(W_{xo}x_t+W_{ho}h_{t-1}+b_o)
	  $$
	  Where $W_{xo}\in \mathbb{R}^{h\times d}$ and $W_{ho}\in\mathbb{R}^{h\times h}$ are weight parameters and $b_o$ a bias parameter.


* The LSTM memory cell also has an **input node** which operates as follows   
  If we have input $x_t\in \mathbb{R}^{d}$ and the hidden state $h_{t-1}\in \mathbb{R}^{h}$  in the previous time step, then the input node $\bar{c_t}\in \mathbb{R}^{h}$ is determined by 
  $$
  \bar{c_t}=\tanh(W_{xc}x_t+W_{hc}h_{t-1}+b_c)
  $$
  Where $W_{xc}\in \mathbb{R}^{h\times d}$ and $W_{hc}\in\mathbb{R}^{h\times h}$ are weight parameters and $b_c$ a bias parameter, and we use the $\text{tanh}$ activation functions
  
* *The internal state is updated as follows*. 
  Let $c_{t-1} \in \mathbb{R}^{h}$ denote the internal state in the previous time step
  $\bar{c_t}$ denote the input node at the current time step 
  
  We have
  $$
  c_t=f_t\odot c_{t-1} +i_t\oplus \bar{c_t}
  $$
  Where $\odot$ is the Hadamard product 

* *The hidden state is updated as follows*
  
  $$
  h_t=o_t\odot \tanh{c_t}
  $$
  The operation above allows us to accrue more information from previous time steps without necessarily updating the state of the output. 
![[LSTM memory cell.png]]
<figcaption> LSTM Memory Cell. Image taken from Zhang et al. </figcaption>

# GRU
* The **Gated Recurrent Unit (GRU)** offers a more streamlined version of the [[#LSTM]]. It *improves memory cells computationally without sacrificing performance*

* Let
  $d$ be the number of inputs. 
  $h$ be the number of hidden units.
  $x_t\in \mathbb{R}^{d}$ be the input at time step $t$.
  $h_t \in \mathbb{R}^{h}$ be the hidden state at time step $t$
  $\sigma$ - sigmoid activation

* We replace the three gates of an LSTM with only two.
	* **Reset Gate** - *controls how much of the previous state wee remember*. It captures short-term dependencies in the sequence.
	  
	  The reset gate $r_t\in \mathbb{R}^{h}$ is computed as
	  $$
	  r_t=\sigma(W_{xr}x_t+W_{hr}h_{t-1}+b_r)
	  $$
	  
	  Where $W_{xr}\in \mathbb{R}^{h\times d}$ and $W_{hr}\in \mathbb{R}^{h\times h}$ are weights, and $b_r$ is a bias parameter.
		* When $r_t$ is close to $1$ we recover a vanilla RNN.
		* When $r_t$ is close to $0$, we have an MLP with $X_t$ as input and any pre-existing hidden state is reset to their defaults.
	* **Update Gate** - *controls how much of the new state is just a copy of the old state*.  It captures long-term dependencies in the sequence.
	  
	  The update gate $z_t\in \mathbb{R}^{h}$ is computed as
	  $$
	  z_t=\sigma(W_{xz}x_t+W_{hz}h_{t-1}+b_z)
	  $$
	  
	  Where $W_{xz}\in \mathbb{R}^{h\times d}$ and $W_{hz}\in \mathbb{R}^{h\times h}$ are weights, and $b_z$ is a bias parameter.
		* When $z_t$ is close to $1$, we retain the old state. Any information from $X_t$ is ignored and we skip time step $t$.
		* When $z_t$ is close to $0$, the new hidden state approaches the latent state $\bar{H_t}$. 

![[GRU cell.png]]
<figcaption> GRU cell. Image taken from Zhang et al. </figcaption>

* We first derive a candidate hidden state $\bar{h}_t$ using only the reset gate as follows
  
  $$
  \bar{h}_t = \tanh(W_{xh}x_t +W_{hh}(r\odot h_{t-1}) +b_h)
  $$
  Where $W_{xh}\in \mathbb{R}^{h\times d}$ and $W_{hh}\in \mathbb{R}^{hh}$ are weight parameters and $b_h\in \mathbb{R}^{h}$  is the bias term. We also use the Hadamard product  $\odot$ and the $\text{tanh}$ activation function. 
* The hidden states are calculated using the update gate
  
  $$
  h_t=z_t\odot h_{t-1} +(1-z_t)\odot \bar{h}_t
  $$


* In the derivation of the candidate hidden state, rather than performing matrix multiplication to model the influence of previous hidden states, we can instead reduce this to performing elementwise multiplication. 

# Deep RNN
* A **Deep RNN** is a variant which involves *using multiple recurrent layers stacked on top of each other*. 
	* Like with deep neural networks, deep RNNs generally outperform single-layer RNNs. 

* Given a sequence of length $T$, one layer produces a new sequence of the same length and this is fed to the next layer. 
* *Each hidden state operates on a sequential input and produces sequential output. *
* Any RNN cells at each time depend on both the same layer's value at the previous time step, and the previous layer's value at the same time step.

* More formally,  Let 
  $d$ be the number of inputs in each example
  $L$ be the number of layers in the network.
  $h_t^{(l)}\in \mathbb{R}^{h}$ be the hidden state at the $l$-th layer. 
  $h_t^{(0)}\in \mathbb{R}^{d}$ be a minibatch of inputs (i.e., we treat the input as the $0$-th layer).
  $\phi$ be some activation function
  
  Then 
  $$
  h_t^{(l)}=\phi(W_{xh}^{(l)}h_t^{(l-1)} +W_{hh}^{(l)}h_{t-1}^{(l)}+b_h^{(l)})
  $$
  
  Where $W_{xh}^{(l)}\in \mathbb{R}^{d\times h}$ and $W_{hh}^{(l)}\in \mathbb{R}^{h\times h}$ are weights ,and $b_h$ is a bias term.
  
  The output layer is calculated as
  $$
  o_t=W_{qh} h_t^{(L)}+b_q
  $$
  
  Where $W_{qh}\in \mathbb{R}^{q\times h}$ is the weight and the bias is $b_q$. These are parameters of the output layers. 

![[Deep RNN.png]]
<figcaption> Deep RNN. Image taken from Zhang et al.</figcaption>

# Bidirectional RNN
* A **Bidirectional RNN** is a variant of an RNN which is a *combination of two RNNs* training the network in opposite directions. One starts from the beginning of a sequence, while the other from the end of a sequence.
	* The bidirectional RNN is *motivated by allowing the model to learn from future events as well*. This provides additional input information available to the network. 
	* This is especially useful when the context of the input is needed, i.e., for a particular data point, we need to look at the temporally local data points. 

* Let 
  $d$ be the number of inputs in each example
  $h$ be the number of hidden units. 
  $q$ be the number of outputs.
  $\phi$ be the activation function 
  $x_t\in \mathbb{R}^{d}$ be a minibatch input. 
  $\overrightarrow{h_t}\in \mathbb{R}^{h}$ be the forward hidden state
  $\overleftarrow{h_t}\in \mathbb{R}^{h}$ be the backward hidden state. 
  $o_t\in\mathbb{R}^{q}$ be the output of a layer.
  
  We update the hidden states as follows: 
  $$
  \begin{equation} \begin{split}
  \overrightarrow{h_t} &= \phi(W_{xh}^{(f)}x_t+W_{hh}^{(f)}\overrightarrow{h}_{t-1}+b_h^{(f)})  \\
  \overleftarrow{h_t} &= \phi(W_{xh}^{(b)}X_t+W_{hh}^{(b)}\overleftarrow{h}_{t-1}+b_h^{(b)})
  \end{split}\end{equation}
  $$
  Where we have weight parameters and bias parameters.
  
  Then, we concatenate the forward and backward hidden states to obtain the hidden state $h_t\in\mathbb{R}^{2h}$. 
  
  In a deep BRNN with multiple hidden layers, the hidden layer state is passed as input to the next bidirectional layer. 
  
  We then calculate the output layer as 
  $$
  o_t=W_{hq}h_t+b_q
  $$

![[Bidirectional RNN.png]]
<figcaption> Bidirectional RNN. Image taken from Zhang et al. </figcaption>

# RNN Encoder Decoder
* See [[Encoder-Decoder Network]].

# Links
* [[Recurrent Neural Network]]
* [[Dive into Deep Learning by Zhang, Lipton, Li and Smola]]
* [[Speech and Language Processing - An Introduction to Natural Language Processing, Computational Linguistics, and Speech Recognition with Language Models by Jurafsky and Martin]]