* Sampling in the context of NLP refers to the procedure we use to generate the next token.
* Sampling inherently has a [[The Exploitation-Exploration Trade-Off|Exploration-Exploitation tradeoff]]. 
	* High exploration would mean more **diverse** outputs at the cost of quality, cohesion, and truthfulness
	* High exploitation would mean higher **quality** outputs at the cost of diversity and creativity.
  
* Let $w_t$ be the current word and $w_{<t}$ be the context. Also let $V$ be the vocabulary of tokens.

* **[[Greedy Algorithm|Greedy]] Decoding** involves generating the most likely word given the context. That is,
  $$
  w_t =\text{argmax}_{w\in V} P(w\mid w_{<t})
  $$
	* *Limitation*: Deterministic. The resulting text is thus generic.

* **Random Sampling** involves choosing randomly based on the resulting [[Random Variables and Probability Distributions|probability distribution]]. Thus
  $$
  w_t \sim P(w_t\mid w_{<t})
  $$
	* *Limitation*: This will still pick rare words that are very unlikely to make the generated text sensible. While one rare word on its own has low probability, this is offset by having many rare words.  

* **Top-k sampling** generalizes greedy decoding [^topk]. 
	* We do the following:
		* Choose hyperparameter $k$. 
		* Choose the top $k$ words based on the probability distribution $P(w_t\mid w_{<t})$. 
		* Truncate the distribution to only include the top $k$ words.
		* Renormalize the distribution
		* Sample from the renormalized distribution. 
	* *Limitation:* This implicitly assumes that the conditional probability distributions are of the same shape regardless of context. 
	  
	  However, this is not necessarily the case as the top-k choices might constitute only a small probability mass.

[^topk]: When $k=1$, top-k sampling degenerates to greedy sampling.

* **Nucleus / Top-p sampling** improves top-k sampling by instead choosing based on the top $p\%$ of the probability mass distribution.  
	* The top $p$ vocabulary $V^{(p)}$ is the smallest non-empty set of tokens such that 
	  $$
	  \sum_{w\in V^{(p)}} P(w\mid w_{<t}) \ge p
	  $$
	  We sample from the top $p$ vocabulary.
	* By using probabilities instead of just the top $k$ words, we have a sampling method that is more robust against changes in context. 

* **Temperature Sampling** involves reshaping the distribution rather than truncating it. 
	* We introduce the [[Thermodynamics|temperature]] parameter $\tau$ which controls this reshaping process.
	* We apply the temperature parameter prior to softmax. The distribution $y$ is then obtained as
	  $$
	  y= \text{softmax}\left(\frac u \tau\right)
	  $$
	* When $\tau$ is close to $1$, the distribution doesn't change.
	* When $\tau \le 1$, we give more weight to more likely words and less weight to less likely words. 
	  
	  As $\tau\to 0$, the most likely word is given probability $\to 1$. 
	* When $\tau>1$, we give less weight to more likely words and more weight to less likely words.
	  
	  As $\tau\to\infty$ the distribution becomes more uniform. 


* [C5W3LO4 Beam Search](https://www.youtube.com/watch?v=RLWuzLLSIgw) - beam search is an algorithm similar to BFS and DFS (but is not guaranteed to find maxima), wherein given beam length $B$, we select the top $B$ likely outputs at each step of the search. The goal is to find the likely $B$-length sentence using this search.
* [C5W3LO4 Refining Beam Search](https://www.youtube.com/watch?v=gb__z7LlN_4) - use length normalization techniques to optimize beam search (maximize log likelihood, average based on sentence length).
# Links
* [[Speech and Language Processing - An Introduction to Natural Language Processing, Computational Linguistics, and Speech Recognition with Language Models by Jurafsky and Martin]]

* [[Large Language Model]]