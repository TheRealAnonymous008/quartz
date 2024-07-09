# Elman RNN
* An **Elman RNN** is the most basic RNN architecture consisting only of recurrent layers and no more modifications.

![[Elman Network.png]]
<figcaption> Elman Network </figcaption>

# LSTM
* **Long Short Term Memory (LSTM)** is an RNN architecture that improves over the Elman Network. *We replace each recurrent node with an LSTM memory cell*
* The term "long short-term memory" comes from the fact that standard recurrent neural networks have *long term memory* because of their weights. These weights change slowly during training, which encodes general knowledge about the data. RNNs also have *short term memory* because of their activations The LSTM model combines these two facets through memory cells.
* *LSTMs are better than standard RNNs at dealing with [[Pathologies of Deep Learning|Vanishing and exploding gradients]]*.

*  Let
  $n$ be the batch size
  $h$ be the number of hidden units and
  $d$ the number of inputs. 
  $X_t\in \mathbb{R}^{n\times d}$  denotes the inputs in the current time step
  $H_{t-1}\in \mathbb{R}^{n\times h}$ denotes the hidden states in the previous time step
  $\sigma$ - the sigmoid activation function

* An **LSTM Memory Cell** features an internal state with a number of *multiplicative gates*. 
	* **Input Gate** - determines *how much of the input node's value should be added to the current value* of the internal state of the memory cell
	  
	  The input gates $I_t\in \mathbb{R}^{n\times h}$ are determined by
	  $$
	  I_t=\sigma(X_tW_{xi}+H_{t-1}W_{hi}+b_i)
	  $$
	  Where $W_{xi}\in \mathbb{R}^{d\times h}$ and $W_{hi}\in\mathbb{R}^{h\times h}$ are weight parameters and $b_i$ a bias parameter

	* **Forget Gate** - determines *whether we should keep the current state of the cell or "forget" it (flush it to $0$).*
	  
	  The forget gates $F_t\in \mathbb{R}^{n\times h}$ are determined by
	  $$
	  F_t=\sigma(X_tW_{xf}+H_{t-1}W_{hf}+b_f)
	  $$
	  Where $W_{xf}\in \mathbb{R}^{d\times h}$ and $W_{hf}\in\mathbb{R}^{h\times h}$ are weight parameters and $b_f$ a bias parameter

	* **Output Gate** - determines *whether a memory cell should influence the output at the current time step*.
	  
	  the output gates $O_t\in \mathbb{R}^{n\times h}$ are determined by
	  $$
	  O_t=\sigma(X_tW_{xo}+H_{t-1}W_{ho}+b_o)
	  $$
	  Where $W_{xo}\in \mathbb{R}^{d\times h}$ and $W_{ho}\in\mathbb{R}^{h\times h}$ are weight parameters and $b_o$ a bias parameter.


* The LSTM memory cell also has an **input node** which operates as follows   
  If we have input $X_t\in \mathbb{R}^{n\times d}$ and $H_{t-1}\in \mathbb{R}^{n\times h}$ hidden states in the previous time step, then the input nodes $\bar{C_t}\in \mathbb{R}^{n\times h}$ are determined by 
  $$
  \bar{C_t}=\tanh(X_tW_{xc}+H_{t-1}W_{hc}+b_c)
  $$
  Where $W_{xc}\in \mathbb{R}^{d\times h}$ and $W_{hc}\in\mathbb{R}^{h\times h}$ are weight parameters and $b_c$ a bias parameter, and we use the $\text{tanh}$ activation functions
  
* *The internal state is updated as follows*. 
  Let $C_{t-1} \in \mathbb{R}^{n\times h}$ denote the internal state in the previous time step
  $\bar{C_t}$ denote the input node at the current time step 
  
  We have
  $$
  C_t=F_t\odot C_{t-1} +I_t\oplus \bar{C_t}
  $$
  Where $\odot$ is the Hadamard product 

* *The hidden state is updated as follows*
  
  $$
  H_t=O_t\odot \tanh{C_t}
  $$
  The operation above allows us to accrue more information from previous time steps without necessarily updating the state of the output. 
![[LSTM memory cell.png]]
<figcaption> LSTM Memory Cell. Image taken from Zhang et al. </figcaption>

