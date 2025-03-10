* **Positional Encoding** is done to account for the fact the order tokens appear in sequence is important
	* The original positional encoding proposed encodes both the absolute position of a token, and its position relative to other tokens.  *For any fixed offset $\delta$, the positional encoding at $i+\delta$ can be obtained through linear [[Projection|projection]] of $\delta$ at $i$.*
	* An ideal positional encoding has the following properties [^rope_1]
		* Unique encoding for each position across sequences regardless of sequence length.
		* [[Linear Combination|Linear]] relation between two encoded positions (for simplicity). 
		* [[Pathologies of Deep Learning|Generalizable]] to longer sequences than those encountered in training.
		* Deterministically generated
		* Extensible to multiple dimensions.

* *Position encoding can either be applied to only the first input, or in every layer. The latter tends to be  more performance*. 

* The positional encoding $P\in\mathbb{R}^{L\times d}$  is applied to $X$ as follows
  $$
  X+P
  $$

* **Sinusoidal Positional Embedding**  constructs the embedding as follows
  $$
  P_{ij} =\begin{cases}
  \sin\left(\frac{i}{10000^{2k/d}}\right) & \text{if } j=2k \\ 
  \cos\left(\frac{i}{10000^{2k/d}}\right) & \text{if } j = 2k+1
  \end{cases}
  $$

* **Learned Positional Encoding** involves treating $P$ as a trainable matrix. We can treat layers as having shared or independent positional encoding matrices.



