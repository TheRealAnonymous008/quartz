# Sequential Data
* When working with sequences, we assume the following
	* **Non-IID assumption**: The standard IID assumption does not hold for our datapoints. The data points are not necessarily independent of others in the sequence. Instead, we assume that *sequences are sampled independent of each other*
	* **[[Pathologies of Deep Learning#Nonstationarity|Stationarity]]**: The sequential data is stationary if while the specific values within the sequence might change, the dynamics to which these observations do not. 
	* **Markov Assumption**: The data is [[Markov Chain|Markovian]]

* For sequential data, we often *consider the sequence in the natural reading order for a few reasons.*
	* It is the most natural direction for us to think in.
	* Factoring in order allows us to assign probabilities to long sequences using the same model by exploiting the structure of order.
	*  The ordering gives us models since there is a structure. It is not just words placed randomly.


# Tasks
* One task common task is **$K$-step ahead prediction**. 
   
   Let $\{x_1, \dots, x_T\}$ be a sequence of data points. The $k$-steps ahead prediction task asks us to predict $x_{T+k}$.
   
   This is achieved by using a model where we input $\{x_{T+k-1}, \dots\}$, where we obtain $x_{T+k-1}, \dots, x_{T+1}$ using the same model.

* Another task is called **Unsupervised Density Modelling** which may be formulated as follows:
  
  Given a collection of sequential data, estimate the [[Random Variables and Probability Distributions|probability mass function]] that tells us how likely we are to see any given sequence in this collection

# Topics
* [[Recurrent Neural Network]]
* [[Time Series Analysis]]
* [[Transformer Model]]
* [[Language Model]]
* [[Encoder-Decoder Network]]
# Links
* [C5W3LO4 Beam Search](https://www.youtube.com/watch?v=RLWuzLLSIgw) - beam search is an algorithm similar to BFS and DFS (but is not guaranteed to find maxima), wherein given beam length $B$, we select the top $B$ likely outputs at each step of the search. The goal is to find the likely $B$-length sentence using this search.
* [C5W3LO4 Refining Beam Search](https://www.youtube.com/watch?v=gb__z7LlN_4) - use length normalization techniques to optimize beam search (maximize log likelihood, average based on sentence length).