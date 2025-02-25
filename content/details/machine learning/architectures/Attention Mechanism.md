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
	  \text{Attention}(q,D) := \sum_{i=1}^m \alpha(q,k_i)v_i
	  $$
	  Where $\sum \alpha(q,k_i) = 1$, achieved via applying softmax
	  $$
	  \alpha(q,k_i) = \frac{\exp(a(q,k_i))}{\sum_j \exp(a(q,k_j))}
	  $$
	  For any differentiable function $a$.

	* Attention can be imagined as *doing a proportional retrieval from the database*. 

	* $\alpha(q,k)$ is used to *determine how well the query matches the key*. It can be **additive** or use a **scaled dot product**. It is normalized using SoftMax.

 * Attention can be extended to **multi-head attention** where queries, keys, and values are transformed using multiple attention operations (called **heads**).
	* The idea is that *each head attends to different parts of the input*.
	* By the end of the pipeline, the outputs of all heads are concatenated.
* **Self-attention** pertains to an attention mechanism where *the tokens are used as the source of the queries, keys, and values*. 
	* In a sense, every token can attend to every other token in the sequence.
	* Note that because of this design, *the importance of positioning is lost*.

# Links
* [[Dive into Deep Learning by Zhang, Lipton, Li and Smola]]