# RNN Encoder-Decoder
* An **RNN Encoder-Decoder** is an [[Recurrent Neural Network]] architecture which comprises of two units, both are RNNs.
	* An **encoder** takes a variable length sequence as input and encodes it to some hidden state of fixed length
	* A **decoder** which takes the hidden state from the encoder and the leftwards context of the target sequence, and predicts the subsequent token in the target sequence. 

* At training time, the decoder is conditioned on the preceding tokens on the original sequence. However, at test time, we condition the decoder on the tokens already predicted. This may be achieved using [[Backpropagation through Time#Teacher Forcing|teacher forcing]].

![[Encoder-Decoder RNN.png|300]]
<figcaption> Encoder-Decoder RNN. Image taken from Zhang et al. </figcaption>

* The encoder transforms the input data as follows. 
  
  Suppose our input sequence is $x_1,\dots, x_T$. Then, at time step $t$, we obtain a hidden state $h_t$ as 
  $$
  h_t=f(x_t,h_{t-1})
  $$
  
  Where we concatenate the input feature vector with the previous hidden state. 
  
  After this, we transform the hidden states into a context variable $c$ such that  
  $$
  c=q(h_1,\dots,h_T)
  $$

* Let $y_1,\dots,y_T$ be an output sequence.
  
  For each time step $t'$, we assign a [[Random Variables and Probability Distributions|conditional probability]] based on the previous inputs and the context variable. 
  
  That is, 
  $$
  P(y_{t'+1} \ | \ y_1,\dots, y_{t'}, c)
  $$
  
  To perform the actual prediction, we simply take:
  
  $y_{t'}$ the previous token's target.
  $s_{t'-1}$ the hidden state from the previous time step
  $c$, the context variable. 
  
  We obtain the new hidden state $s_{t'}$ as
  $$
  s_{t'}=g(y_{t'-1},c,s_{t'-1})
  $$
  
  Where $g$ is some function that describes the decoder's transformation. 
  
  An output layer is then determined using $s_{t'}$ to figure out the conditional probabilities. Finally, we use softmax to generate our token $y_{t'+1}$. 
  
  In practice, we may continue generating entries using the decoder simply by feeding the shifted sequence to the model again.

* Since we use softmax for the decoder, we use the cross entropy [[Loss Function]].  
* We perform an additional step during training and mask irrelevant entries with $0$ so that they do not affect the loss (at the current time step). The masking is necessary since we also need to pad the sequence. 

# Transformers
* See [[The Transformer Model]]. Transformers have the advantage that their latent space representation can be of variable dimension

# Links
* [[Dive into Deep Learning by Zhang, Lipton, Li and Smola]]