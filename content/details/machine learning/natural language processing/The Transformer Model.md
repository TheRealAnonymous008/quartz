# Query-Key-Value Model
* The design of the transformer is motivated by observations found in databases and retrieval systems where:
	* We have a set of **keys** to index the data found in the database.
	* Each key is associated with a **value**
	* The user can retrieve data through **queries**.
* Such a design leads to the following implications.
	* We can design queries that operate on key-value pairs such that they are valid regardless of the database size.
	* The same query can receive different answers according to the context of the database.
	* The code executed to operate on a large database can be simple.
	* There is no need to compress or simplify the database to make the operations effective.
# Attention  
* **Attention** is a mechanism that allows a model to selectively focus on particular tokens within some sequential input. 
* *Attention is a linear combination of the values where the weights are a function of the query and the key*. Or more mathematically it is given as follows.
	* *$\text{Attention}(q,D) := \sum_{i=1}^m \alpha(q,k_i)v_i$
	* $\alpha(q,k)$ is used to *determine how well the query matches the key*. It can be **additive** or use a **scaled dot product**. It is normalized using SoftMax.
 * Attention can be extended to **multi-head attention** where queries, keys, and values are transformed using multiple attention operations (called **heads**).
	* The idea is that *each head attends to different parts of the input*.
	* By the end of the pipeline, the outputs of all heads are concatenated.
* **Self-attention** pertains to an attention mechanism where *the tokens are used as the source of the queries, keys, and values*. 
	* In a sense, every token can attend to every other token in the sequence.
	* Note that because of this design, *the importance of positioning is lost*.
# The Transformer Model
* The **transformer** model makes use of the attention mechanism to transform an input sequence to another output sequence.
* The model takes in an **embedding** (from some tokenizer or byte pair encoding) that acts as a more compact representation of the input data. 
* The model first performs **positional encoding** to represent the position of a token in the sequence. *This is done to account for the fact the order tokens appear in sequence is important*
	* The original positional encoding proposed encodes both the absolute position of a token, and its position relative to other tokens.  *For any fixed offset $\delta$, the positional encoding at $i+\delta$ can be obtained through linear projection of $\delta$ at $i$.*
* The model then consists of an [[Encoder-Decoder networks|encoder and a decoder]] 
	* The **encoder** takes in the input sequence and outputs a latent space representation called a **context variable** for each position in the input sequence. 
		* *Encoders can attend to the whole sequence as needed*.
	* The **decoder** takes in the context variable as well as another sequence and produces an output sequence.
		* The architecture for a decoder is mostly similar to the encoder except for the presence of a specialized layer.
		* It makes use of **encoder-decoder-attention** which performs attention such that the queries are from the previous decoder layer, and they keys and values are from the encoder outputs. 
		* *Decoders can only attend to the tokens that have already been generated*. 
		* *In deployment, the decoder is simply fed the outputs it has generated so far*.
	* The encoder produces the retrieval system for one language and the decoder produces the queries from another language.
* *The encoder and decoder need not be used together. They can be taken and trained separately*.
	* **Encoder-Only Transformers** are best suited for tasks where there is a need to understand the full sequence within one language.
		* They are pre-trained by corrupting the given sequence and tasking the model with reconstructing the initial sequence.
	* **Decoder-Only Transformers** are best suited for tasks that involve text-generation.
		* They are pre-trained by predicting the next word of the sequence.
* *Transformers scale very well* with increased model size and training computation. 
	* This scaling follows a power law.
	* This scaling is due to the fact the transformer is also easily parallelizable, enabling deeper architectures without performance loss.
# Papers
* [Attention is All You Need by Vaswani et. al (Dec 6, 2017)](https://arxiv.org/pdf/1706.03762.pdf) - the seminal Transformer paper.

* Universal Transformers by Deghani et. al (Mar 5, 2019) 

* Generating Long Sequences with Sparse Transformers by Child, Gray, Radford, Sutskever (Apr 23, 2019) 

* The Evolved Transformer by So, Liang, Le (May 17, 2019)
# Links
* [[Dive into Deep Learning by Zhang, Lipton, Li and Smola|Zhang et. al Ch. 11]] - for everything about the basics of the transformer model.
* [All about Attention](https://lilianweng.github.io/posts/2018-06-24-attention/) - more about attention