*  **Rotary Position Embedding (RoPE)** [^su_2021] *encodes the absolute position with a rotation matrix* while incorporating explicit relative position dependency. 
	* We formulate the [[Inner Product Space|inner product]] of $q_m$ and $k_n$ such that it is a function $g$ only dependent on the word embeddings $x_m,x_n\in \mathbb{R}^d$ and the relative distance $m-n$ .  Thus
	  $$
	  \braket{f_q(x_m,m) , f_k(x_n,n)} = g(x_m,x_n,m-n)
	  $$
	* Consider the simpler case of $d=2$ dimensional embeddings.  By our stipulation 
	  $$
	  q_mk_n^T = \braket{f_q(x_m,m), f_k(x_n,n)} = g(x_m,x_n,n-m)
	  $$
	  Further assume we have the initial conditions with no position information encoded.
	  $$
	  \begin{split}
	  q&=f_q(x_q,0)\\
	  k&= f_k(x_k, 0)
	  \end{split}
	  $$
	  We use [[Complex Numbers and Quaternions|Complex numbers]] to represent the $2D$ vectors. Let $R_z$ and $\Theta_z$ denote the radial and angular components of $z$. Then we note that we can rewrite $z=R_z e^{i\Theta_z)}$. Applying this to $f$ and $g$ we get the relations
	  $$
	  \begin{split}
	  R_q(x_q,m) R_k(x_k,n) &= R_g(x_q,x_k,n-m) \\
	  \Theta_k(x_k,n) -\Theta(x_q,m) &= \Theta_g(x_q,x_k,n-m) \\ 
	  q&= \|q\|e^{i\theta_q} \\
	  k &= \|k\|e^{i\theta_k}
	  \end{split}
	  $$
	  Where $\|q\|=R_q(x_q,0)$  and $\|k\|=R_k(x_k,0)$.
	  
	  We can find a solution by setting $m=n$.  This gives us
	  $$
	  \begin{split}
	  R_q(x_q,m) R_k(x_k,m) &= R_g(x_q,x_k,0) &= R_q(x_q,0) R_k(x_k,0) &= \|q\| \cdot \|k\| \\
	  \Theta_k(x_k,m) - \Theta_q(x_q,m) &= \Theta_g(x_q,x_k,0) &= \Theta_k(x_k,0)-\Theta_q(x_q,0) &= \theta_k-\theta_q
	  \end{split}
	  $$
	  One solution could therefore be to set $R_q(x_q,m)=||q||$ and $R_k(x_k,n)=||k||$. Thus *the radial functions are independent from position*.
	  
	  Furthermore, since $\Theta_q(x_q,m)-\theta_q=\Theta_k(x_k,m)-\theta_k$ *the angular functions do not depend on the query and the key* so we simply set $\Theta_f=\Theta_q=\Theta_k$.  We have
	  $$
	  \Theta_f(x_q,x_k,m) + \theta_q-\theta_k = \phi(m) +\theta_q-\theta_k
	  $$
	  For some function $\phi(m)$.
	  
	  Also setting $n=m+1$ 
	  $$
	  \phi(m+1)-\phi(m) = \Theta_g(x_q,x_k,1) + \theta_q-\theta_k
	  $$
	  Thus $\phi(m)$ must  be linear. Using $\theta,\gamma\in\mathbb{R}$, and $\theta\ne 0$. 
	  $$
	  \phi(m)=m\theta + \gamma
	  $$
	  Let us set $\gamma = 0$ , $q=x_mW^q$ and $k=x_nW^k$. The final solution is 
	  $$
	  \begin{split}
	  f_q(x_m,m) &= (x_mW^q)e^{im\theta} \\
	  f_k(x_n,n) &= (x_nW^k)e^{in\theta} 
	  
	  \end{split}
	  $$
	  Therefore
	  $$
	  g(x_m,x_n,m-n) = \text{Re}(x_mW_q (x_nW_k)^\ast e^{i(m-n)\theta})
	  $$
	  Where $z^\ast$ denotes complex conjugation. .
	* We can represent the solution using a rotation matrix of the form
	  $$
	  \begin{bmatrix}
	  \cos m\theta & \sin m \theta \\
	  -\sin m\theta & \cos m \theta
	  \end{bmatrix}
	  $$
	* In the general form where $x_i\in\mathbb{R}^{d}$, where $d$ is even. We divide the space into $d/2$ [[Vector Subspace|subspaces]] and by linearity, $f$ (for both $q$ and $k$) is of the form
	  $$
	  f (x_m,m) = x WR_{\Theta,m}^{d_k}
	  $$
	  Where
	  $$
	  R_{\Theta,m}^{d_k} = 
	  \begin{bmatrix}
	  R^m_1 & O  & \cdots & O \\
	  O & R^m_2 & \cdots & O \\
	  \vdots & \vdots & \ddots & O \\
	  O & O & \cdots & R^m_{d_k/2} 
	  \end{bmatrix}
	  $$
	  And 
	  $$
	  R^m_i = \begin{bmatrix}
	  \cos m\theta_i & -\sin m \theta_i \\
	  \sin m\theta_i & \cos m \theta_i
	  \end{bmatrix} 
	  $$
	  The inner product is therefore
	  $$
	  q_m k_n^T = (x_m W^qR_{\Theta,m}^{d_k})(x_n W^k R_{\Theta,n}^{d_k})^T = x_m^T W^q R^{d_k}_{\Theta, n-m} W^k x_n
	  $$
	* For completeness, set $\theta_i=10000^{-2i/d}$.  Intuitively *tokens do not influence other tokens that are relatively far away*. 
	* Because $R_{\Theta,m}^d$ is sparse, we can perform multiplication with it uses the Hadamard product as follows
	  $$
	  R_{\Theta,m}^d x= \begin{bmatrix}
	  x_1 \\ x_2 \\ x_3 \\ x_4 \\ \vdots \\ x_{d-1} \\ x_d
	  \end{bmatrix}
	  
	  \odot 
	  \begin{bmatrix}
	  \cos m\theta_1 \\ \cos m \theta_1 \\ \cos m\theta_2 \\ \cos m \theta_2 \\ \vdots \\ \cos m \theta_{d/2} \\ \cos m \theta_{d/2}
	  \end{bmatrix} + \begin{bmatrix}
	  -x_2 \\ x_1 \\ -x_4 \\ x_3 \\ \vdots \\ -x_{d} \\ x_{d-1}
	  \end{bmatrix} \odot
	  \begin{bmatrix}
	  \sin m\theta_1 \\ \sin m \theta_1 \\ \sin m\theta_2 \\ \sin m \theta_2 \\ \vdots \\ \sin m \theta_{d/2} \\ \sin m \theta_{d/2}
	  \end{bmatrix}
	  $$

	* Notice *we do not add position information to the values*. 
	* One main challenge with RoPE is [[Extending Context in Transformers|extrapolation]].



