* A **language model** is a type of model which aims to estimate the [[Random Variables and Probability Distributions|joint probability]] that a sequence exists in some distribution.
* The modern approach for language models is  [[Time Series Analysis|autoregressive]] (also called **causal language model generation**). It models prediction by decomposing the joint probability of a sequence as follows (using the Chain rule of Probability)
  
  $$
  P(x_1,\dots,x_T)=P(x_1 ) \prod_{t=2}^TP(x_t \ | \ x_{t-1}, \dots, x_1)
  $$
  We may also simplify the above if we make use of the [[Markov Chain|Markov]] property.
  
  The goal is to then predict $x_t$ given the previous tokens in the sequence.  We refer to the previous tokens as the **context**. 

# Pipeline
* In general, the pipeline for language data is:
	* Clean the data (Optional depending on problem) 
		* Remove **stop words** or words that are commonly used.
		* Normalize the data -- everything should be in a consistent format
		* **Sequence Partitioning** - we partition a corpus into smaller subsequences.
		  
		  Let $T$ be the size of the corpus and $n$ the size of each $n$-grams.
		  
		  At the beginning of an epoch, discard the first $d$ tokens, where $d$ is uniformly sampled at random.
		  
		  The rest  of the sequence is then partitioned into $m=\left\lfloor\frac{T-d}{n}\right\rfloor$
	* Load inputs into memory
	* **Tokenization** -- this pertains to the process of splitting a string into a sequence of small indivisible units called **tokens**.
	* Build a vocabulary to associate each vocabulary element with a numerical index.
	* Convert the text into a sequence of numerical indices.

# Basic Models
## Frequency-Based Estimation
* Language models can be used to determine the conditional probability of any given word using its relative frequency in the training set. 
  
  Given words, $x$, and $y$, we have 
  $$
  P(x\ | \ y)=\frac{n(x,y)}{n(y)}
  $$
  Where $n(x,y)$ denotes the number of occurrences of $x$ and $y$ in that order.
	* Due to the number of possible arrangements an $n$-gram may have, we may find the probability above to be zero.
	* One technique to solve this is to use **Laplace Smoothing**. We add a small constant to all counts so that 
	  $$
	  P(x) = \frac{n(x) +\epsilon}{n + \epsilon}
	  $$
	  
	  This has a few drawbacks
		* Manny $n$-grams occur very rarely which makes them still unusable
		* We need to store all the counts which can get unwieldy for large vocabularies.
		* This ignores the meaning of words.
		* Long word sequences are likely to be less common


* [[Recurrent Neural Network]]
* [[Transformer Model]] - more on the transformer model 
* [[Large Language Model]] - an expansion of LMs 

# Techniques
* One technique we can employ to reduce parameters is to use **weight tying**. Assume we have an embedding layer for our language model, we make the embedding layer share its parameters with the final layer of the language model.
	* This not only reduces the parameters but also improves perplexity.
	* This is based on the insight that for next token prediction, often the embedding matrix $E$ and the final layer (sometimes denoted $E^T$) have the same dimensions (up to transposition).

* [[Language Model Sampling]]
# Papers
* On Natural Language Processing and Plan Recognition by Geib and Steedman (2007)

* SQuAD -- 100 000 + Questions for Machine Comprehension for Text by Rajpurkar, Zhang, Lopyrev, and Liang (Oct 11, 2016)

* An Efficient Framework for Learning Sentence Representations by Logeswaran and Lee (2018)

* GLUE -- A Multi-Task Benchmark and Analysis Platform for Natural Language Understanding by Wang et. al (Feb 22, 2019)

* UnifiedSKG -- Unifying and Multi-Tasking Structured Knowledge Grounding with Text-to-Text Language Models by Xie et. al (Oct 18, 2022)
# Links
* [[Metrics for Language Modeling]] 
* [[Speech and Language Processing - An Introduction to Natural Language Processing, Computational Linguistics, and Speech Recognition with Language Models by Jurafsky and Martin]]