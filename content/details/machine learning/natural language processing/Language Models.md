* **Tokenization** pertains to the process of splitting a string into a sequence of small indivisible units called **tokens**.
* In general, the pipeline for language data is:
	* Clean the data (Optional depending on problem) 
		* Remove **stop words** or words that are commonly used.
		* Normalize the data -- everything should be in a consistent format
		* **Sequence Partitioning** - we partition a corpus into smaller subsequences.
		  
		  Let $T$ be the size of the corpus and $n$ the size of each $n$-grams.
		  
		  At the beginning of an epoch, discard the first $d$ tokens, where $d$ is uniformly sampled at random.
		  
		  The rest  of the sequence is then partitioned into $m=\left\lfloor\frac{T-d}{n}\right\rfloor$
	* Load inputs into memory
	* Tokenize
	* Build a vocabulary to associate each vocabulary element with a numerical index.
	* Convert the text into a sequence of numerical indices.

# Metrics
* One common metric is the **perplexity**. It is proportional to the [[Loss Function|cross entropy loss]] averaged over all $n$ tokens of a sequence. More formally 
  
  $$
  \text{PP}(x)=\exp\left(-\frac{1}{n}\sum_{i=1}^n\log(P(x_t \ | \ x_{t-1},\dots x_1 ) \right)
  $$
  The language model provides us with the conditional probability terms in the summation.

	* It is based on *assessing quality by determining how [[Information Theory|surprising]] a piece of text is*. More surprising = higher perplexity = worse.
	* From an Information Theory perspective, this corresponds to determining how many bits we need to compress a sequence to predict what is next.
	* It can be understood as the *geometric mean of the number of real choices we have when deciding which token to pick next.*

# Papers
* On Natural Language Processing and Plan Recognition by Geib and Steedman (2007)

* SQuAD -- 100 000 + Questions for Machine Comprehension for Text by Rajpurkar, Zhang, Lopyrev, and Liang (Oct 11, 2016)

* An Efficient Framework for Learning Sentence Representations by Logeswaran and Lee (2018)

* GLUE -- A Multi-Task Benchmark and Analysis Platform for Natural Language Understanding by Wang et. al (Feb 22, 2019)

* UnifiedSKG -- Unifying and Multi-Tasking Structured Knowledge Grounding with Text-to-Text Language Models by Xie et. al (Oct 18, 2022)
# Links
* [[The Transformer Model]] - more on the transformer model 
* [[Large Language Models]] - an expansion of LMs 