![[RoPE.png]]
<figcaption> Rotary Position Embedding. Image taken from Su et al. (2021) </figcaption>

[^Su_2021]: Su et al. (2021) [RoFormer: Enhanced Transformer with Rotary Position Embedding](https://arxiv.org/abs/2104.09864)
[^rope_1]: RoPE has all these properties. See https://huggingface.co/blog/designing-positional-encoding

* [^dai_2019] proposes a modified relative positional encoding for use in models that have extended context lengths. 

  We  use the following decomposition. Let $x_i\in\mathbb{R}^d$ be the $i$-th row of $X$. 
  $$
  \begin{split}
  q_ik_j^T&= (x_i+p_i)W^qW^{kT} (x_j+p_j)^T \\
  &= x_iW^qW^{kT} x_j^T + x_iW^qW^{kT}p_j^T + p_iW^qW^{kT}x_j ^T + p_jW^qW^{kT}p_j^T
  \end{split}
  $$
  We perform the following reparameterization
	* Replace $p_j\in\mathbb{R}^d$ with $r_{i-j}^\mathbb{d}$ where $R$ corresponds to the sinusoidal position embedding. *Only the relative distance matters for where to attend*
	* Replace $p_iW^q$ with trainable parameters for $u$ and $v$ corresponding to content and location respectively. 
		* Since the query vector is the same for all query positions, the bias should remain the same regardless of query positions.
	* Split $W^k$ to $W^k_E$ and $W^k_R$ for content and local information.
	* The final reparameterization now looks like
	  $$
	  q_ik_j^T  = x_i W^q W_E^{kT} x_j^T + x_iW^qW^{kT}_Rr_{i-j}^T + uW^k_Ex_j^T + vW_R^kr_{i-j}^T
	  $$
		* The first term corresponds to *content-based addressing*
		* The second term corresponds to *content-dependent positional bias*.
		* The third term corresponds to *global content bias*
		* The fourth term correspond to *global positional bias*

[^Dai_2019]:: Dai et al. (2019) [Transformer-XL: Attentive Language Models Beyond a Fixed-Length Context](https://arxiv.org/abs/1901.02860)


* [^shaw_2018]  introduces relative positional encoding. 
	* *Rationale*: This is one approach to consider arbitrary pairwise relations between any two input tokens. We treat the input as a labeled fully connected [[Directed Graph|digraph]]. 
	* The edge between input elements $x_i, x_j$ is represented by the vectors $P_{ij}^v,P_{ij}^k$. We apply the positional embedding by modifying the key-value matrices
	  $$
	  \begin{split}
	  K &= XW^k + P^k \\
	  V &= XW^v + P^v 
	  \end{split}
	  $$
	* We clip the maximum distance to a maximum absolute value $k$
		* *Rationale*:  This lets us generalize to sequence lengths not seen in training. Also it is hypothesized that previse positional information is not useful beyond a certain distance. 
		* We consider $2k+1$ edge labels (within the interval $[-k,k]$).   We then obtain
		  $$
		  \begin{split}
		  P_{ij}^k &= w^k_{\text{clip}(j-i,k)}\\
		  P_{ij}^v &= w^v_{\text{clip}(j-i,j)} 
		  \end{split}
		  $$
		  Where $\text{clip}(x,k)=\text{clip}(x,-k,k)$. 
		  
		  $w^k$ and $w^v$ are then treated as learnable training parameters. 
		* For efficiency, we share the relative position encoding either across heads or across sequences
	* When computing the scaled dot product, we separate the computation and perform tensor reshaping on the second term in the following
	  $$
	  q_ik_j^T = x_iW^qW^{kT}x_j^T + x_iW^qP^{kT}_{ij}
	  $$
	  The computation for the output using $V$ is done similarly, separating $XW^v$ and $P^v$ and reshaping the term corresponding to $P^v$. 

[^Shaw_2018]:  Shaw, Uszkoreit, Vaswani (2018) [Self-Attention with Relative Position Representations](https://arxiv.org/abs/1803.02155)

# Incorporating Long Contexts

* **Attention with Linear Biases (ALiBi)** [^press_2021]  proposes a position encoding method where we add a bias for query-key attention scores with a penalty proportional to their distance. 
	* The authors speculate that the failure to [[Extending Context in Transformers|extrapolate]] is due to the choice of positional encoding used.
	* Using ALiBi entails training the model on short sequences. Thus, training incurs lower cost.
	* ALiBi simply entails modifying the [[Attention Mechanism|attention]] mechanism by introducing a static, non-learned bias. For the $i$-th query, we perform 
	  $$
	  A_i=q_iK^T + m\cdot \begin{bmatrix}
	  -(i-1),\dots, -2, -1, 0
	  \end{bmatrix}
	  $$
	  Where $m$ is a head specific sloping parameter.
		* The paper uses a geometric sequence for $m$. So for $n$ heads we have $m_k=\frac{1}{2^k}$

	* ALiBi has an inductive bias towards recency.  The penalty decreases as the distance between a key and query diminishes.
	* ALiBi's decrease in perplexity when given longer sequences is largely explained by its improved avoidance of the early token curse 
	* *Limitation*: When using a larger context during validation, ALiBi might not actually be using contexts longer than the one it was trained on. 

[^Press_2021]: Press, Smith, Lewis (2021) [Train Short, Test Long: Attention with Linear Biases Enables Input Length Extrapolation](https://arxiv.org/abs/2108.12409v2)


* [^wu_2021] propose the **DA-Transformer (distance aware transformer)** which incorporates the real distance between tokens in re-scaling raw self-attention weights. 
	* *Rationale*: Global and local context modelling usually have different distance preferences for attention. 
	* In each attention head, we use a learnable parameter $w_i$ to weight the relative distance. Let $R$ be the relative distance matrix where $R_{ij}=|i-j|$ then 
	  $$
	  R^{(i)} =w_i R
	  $$
	  It is stipulated that $R^{(i)}$ being  more positive favors long-distance information, while it being more negative favors short-term context.
	* We then design a function $f$ to obtain the rescaled coefficients $\hat R^{(i)} = f(R^{(i)})$. The function satisfies.
		* $f(0)=1$ since zero distance does not influence attention weights.
		* $\lim_{R^{(i)}\to -\infty} f(R^{(i)})=0$. If attention prefers local information, the long-distance information should be surpassed.
		* $\lim_{R^{(i)}\to\infty}f (R^{(i)})\le c$. We introduce this bound so that the model can process long sequences without over-emphasizing distance contexts.
		* The scale of $f$ is tunable to adjust the intensity of distance information.
		* $f$ is monotone.
	* Our choice for $f$ is a learnable sigmoid function
	  $$
	  f(R^{(i)}; v_i) = \frac{1+\exp(v_i)}{1+\exp(v_i-R^{(i)})}
	  $$
	  Where $v_i$ is a head-specific learnable parameter. 
	* The re-scaled coefficients are used to adjust the attention weights. We obtain the attention matrix as follows
	  $$
	  A=\text{softmax}\left(\frac{\text{ReLU} (Q^{(i)}K^{(i)T}) \odot \hat R^{(i)}}{\sqrt d}\right)
	  $$
		* The scaling is multiplicative since adding might over-amplify the attention weights.
		* The ReLU is incorporated since the sign of $QK^T$ can be both positive and negative. Thus, multiplication does not reflect distance information.
		* ReLU also adds sparsity since only positive attention is amplified.
	* The extra time and space complexity for computing the above is $O(L^2)$ and $O(2h)$ respectively. 

[^Wu_2021]: Wu, Wu, Huang (2021) [DA-transformer: Distance Aware Transformer](https://aclanthology.org/2021.naacl-main.166/)



# Links
* [[Dive into Deep Learning by Zhang, Lipton, Li and Smola|Zhang et. al Ch. 11]] - for everything about the basics of the transformer model.
* [All about Attention](https://lilianweng.github.io/posts/2018-06-24-attention/) - more about attention

* [The Transformer Family v2.0 by Lilian Weng](https://lilianweng.github.io/posts/2023-01-27-the-transformer-family-v2/)
* [[Transformer Model]]