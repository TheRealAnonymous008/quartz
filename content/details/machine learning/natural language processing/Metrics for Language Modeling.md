* One common metric is the **perplexity**. It is proportional to the [[Loss Function|cross entropy loss]] averaged over all $n$ tokens of a sequence. More formally 
  
  $$
  \text{PP}(x)=\exp\left(-\frac{1}{n}\sum_{i=1}^n\log(P(x_t \ | \ x_{t-1},\dots x_1 ) \right)
  $$
  The language model provides us with the conditional probability terms in the summation.

	* It is based on *assessing quality by determining how [[Information Theory|surprising]] a piece of text is*. More surprising = higher perplexity = worse.
	* From an Information Theory perspective, this corresponds to determining how many bits we need to compress a sequence to predict what is next.
	* It can be understood as the *geometric mean of the number of real choices we have when deciding which token to pick next.*

* The **Brevity Penalty** is a penalty that punishes candidate strings that are too short.
  
  Let 
  $\hat{S} = \{\hat{y}^{(1)}, \dots \hat{y}^{(M)}\}$ be a set of candidate strings
  $S_i = \{y^{(i, 1)} \dots, y^{(i, N_i)}\}$ be a set of reference strings for the $i$-th candidate string.
  $S = \{S_1, \dots, S_M\}$.
  
  The brevity penalty is defined as $$\text{BP}(\hat{S} \ ; \ S):=e^{-\max(0, \frac{r}{c}-1)}$$We define $r$ and $c$ as follows.
  
  $c$ is the length of the candidate corpus. That is 
  $$
  c:=\sum_{i=1}^M\left|\hat{y}^{(i)}\right|
  $$
  
  $r$ is the effective reference corpus length, defined as
  $$
  r:=\sum_{i=1}^M\left|\arg\min_{y\in S_i} \left(||y| -|\hat{y}^{(i)}||\right)\right|
  $$
  
  That is, for each entry in the candidate corpus, we find the sentence from $S_i$ (the set of corresponding reference strings), whose length is as close as possible to $\hat{y}^{(i)}$ as possible. 

* The **$n$-gram Precision** tells us *how many instances of an $n$-gram from the candidate string appear in the reference string* [^n-gram_prec]. 
  
  However note that it does not take into account the fact that we may have too many $n$-grams in the candidate string compared to the reference string.
  
  It is computed as follows. Let
  $\hat{y}$ be a candidate string
  $y$ be a reference string
  $G_n(x)$ be the number of $n$-grams in a string $x$.
  $\delta(x,y)$ be a modification of the Kronecker Delta function where it is $1$ if $x$ is a substring of $y$ and $0$ otherwise.
  
  The n-gram precision is defined as
  $$
  p_n(\hat{y},y)=\frac{\sum_{s\in G_n(\hat{y})}\delta(s,y)}{|G_n(\hat{y})|}
  $$




[^n-gram_prec]: Analogous to [[Model Performance#Precision-Recall|precision]]. 

* The **Modified $n$-gram precision** is defined similarly to the regular $n$-gram precision.
  
  Let
  $\hat{y}$ be a candidate string
  $y$ be a reference string
  $G_n(x)$ be the number of $n$-grams  in a string $x$.
  $C(x,y)$ be the number of times $x$ occurs as a substring of $y$.
  
  The modified $n$-gram precision is defined as
  $$
  p_n(\hat{y},y)=\frac{\sum_{s\in G_n(\hat{y})}\min\left(C(s,\hat{y}), C(s,y)\right)}{\sum_{s\in G_n(\hat{y}) }C(s,\hat{y})}
  $$
	* If $p_n=0$, then none of the substrings in the candidate are in the reference.
	* If $p_n=1$, then every $n$-gram in the substring appears in the reference for at least as many times as that in the candidate.
	* *Intuition*: Begin by measuring how many instances of the $n$-grams in the candidate appear in the reference string. This is done in the expression 
	  $$
	  \sum_{s\in G_n(\hat{y})}C(s,y)
	  $$
	  
	  If we encounter duplicates (i.e., $y=\text{ababab}, \hat{y}=\text{ab}$), we count each duplicate.
	  
	  However, we need to keep in mind the case where the candidate string is too short. This is rectified by adding a minimum function $${\sum_{s\in G_n(\hat{y})}\min\left(C(s,\hat{y}), C(s,y)\right)}$$Essentially, what this does is determine the number of common substrings (allowing duplicates) that appear in both the candidate and the reference. 
	  
	  Finally, we obtain the denominator in $p_n$ simply by normalizing the expression above.
	* If we have an entire corpus $\hat{S}$ of candidates and $S=\{S_1,\dots, S_M\}$ where  $S_i$ is the set of reference strings for the $i$-th candidate string and $|\hat{S}| = M$, then we can extend the definition to apply to a corpus. 
	  
	  $$
	  p_n(\hat{S} ; S) = \frac{\sum_{i=1}^M \sum_{s\in
	  G_n(\hat{y}^{(i)})} \min\left(C(s,
	  \hat{y}^{(i)}\right), \max_{y\in
	  S_i}\left(C(s,y)\right)}
	  {\sum_{i=1}^M \sum_{s\in G_n(\hat{y}^{(i)})} C(s, \hat{y}^{(i)})}
	  $$


* The **Bilingual Evaluation Understudy** is a performance metric that allows us to evaluate the probability that an $n$-gram appears in a target sequence.
  
  Let 
  $\hat{S} = \{\hat{y}^{(1)}, \dots \hat{y}^{(M)}\}$ be a set of candidate strings
  $S_i = \{y^{(i, 1)} \dots, y^{(i, N_i)}\}$ be a set of reference strings for the $i$-th candidate string.
  $S = \{S_1, \dots, S_M\}$.
  $p_n$ be the modified $n$-gram precision
  $\text{BP}(\hat{S} ; S)$ denote the brevity penalty
  ${w} = \{w_1,w_2,\dots\}$ be a weighting vector whose entries are all sampled from a probability distribution (i.e., the sum of all weights is $1$).  This is chosen by us. 
  
  The Bilingual Evaluation Understudy is defined as 
  $$
  \text{BLEU}_w(\hat{S}\ ; \ S) := \text{BP}(\hat{S} ; S) \cdot \exp\left(\sum_{n=1}^\infty w_n \ln p_n(\hat{S} \ ; \ S) \right)
  $$
