* A naive increase in context length leads to an increase in time and space [[Complexity Theory|complexity]] since both scale quadratically. 
* **Extrapolation** pertains to the ability of the model to continue to perform well as the sequence length increases beyond the number of tokens seen during training. 
	* *Handling longer contexts necessitates better extrapolation*

* A vanilla transformer has fixed and limited context window.  *This leads to context fragmentation during training.* Thus:
	* *We cannot capture long-term dependencies* between tokens that are of distance greater than the context window. Therefore, information from the first token is lost.
	* During inference, the issue now becomes a matter of performance since we maximize the context but this entails moving one token at a time and *re-processing tokens that have already been processed*.
	* The **early token curse** - perplexity degrades for early tokens in a subsequence since they cannot access many previous context tokens.

# Extending Context Memory 
* [^rae_2019] proposes the **Compressive Transformer** which *compresses past memories for long-range sequence learning*. 
	* This is an improvement to the Transformer-XL model. Instead of discarding previous hidden states, we compress them 
	* Let $n_m$ and $n_c$ be the number of memory and compressive memory slots in the model per layer. 
	  
	  The overall input sequence is $S=x_1,\dots,x_{L}$ and split into fixed-sized windows of size $n_s$. The model observes $x=\set{x_t,\dots,x_{t+n_s}}$ 
	  
	  As the model moves, its $n_s$ hidden activations are pushed into FIFO memory with the oldest $n_s$ activations being evicted.
	  
	  Evicted activations are passed to the **compression operation** $f_c:\mathbb{R}^{n_s\times d}\to \mathbb{R}^{\lfloor \frac{n_s}{c} \rfloor \times d}$  to the $n_s$ oldest memories to $\lfloor\frac{n_s}{c} \rfloor$. 
	* Some choices for compression functions $f_c$:
		* [[Convolutional Neural Network#Pooling|Max/Mean Pooling]] with kernel and stride set to $c$. 
		* 1D convolution with kernel and stride set to $c$.
		* Dilated convolutions
		* Preserve the most attended memories. 
	* The compression network is trained using an **auto-encoding loss** with the goal of [[Encoder-Decoder Network|reconstructing]] the original memories from compressed memories.  The loss is defined using a learned decoder $g:\mathbb{R}^{\frac{n_s}{c}\times d}\to \mathbb{R}^{n_s\times d}$ to minimize
	  $$
	  \mathcal{L}^{ae} = ||h_o-g(h_c)||_2
	  $$
	  Where $h_o$ and $h_c$ are the original and compressed memories respectively.
	* We also add an **attention reconstruction loss** that reconstructs the content-based attention over memory with content-based attention over compressed memory. This is what we use for $f_c$. 
	  
	  Define the attention operator as 
	  $$
	  A(h,m) = \sigma(hQ mK) mV
	  $$
	  Let $h_o$ and $h_c$ be the original and compressed memories. Then the loss is defined by summing across all layers as 
	  $$
	  \mathcal{L}^{attn} = \sum_{l} ||A(h^{(l)}, h_o^{(l)}) - A(h^{(l)} - h_c^{(l)})||_2 
	  $$
	  Where $h^{(l)}$ is the hidden state at the $l$-th layer.  

	* Compression losses are not mixed with the losses of the main network.
	* The temporal range of the compressed transformer with  $N$ layers is 
	  $$
	  O(n_m + c \cdot n_c)
	  $$
	  The attention cost is 
	  $$
	  O(L^2 + L(n_m + n_c)) 
	  $$

![[Compressive Transformer.png]]
<figcaption> Compressive Transformer Architecture. Image taken from Rae et al. (2019)  </figcaption>

![[Compressive Transformer Algorithm.png]]
<figcaption> Compressive Transformer Algorithm.  Image taken from Rae et al. (2019)  </figcaption>

[^Rae_2019]: Rae et al. (2019) [Compressive Transformers for Long-Range Sequence Modelling](https://arxiv.org/abs/1911.05507)



* [^dai_2019] introduces **Transformer-XL** for learning dependencies beyond a fixed context length. 
	* Longer context is achieved using [[Recurrent Neural Network|recurrent layers]] coupled with a new relative positional encoding scheme.
	* During training, *the hidden state sequence from the previous segment(s) is fixed and cached*. This is treated as an extended context and models long term dependencies. *The current key and value are conditioned on the extended context*.
	* More formally. Let $s_\tau=\set{x_{\tau,1},\dots,x_{\tau,L}}$ be a segment and the hidden state produced by the $n$-th layer for $s_\tau$ be $h_\tau^n\in\mathbb{R}^{L\times d}$. Then the $n$-th layer hidden state for $s_{\tau+1}$ is given by 
	  $$
	  \begin{split}
	  \tilde h_{\tau+1}^{n-1} &= \left[\text{SG} (h_{\tau}^{n-1}) \circ  h_{\tau+1}^{n-1} \right] \\
	  Q_{\tau + 1}^n &= h_{\tau}^{n-1} W^q \\
	  K_{\tau + 1}^n &= \tilde h_{\tau+1}^{n-1} W^k \\
	  V_{\tau + 1}^n &= \tilde h_{\tau+1}^{n-1} W^v \\
	  h_{\tau + 1}^n&= \text{transformer}(Q_{\tau+1}, K_{\tau+1}^n, V_{\tau+1}^n)
	  \end{split}
	  $$
	  Where $\text{SG}(\cdot)$ denotes we stop computing the gradient for the argument and $\circ$ denotes concatenation.
		* We can cache more than the previous hidden state to produce a sequence of hidden states referred to as the memory $m_{\tau}^n$. 
	* During evaluation, *representations from previous segments can be reused*. 
	* Introducing recurrence necessitates the use of relative [[Positional Encoding|positional encoding]] to keep positional encodings coherent. See more in the linked page.
	* The temporal range of Transformer-XL with $N$ layers is $O(mN)$. The attention cost is $O(L^2+Lm)$ 
	  

![[Transformer XL.png]]
<figcaption> Transformer-XL Framework. Image taken from Dai et al. (2019) </figcaption>

[^Dai_2019]: Dai et al. (2019) [Transformer-XL: Attentive Language Models Beyond a Fixed-Length Context](https://arxiv.org/abs/1901.02860)





# Non-Differentiable External Memory
* The primary approaches here revolve around introducing Non-Differentiable External Memory via a Key-Value (KV) [[Database|database]].
	* Memory being Non-Differentiable (not trained) is essential as otherwise, all keys and values would have to be recomputed. [^wu_2022]



* [^wu_2022] extends language models with the ability to memorize the internal representations of past inputs. Effectively *the models can acquire new knowledge immediately at inference time*. 
	* The approach relies on [[Clustering|kNN]] lookup.  The focus is on *unifying attention and retrieval* using a decoder-only transformer. 
	* The proposed model also includes a Transformer-XL style cache
	* We make use of a kNN-augmented attention layer. For the local context, it performs self-attention. For the global context, it does an approximate kNN search into external memory.  This yields $V_m$ and $V_c$ for the attention result in external memory and local context respectively.
	  
	  Both attention results are combined using a learned gate
	  $$
	  \begin{split}
	  g &= \sigma(b_g) \\
	  V_a &= V_m\odot g + V_c \odot (1-g)
	  \end{split}
	  $$
	  Where $b_g$ is a scalar parameter unique per head.
	* For each head, the external memory keeps a cache of the prior KV pairs. 
	* Documents that are processed over long time steps induce a [[Pathologies of Deep Learning#Distribution Shift|Distribution shift]]. 
	  
	  To reduce the effects of old KV's becoming stale, keys and queries are normalized such that old and new keys do not differ in magnitude. 
	* Unlike prior approaches, we *use approximate kNN and learn the retrieval process*. We use the same queries for both local and external memory.
	* External memory is observed to provide an improvement (lower perplexity) at scale.  The improvement in perplexity seems to be mainly driven by a small percentage of tokens that obtain a large improvement in cross-entropy loss when using the larger memory.
	* *A non-memory transformer can be finetuned to use memory*.

![[Memorizing Transformer.png]]
<figcaption> Memorizing Transformer. Image taken from Wu, Rabe, Hutchins, and Szegedy (2022) </figcaption>

[^Wu_2022]: Wu, Rabe, Hutchins, and Szegedy (2022) [Memorizing Transformers](https://arxiv.org/abs/2203.08913)


* [^yogatama_2021]  introduces **SPALM (Semi-Parametric Language Model** mix a transformer with non-parametric memory. This allows models to obtain information from both its parameters and external memory depending on context. 
	* The idea is *store short term memory (temporary storage) for comprehending sentences* and *use long-term memory to store experiences, events and knowledge*.  Modularizing both facilitates easier training and a better model.
	* The model consists of three main components.  Essentially, *it combines features introduced by Transformer-XL and KNN-LM*. 
		* A *parametric base model* (transformer) that processes the local context. $\set{x_{t-N+1},\dots,x_t}$. 
		* A *short-term memory module* (i.e., like Transformer-XL) stores hidden states from an extended context.
			* Like in Transformer-XL, the extended context is the $M$ tokens prior to the current context.  That is $\set{x_{t-N-M+1},\dots,x_{t-N}}$
			* Let $h_t^r$ be the hidden state for $x_t$ at layer $r$. The hidden states associated with the current context are  $H^r=\set{h_{t-N}^r,\dots,h_t^r}$ and the extended context is $E^r=\set{\text{SG}(h_{t-N-M+1}^r),\dots,\text{SG}(h_{t-N}^r)}$, where $\text{SG}$ is the stop gradient function. 
			  
			  The two are used as input for the attention mechanism (with relative [[Positional Encoding|positional encoding]]) to obtain the KQV's to produce $H^{r+1}$. 

		* A *KV database* (i.e., like KNN-LM) stores compressed long term context.
			* Keys are compressed vector representations of $\set{x_{i-N+1},\dots,x_i}$ which we denote $d_i$ 
			* Values are the output token for that context $x_{i+1}$. 
			* Unlike in kNN-LMs, here we incorporate the retrieval process within the architecture rather than mixing between the outputs of two pretrained models.
	* The model combines the current context, the short-term memory, and retrieves past output tokens used in a similar token from long-term memory. This is all done via a gating mechanism. 
	  
	  Suppose the current context is $\set{x_{t-N+1},\dots, x_{t}}$ and we wish to predict $x_{t+1}$. First we get the representation of the context.
	  
	  We use this representation to then perform a $k$-NN search to retrieve the top $K$ values $y_1',\dots, y_K'$ from the database. 
	  
	  For each $y_i'$, obtain a vector  representation $y_i$ using the base model's embedding matrix.
	  
	  The gating mechanism then operates as follows
	  
	  $$
	  \begin{split}
	  m_t &= \sum_{k=1}^K \frac{\exp (y_kh_t^{RT})}{\sum_{j=1}^K\exp(y_jh_t^{RT})} y_k \\
	  g_t &= \sigma (w_g\cdot  h_t^R) \\ 
	  z_t &= (1-g_t) \odot m_t + g_t \odot h_t^R \\ 
	  p(x_{t+1}\mid \set{x_{t-N+1}, \dots, x_t}) &= \text{softmax}(z_t)
	  \end{split} 
	  $$
	  Where $w_g$ is a parameter, $\sigma$ is the sigmoid.  
		* The long term information $m_t$ is obtained by applying [[Attention Mechanism|attention]] using $h_t^R$ as the query. 
		* The gate $g_t$ is dependent on context and is used to decide how much local information or long-term information must be used based on the current context. 
		* $w_g$ lets the model adaptively combine short and long term memory.  
		* When training the above, key representations stay constant but the word embedding matrix gets updated.

	* *Limitation*: Retrieving from the KV database is time consuming.  

![[SPALM.png|250]]
<figcaption> SPALM. Image taken from Yogatama, d'Autume and Kong  (2021) </figcaption>

[^Yogatama_2021]: Yogatama, d'Autume and Kong (2021) [Adaptive Semiparametric Language Models](https://arxiv.org/abs/2102.02557)


* [^khandelwal_2019] introduces **$k$-NN LMs** which incorporate a [[Clustering|kNN]] model with a pre-trained [[Language Model|Language Model]].
	* The results of their work suggest that *[[Representation Learning|Learning similarity]] between sequences of text is easier than predicting the next word*, and that nearest neighbor search is an effective approach for language modeling in the long tail.
		* The rationale  behind this is that *identical sequences of words will have essentially the same distribution over the next word*. 
		* The approach is to then *memorize [[Information Theory|rare and surprising]] linguistic patterns* rather than implicitly encoding them in model parameters. 
	* We augment a pre-trained LM with a nearest neighbor retrieval mechanism. 
	  
	  This is done by maintaining a datastore. 
	  
	  Let $f$ be a function that maps context $c$ to a fixed vector representation computed by the pre-trained LM.  We maintain a datastore using the training examples in the training set $\mathcal{D}$.
	  $$
	  (\mathcal K,\mathcal V) = \set{(f(c_i),w_i) \mid (c_i,w_i)\in\mathcal{D}]}
	  $$
	  Where $c_i=(w_1,\dots,w_{i-1})$ (i.e., it is the prefix). 
	* At inference, given input context $x$, we generate the output distributions using the Language model and the context representation $f(x)$. 
	  
	  We query the data store with $f$ to retrieve the $k$ nearest neighbors $\mathcal{N}$ using the distance function $d$. 
	  
	  The distribution over the kNN is then computed using the negative distances. 
	  $$
	  p_{\text{kNN}}(y\mid x) = \sum_{(k_i,v_i)\in\mathcal{N}} \mathbb{1}_{y=v_i} \exp (-d(k_i,f(x)))
	  $$
	* The final kNN-LM distribution is 
	  $$
	  p(y\mid x ) = \lambda  \cdot p_{\text{kNN}}(y\mid x) + (1-\lambda)  p_{\text{LM}} (y\mid x)
	  $$
	* *kNN-LM is especially helpful for cases with rare patterns*. For example: incorporating factual knowledge, names and near duplicate sentences. In this case *it is easier to memorize these patterns via the representations rather than using next-word prediction*. 
	* Its effectiveness comes from:
		* The Transformer is good at learning a representation function for contexts with an implicit notion of similarity.
		* The Transformer has the capacity to memorize all training examples but at the cost of making its  representation less generalizable. But, the kNN representations mitigate this by memorizing the training data. 

![[kNN-LM.png]]
<figcaption> kNN-LM. Image taken from Khanelwal et al. (2019) </figcaption>

[^Khandelwal_2019]: Khanelwal et al. (2019) [Generalization through Memorization: Nearest Neighbor Language Models](https://arxiv.org/abs/1911.00172)

# Links
* [[Dive into Deep Learning by Zhang, Lipton, Li and Smola|Zhang et. al Ch. 11]] - for everything about the basics of the transformer model.
* [All about Attention](https://lilianweng.github.io/posts/2018-06-24-attention/) - more about attention

* [The Transformer Family v2.0 by Lilian Weng](https://lilianweng.github.io/posts/2023-01-27-the-transformer-family-v2/)
* [[Transformer Model]]