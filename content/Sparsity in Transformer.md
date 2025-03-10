* A simple approach to sparsity is to restrict the attention span of each token to local context only. 

* [^child_2019] introduces **Sparse Transformers**  via a sparse factorization of the transformer that scales as $O(n\sqrt[p]{n})$. 
	* We also improve training using a structured [[Residual Learning|residual block]] and weight initialization scheme. 
	* We introduce sparse attention kernels that can efficiently compute subsets of the attention matrix.
	* We reduce  memory usage during training by recomputing attention weights. 
	* The key motivation behind factorization is the insight that *most layers have sparse attention patterns across most data points*.
	* Factorized self attention has $p$ attention heads where the $m$-th head define a subset of indices. $A_i^{(m)}\subset \set{j : j\le i}$ which determines the connectivity pattern  -- that is, where the $i$-th output vector attends to.
	  
	  Here, $|A_i^{(m)}|\propto \sqrt[p]{n}$. 
		* For every $j\le i$ pair, we set $A$ such that $i$ can attend to $j$ through a path of locations with maximum length $p+1$. Each location $x_i\in A_i^{(i)}$. 
		  
		  *This allows us to propagate signals throughout the sequence while reducing computation*
		* One approach is to have one head attend to the previous $l$ locations and the other attend to every $l$-th location, where $l\approx \sqrt{n}$ and is called the **stride**. This gives us **strided attention**.
		  
		  Thus for $p=2$ $A_i^{(1)}=\set{t,t+1,\dots, i}$ for $t=\max(0,i-l)$ and $A_i^{(2)}=\set{j:(i-j) \mod l =0}$. 
			* *Limitation*: Does not work for data without a periodic structure. 
		* Another approach is to use a **fixed attention pattern** where cells summarize previous locations.
		  
		  For $p=2$, $A_i^{(1)}=\set{j:\lfloor j/l \rfloor = \lfloor i / l \rfloor}$ and $A_i^{(2)} = \set{j:j\mod l\in\set{t,t+1,\dots, l}}$, where $t=l-c$ and $c$ is a hyperparameter. 
		  
		  Ideally we want *multiple heads attend to distinct sub-blocks of length $c$ within blocks of size $l$* rather than all heads attending to the same sub-block.
	* In order to incorporate the attention pattern to the transformer mechanism, we consider the following
		* The standard approach using **dense attention**. Let $S$ be the full connectivity pattern where $S_i$ denotes the indices of input vectors to which the $i$-th output vector attends. Define the attention pattern as follows: 
		  $$
		  \text{Attend}(X,S) = \set{x_i, S_i}_{i\in \set{1,\dots, n}}
		  $$
		* We can use *one attention type per residual block*. Let $p$ be the number of factorized attention head and $r$ the index of the current residual block.
		  $$
		  \text{Attend}(X,A^{(r\mod p)})
		  $$
		* Have a single head attend to the locations of pixels that all factorized heads would attend to. This is a **merged head**. It is more intensive than the previous by $O(1)$.
		  $$
		  \text{Attend}\left(X,\bigcup_{m=1}^p A^{(m)} \right)
		  $$
		* Use multi-headed attention with $n_h$ attention products computed in parallel and concatenated along the feature dimension.
		  $$
		  \set{\text{Attend}(X,A)^{(i)}}_{i\in\set{1,\dots,n_k}}
		  $$
		  Where $A$ is any choice of attention pattern defined previously.  The dimensions of any matrices are reduced by $n_h$ such that *the number of parameters is invariant to the number of heads*.
			* Typically better for shorter sequences. For longer sequences, the bottleneck is attention so parallelism does not yield benefits. 
	* Use [[Positional Encoding|learned positional embeddings]] rather than fixed ones. 
	* For long sequences with high memory usage, we use **gradient checkpointing**.  This means, recomputing attention and feedforward blocks during the backward pass. 

![[Sparse Transformers Attention Pattern.png]]
<figcaption> Sparse Transformers Attention Pattern . Image taken from Child, Gray, Radford and Sutskever (2019)</figcaption>

![[Sparse Transformer.png]]
<figcaption> Sparse Transformer. Image taken from Child, Gray, Radford and Sutskever (2019) </figcaption>

[^Child_2019]: Child, Gray, Radford, Sutskever (2019) [Generating Long Sequences with Sparse Transformers](https://arxiv.org/abs/1904.10509)

# Links
* [[Transformer Model]]
* [[Attention Mechanism]]