# GRU
* The **Gated Recurrent Unit (GRU)** offers a more streamlined version of the [[#LSTM]]. It *improves memory cells computationally without sacrificing performance*

* Let
  $n$ be the number of examples 
  $d$ be the number of inputs. 
  $h$ be the number of hidden units.
  $X_t\in \mathbb{R}^{n\times d}$ be the input as a minibatch
  $H_{t-1}\in \mathbb{R}^{n\times h}$ be the hidden state
  $\sigma$ - sigmoid activation

* We replace the three gates with only two.
	* **Reset Gate** - *controls how much of the previous state wee remember*. It captures short-term dependencies in the sequence.
	  
	  The reset gate $R_t\in \mathbb{R}^{n\times h}$ is computed as
	  $$
	  R_t=\sigma(X_tW_{xr}+H_{t-1}W_{hr}+b_r)
	  $$
	  
	  Where $W_{xr}\in \mathbb{R}^{d\times h}$ and $W_{hr}\in \mathbb{R}^{h\times h}$ are weights, and $b_r$ is a bias parameter.
		* When $R_t$ is close to $1$ we recover a vanilla RNN.
		* When $R_t$ is close to $0$, we have an MLP with $X_t$ as input and any pre-existing hidden state is reset to their defaults.
	* **Update Gate** - *controls how much of the new state is just a copy of the old state*.  It captures long-term dependencies in the sequence.
	  
	  The update gate $Z_t\in \mathbb{R}^{n\times h}$ is computed as
	  $$
	  Z_t=\sigma(X_tW_{xz}+H_{t-1}W_{hz}+b_z)
	  $$
	  
	  Where $W_{xz}\in \mathbb{R}^{d\times h}$ and $W_{hz}\in \mathbb{R}^{h\times h}$ are weights, and $b_z$ is a bias parameter.
		* When $Z_t$ is close to $1$, we retain the old state. Any information from $X_t$ is ignored and we skip time step $t$.
		* When $Z_t$ is close to $0$, the new hidden state approaches the latent state $\bar{H_t}$. 

![[GRU cell.png]]
<figcaption> GRU cell. Image taken from Zhang et al. </figcaption>

* We first derive a candidate hidden state $\bar{H}_t$ using only the reset gate as follows
  
  $$
  \bar{H}_t = \tanh(X_tW_{xh} +(R\odot H_{t-1})W_{hh} +b_h)
  $$
  Where $W_{xh}\in \mathbb{R}^{d\times h}$ and $W_{hh}\in \mathbb{R}^{hh}$ are weight parameters and $b_h\in \mathbb{R}^{1\times h}$  is the bias term. We also use the Hadamard product  $\odot$ and the $\text{tanh}$ activation function. 
* The hidden states are calculated using the update gate
  
  $$
  H_t=Z_t\odot H_{t-1} +(1-Z_t)\odot \bar{H}_t
  $$


* In the derivation of the candidate hidden state, rather than performing matrix multiplication to model the influence of previous hidden states, we can instead reduce this to performing elementwise multiplication. 

# Deep RNN
* A **Deep RNNN** is a variant which involves *using multiple recurrent layers stacked on top of each other*. 
* Given a sequence of length $T$, one layer produces a new sequence of the same length and this is fed to the next layer. 
* *Each hidden state operates on a sequential input and produces sequential output. *
* Any RNN cells at each time depend on both the same layer's value at the previous time step, and the previous layer's value at the same time step.

* More formally,  Let 
  $n$ be the size of a minibatch
  $d$ be the number of inputs in each example
  $L$ be the number of layers in the network.
  $H_t^{(l)}\in \mathbb{R}^{n\times h}$ be the hidden state at the $l$-th layer. 
  $H_t^{(0)}\in \mathbb{R}^{n\times d}$ be a minibatch of inputs (i.e., we treat the input as the $0$-th layer).
  $\phi$ be some activation function
  
  Then 
  $$
  H_t^{(l)}=\phi(H_t^{(l-1)} W_{xh}^{(l)}+H_{t-1}^{(l)}W_{hh}^{(l)}+b_h^{(l)})
  $$
  
  Where $W_{xh}^{(l)}\in \mathbb{R}^{d\times h}$ and $W_{hh}^{(l)}\in \mathbb{R}^{h\times h}$ are weights ,and $b_h$ is a bias term.
  
  The output layer is calculated as
  $$
  O_t=H_t^{(L)}W_{qh}+b_q
  $$
  
  Where $W_{hq}\in \mathbb{R}^{h\times q}$ is the weight and the bias is $b_q$. These are parameters of the output layers. 

![[Deep RNN.png]]
<figcaption> Deep RNN. Image taken from Zhang et al.</figcaption>

# Bidirectional RNN
* A **Bidirectional RNN** is a variant of an RNN which is a *combination of two RNNs* training the network in opposite directions. One starts from the beginning of a sequence, while the other from the end of a sequence.
	* The bidirectional RNN is *motivated by allowing the model to learn from future events as well*. This provides additional input information available to the network. 
	* This is especially useful when the context of the input is needed, i.e., for a particular data point, we need to look at the temporally local data points. 

* Let 
  $n$ be the number of examples
  $d$ be the number of inputs in each example
  $h$ be the number of hidden units. 
  $q$ be the number of outputs.
  $\phi$ be the activation function 
  $X_t\in \mathbb{R}^{n\times d}$ be a minibatch input. 
  $\overrightarrow{H_t}\in \mathbb{R}^{n\times h}$ be the forward hidden state
  $\overleftarrow{H_t}\in \mathbb{R}^{n\times h}$ be the backward hidden state. 
  $O_t\in\mathbb{R}^{n\times q}$ be the output of a layer.
  
  We update the hidden states as follows: 
  $$
  \begin{equation} \begin{split}
  \overrightarrow{H_t} &= \phi(X_tW_{xh}^{(f)}+\overrightarrow{H}_{t-1}W_{hh}^{(f)}+b_h^{(f)})  \\
  \overleftarrow{H_t} &= \phi(X_tW_{xh}^{(b)}+\overleftarrow{H}_{t-1}W_{hh}^{(b)}+b_h^{(b)})
  \end{split}\end{equation}
  $$
  Where we have weight parameters and bias parameters.
  
  Then, we concatenate the forward and backward hidden states to obtain the hidden state $H_t\in\mathbb{R}^{n\times 2h}$. 
  
  In a deep BRNN with multiple hidden layers, the hidden layer state is passed as input to the next bidirectional layer. 
  
  We then calculate the output layer as 
  $$
  O_t=H_tW_{hq}+b_q
  $$

![[Bidirectional RNN.png]]
<figcaption> Bidirectional RNN. Image taken from Zhang et al. </figcaption>

# RNN Encoder Decoder
* See [[Encoder-Decoder networks]].

# Links
* [[Recurrent Neural Network]]
* [[Dive into Deep Learning by Zhang, Lipton, Li and Smola]]