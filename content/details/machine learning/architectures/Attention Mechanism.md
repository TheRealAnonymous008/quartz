* **Attention** is a mechanism that allows a model to selectively focus on particular tokens within some sequential input. 

# Motivation
* *Motivation*: The attention mechanism is motivated by the **bottleneck problem** found in [[Encoder-Decoder Network|Encoder Decoder Networks]] where the encoder must saliently represent the whole source text for the decoder's use. However, often the decoder only needs portions of the source text.
* *This allows the model to learn how to attend to each token in the source text using the tokens so far from the target text*. 
##  Query-Key-Value Model
* Another motivation is by observing  [[Database|Databases]] and retrieval systems where:
	* We have a set of **keys** to index the data found in the database.
	* Each key is associated with a **value**
	* The user can retrieve data through **queries**.
* Such a design leads to the following implications.
	* We can design queries that operate on key-value pairs such that they are valid regardless of the database size.
	* The same query can receive different answers according to the context of the database.
	* The code executed to operate on a large database can be simple.
	* There is no need to compress or simplify the database to make the operations effective.
# Formal Description
* *Attention is a [[Linear Combination|linear combination]] of the values where the weights are a function of the query and the key*. Or more mathematically it is given as follows.
	* $$
	  \text{Attention}(q,k,v) := \sum_{i=1}^m \alpha(q,k_i)v_i
	  $$
	  Where $\sum \alpha(q,k_i) = 1$, achieved via applying softmax
	  $$
	  \alpha(q,k_i) = \frac{\exp(a(q,k_i))}{\sum_j \exp(a(q,k_j))}
	  $$
	  For any differentiable function $a$. 

	* Attention can be imagined as *doing a proportional retrieval from the database*. 

	* $\alpha(q,k)$ is used to *determine how well the query matches the key*. 

## Alignment Scores
* The following lists choices for $\alpha(q,k)$

* **Content Base Attention** which uses cosine similarity
  $$
  \alpha(q,k) = \cos([q,k]) = \frac{q\cdot k}{||q|| \cdot ||k||}
  $$

  This is what was introduced in [^Graves_2014]

* **Additive (Bahdanau) Attention**
  $$
  \alpha(q_i,k_i) = k_a^T \tanh (W_a [q_{i-1}, k_i])
  $$
  Where $v_a$ is a trainable vector, $W_a$ is a trainable matrix and $q_i,k_i$ are the values of $q$ and $k$ at the $i$-th sentence position

* **Multiplicative (Luong) Attention** [^luong_2015]
  $$
  \alpha(q,v) = q^T W_a k
  $$
  Where $W_a$ is a trainable. 

* The **scaled dot product** is a simple choice for $\alpha$ where 
  $$
  \alpha(q,k) = \frac{q^Tk}{\sqrt{d_k}}
  $$
  Where $d_k$ is the dimension of the key-vector. We use this to make sure that exponentiation does not yield values that are too large.


# Extensions
 * Attention can be extended to **multi-head attention** where queries, keys, and values are transformed using multiple attention operations (called **heads**).
	* The idea is that *each head attends to different parts of the input*.
	* By the end of the pipeline, the outputs of all heads are concatenated.
* **Self-attention** pertains to an attention mechanism where *the tokens are used as the source of the queries, keys, and values*. 
	* In a sense, every token can attend to every other token in the sequence.
	* Note that because of this design, *the importance of positioning is lost*.

* Attention can be **hard** or **soft**
	* **Hard Attention** involves selecting one part of the input to apply attention to at a time.
	  
	  This means less calculations in inference time, but is more complicated to train.
	* **Soft Attention** involves applying attention across the entire input.
	  
	  This means more calculations in inference time but with ease of training due to differentiability and smoothness.

* [^luong_2015] proposes a distinction between **global** and **local** attention
	* **Global Attention** means to consider all source tokens. 
	  
	  This can potentially be expensive for longer sequences.
	* **Local Attention** involves choosing to consider only a subset of the source positions per word.
	  
	  This involves selecting a small context window around a source token and a predicted position to place this window. We attend to tokens within this window to compute the context vector.

![[Global Local Attention.png]]
<figcaption> Global and Local Attention. Image taken from Lilian Weng</figcaption>

[^Luong_2015]: Luong, Pham, Manning (2015) [Effective Approaches to Attention-based Neural Machine Translation](https://arxiv.org/abs/1508.04025)

[^Graves_2014]: Graves, Wayne, Danihelka (2014) [Neural Turing Machines](https://arxiv.org/abs/1410.5401)

# Topics
* [[Sparsity in Transformer]]

# Links
* [[Dive into Deep Learning by Zhang, Lipton, Li and Smola]]
* [Attention? Attention by Lilian Weng](https://lilianweng.github.io/posts/2018-06-24-attention/#a-family-of-attention-mechanisms)