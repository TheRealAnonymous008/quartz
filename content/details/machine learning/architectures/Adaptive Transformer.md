* [^schuster_2022] proposes **Confident Adaptive Language Modeling (CALM)** which is a calibrating method that dynamically allocates different amounts of compute per input and generation timestep.
	* Early exiting is a promising approach to decreasing the computational cost of multilayered architectures
		* CALM extends this by scoring and assigning "consistent early-exit" confidence scores after each layer. *The decision to exit is calibrated using a calibration set*. 
	* One metric is via **textual consistency** Given a bounded text dissimilarity function $\mathcal D$ and a calibration set $\mathcal{S}_{\text{cal}} = \set{P_i}$, where each $P_i$ is a prompt, we aim to *calibrate the early exiting LLM such that its predictions agree to a tolerance $\delta$ with the full model* in expectation with high probability
	  $$
	  P(\mathbb E[\mathcal D(Y_\text{early}, Y_{\text{full}})] \le \delta \mid \mathcal {S}_{\text{cal}}) \ge 1-\epsilon
	  $$
		* An adaptive LLM is **textually consistent** if given any bounded $\mathcal D$ and tolerance $\delta$, $\mathbb{E}(\mathcal D(Y_{\text{early}}, Y_{\text{full}})\le \delta$. 
		* This is doable with unlabeled calibration data.
		* The disadvantage of the above is that it may be unnecessarily strict for certain tasks.
	* We can also enforce **[[Model Performance|risk consistency]]** using prompts paired with target references $Z_i$. The calibration set $\mathcal S_{\text{cal}}=\set{(P_i,Z_i)}$ and any bounded risk function $\mathcal{R}$ gives us the following objective
	  $$
	  P(\mathbb{E}[\mathcal R(Y_{\text{early}}, Z_{\text{test}})- \mathcal{R}(Y_{\text{full}}, Z_{\text{test}})]\le \delta \mid \mathcal S_{\text{cal}}) \ge 1-\epsilon
	  $$
		* An adaptive LLM is **risk consistent** if given any $\mathcal R$ and tolerance $\delta$  $\mathbb E[\mathcal R(Y_{\text{early}}, Z_{\text{test}})]-\mathbb E[\mathcal R (Y_{\text{full}}, Z_{\text{test}})]\le \delta$.
	* For the above implicitly, $\mathcal D$ and $\mathcal R$ are assumed to be normalized between $[0,1]$ so that $\delta\in[0,1]$.
	* We choose $y_{t+1}$ by computing $P(y_{t+1}\mid d_t^i)$ where $d_t^i$ is the layer output of the $i$-th layer. 
	  
	  Let $c_t^i\in[0,1]$ denote a confidence score for layer $i$, token $t$. Let $\lambda_t^i\in[0,1]$ denote an early exiting threshold.
	  
	  The model exits early if $c_t^i\ge \lambda_t^i$. Otherwise, it compute the next representation.   
	  
	  If the model has early exited at some layer $j<i-1$ for a token $s<t$ then $d_s^{i-1}$ is not available. An approximation is to perform **state copying** we set $d_s^k=d_s^j$ for all layers $k>j$. 
		* Experiments show that the model is robust to state copying from lower layers.
		* Experiments also show that we can save compute without impacting performance given a good confidence measure.
	* Training is done for local consistency since training for global consistency could be challenging.
	  
	  The training objective is defined as the weighted average of losses for each layer. We set $\mathcal{L}_i$ to be the negative log-likelihood loss to obtain
	  $$
	  \begin{split}
	  \mathcal{L} &= \sum_{i=1}^L \omega_i\mathcal L_i \\
	  \omega_i &= \frac{i}{\sum_{j=1}^Lj}
	  \end{split}
	  $$
	  Where $\omega_i$ is configured to favor  higher layers. 
	* We have a few choices for confidence measures.
		* **Softmax Response** - take the difference between the top two values of the output logits. 
			* *Disadvantage*: Many FLOPs for large output vocabularies.
			* *Advantage*: Next layer $i+1$ can start its computation in parallel.
		* **Hidden State Saturation** - take the cosine similarity between $d_t^i$ and $d_t{i-1}$.
			* *Advantage*: Parameter free and fast. 
			* It identifies early saturation events of the hidden state. 
		* **Early Exit Classifier** - train a linear classifier to predict the likelihood of exiting with local consistency given the hidden state.
	* To choose $\lambda$ we make use of the Learn-Then-Test calibration framework from [^angelopoulos_2021].
		* We obtain the $p$-values for the framework using the empirical consistency of the early-stopping LLM measured over a random calibration sample and using Hoeffding's inequality. 
		  $$
		  p_j^H = e^{-2n (\max(0,\delta-\hat{E}(\lambda_j)))^2}
		  $$
		  Where $\hat E(\lambda_j)= \frac 1 n \sum_i L_i(\lambda_j)$ and $L_i(\lambda_j)$ depends on our consistency metric.
		* For textural consistency
		  $$
		  L_i(\lambda_j) = \mathcal D(\text{LLM}_{\text{early}} (P_i,\lambda_j) , \text{LLM}_{\text{full}}(P_i))
		  $$
		* For risk consistency
		  $$
		  L_i(\lambda_j) = \max(0, \mathcal{R}(\text{LLM}_{\text{early}}(P_i,\lambda_j), Z_i) - \mathcal{R}(\text{LLM}_{\text{full}}, Z_i))
		  $$
 

![[CALM Generation.png]]
<figcaption> CALM generation. Image taken from Schuster et al. (2022) </figcaption>

[^Schuster_2022]: Schuster et al. (2022) [Confident Adaptive Language Modeling](https://arxiv.org/abs/2207.07061)

[^Angelopoulos_2021]: Angelopoulos et al. (2021) [Learn then Test: Calibrating Predictive Algorithms to Achieve Risk Control](https://arxiv.org/abs/2110.01052)

* [^elbayad_2019] proposes **Depth Adaptive Transformer**  which can adjust the amount of computation performed per time step. 
	* *Rationale*: Large scale models are overkill for small-scale generation tasks. Prior methods apply the same amount of computation ignoring the required output scale. 
	* It extends Adaptive Computation Time (ACT) [^graves_2016] and Universal Transformers [^deghani_2018].
		* The model includes mechanisms to estimate network depth and applies a different layer each step.
	* It also borrows from **Anytime Prediction** where predictions can be done at different layers.
		* We attach output classifiers to the output $h_t^n$ of each of the decoder blocks.  Each classifier is parameterized by $W_n$ and we obtain an intermediate output as follows
		  $$
		  p(y_{t+1}\mid h_t^n) = \text{softmax}(W_nh_t^n)
		  $$
		* Dynamic computation means we can use any of the classifiers as exit points, which we denote $n_1,\dots,n_{|y|}$. We denote the exit point for the decoder as $n_t$
		* We have two options for training.
			* *Aligned Training* - all classifiers are optimized simultaneously. 
				* We assume that all previous hidden states $\set{h_1^{n-1},\dots,h_t^{n-1}}$ are available.
				  
				  The loss function per exit is then
				  $$
				  \text{LL}^n = \sum_{t=1}^{|y|}\log P(y_t\mid h_{t-1}^n)
				  $$
				  And the total loss is the weighted average of each $\text{LL}^n$. 
				  
				* At test time, the assumption fails. We instead copy the last computed state to all upper layers (with layer specific KV projections applied first). 
			* *Mixed Training* - we sample several sequences of exits and expose the model to hidden states from different layers.
				* Suppose we sample $M$ exit sequences $\set{n_1^{(m)},\dots,n_{|y|}^m}_{1\le m\le M}$. We use the following loss
				  $$
				  \text{LL}(n_1,\dots,n_{|y|}) = \sum_{t=1}^{|y|} \log P(y_t\mid h_{t-1}^{n_t})
				  $$
				  With the decoder loss being the average of the above across all $M$ sequences.
		* The distribution of exiting at time step $t$ is modeled with a parametric distribution $q_t$. The parameters of $q_t$ are optimized to match an oracle $q_t^\ast$ via cross entropy loss backpropagated to the encoder-decoder parameters. 
		* To perform adaptive depth estimation, we consider two options.
			* *Sequence specific depth* decodes all outputs using the same block. 
				* Let $W_h$ and $b_h$ be parameters for the halting mechanism. and $s_t$ be the encoder output at time $t$. We model $q$ as follows
				  $$
				  \begin{split}
				  s &= \frac{1}{|x|}  \sum_ts_t \\ 
				  q(n\mid x) &= \text{softmax}(W_hs + b_h)
				  \end{split}
				  $$
			* *Token specific depth* chooses a different exit at every time step.  We have two approaches for $q_t$
				* *Multinomial*
				  $$
				  q_t(n\mid x,y_{<t}) = \text{softmax}(W_hh_t^1 + b_h)
				  $$
				  With the most probable exit chosen at inference.
				* *Geometric-Like*
				  $$
				  \begin{split}
				  \forall n\in [1,\dots,N-1], \chi_t^n &= \sigma(w_h^Th_t^n +b_h) \\ 
				  q_t(n\mid x,y_{<t}) &= \begin{cases}
				  \chi_t^n \prod_{n'<n} (1-\chi_t^{n'}) & \text{if } n < N \\
				  \prod_{n'<N} (1-\chi_t^{n'})& \text{otherwise}
				  \end{cases}
				  \end{split}
				  $$
				  During inference, the decoder exits when the halting signal $\chi_t^n$ exceeds a hyperparameter $\tau_n$ (or if not exceeded, exit in the last block as normal)

		* Our choices for the oracle are as follows:
			* The *likelihood* of the entire sequence modeled with a [[Dirac Delta Function|Dirac Delta]] regularized to encourage lower exits that achieve good likelihood
			  $$
			  q^\ast(x,y) =\delta(\text{argmax}_n \text{LL}^n - \lambda n)
			  $$
			  This ignores whether the model already assigns the highest score to the correct target
			  
			  For Token-Specific Depth, we also smooth likelihoods with an RBF kernel since we ignore the impact of the current decision on future time steps.
			* *Correctness* based. Here we choose the block with the most number of correct tokens at time step $t$ (and for Token Specific Depth, also the surrounding tokens)

![[ADT Adaptive Depth Prediction.png]]
<figcaption> Adaptive Depth Prediction. Image taken from Elbayad, Gu, Grave, and Auli (2019) </figcaption>

[^Elbayad_2019]: Elbayad, Gu, Grave, Auli (2019) [Depth Adaptive Transformer](https://arxiv.org/abs/1910.10073)

* [^sukhbaatar_2019] proposes a self-attention mechanism that can *learn its optimal attention span*
	* *Rationale*: [[Attention Mechanism|Attention]] is costly, especially for large context windows. 
	* Each head independently learns its attention span $S$. 
	  
	  For each head, we add a masking function to control the span of attention. The masking function normalizes distance (i.e., it is of the form $\mathbb{R}\to[0,1]$).
	  
	  Our choice of function is the following (parameterized by $z$)
	  $$
	  m_z(x) = \text{clip}\left(\frac{1}{R}(R+z-x), 0, 1\right)
	  $$
	  Where $R$ is a hyperparameter controlling softness.
	* The attention weights are computed with the masked span as follows
	  $$
	  A_{ij} = \frac{m_z(i-j)\exp (A_{ij})}{\sum_{k=i-S}^{i-1} m_z(i-k)\exp(A_{ik})}
	  $$
	* We add an L1 penalty on the parameters $z_i$ for each attention head $i$ of the model to the loss function
	  $$
	  L = -\log P(w_1,\dots,s_L) + \frac{\lambda}{M}\sum_i z_i
	  $$
	* To extend it further, we can make $z$ a function
	  $$
	  z_t = S\sigma (vx^T + b)
	  $$
	  Where $v,b$ are learnable parameters. 
	* *Result*: Lower layers do not require long attention spans. Higher layers may use longer attention spans.
	* Adaptive attention span can reduce the number of FLOPs.

[^Sukhbaatar_2019]: Sukhbaatar, Grave, Bojanowski, and Joulin (2019) [Adaptive Attention Span in Transformers](https://arxiv.org/abs/1905.07799)

[^Graves_2016]: Graves (2016) [Adaptive Computation Time for Recurrent Neural Networks](https://arxiv.org/abs/1603.08983)

[^Deghani_2018]: Deghani et al. (2019) [Universal Transformers](https://arxiv.org/abs/1807.03819)

# Links
* [[Transformer Model]]