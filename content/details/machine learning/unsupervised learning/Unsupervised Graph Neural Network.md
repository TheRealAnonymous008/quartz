## VGAE
* **Variational Graph Autoencoders (VGAE)** apply the techniques from [[Variational Autoencoder|VAEs]] to graphs. 
* Each node in the graph is associated with a feature encoded in matrix $X\in\mathbb{R}^{|V|\times C}$ matrix). Each node is also associated with a latent variable encoded in matrix $Z\in\mathbb{R}^{|V|\times F}$. *The goal is to infer latent variables and decode edges*
* We have the following components.
	* An **encoder** to learn the latent variable distribution. We denote this as $q_\theta(Z\mid A,X)$. We assume nodes are independent.
	  $$
	  \begin{split}
	  q_\phi (Z\mid X,A) &= \prod_{i=1}^{|V|} q_\phi(z_i\mid X,A) \\
	  q_\phi(z_i \mid X,A) &= \mathcal{N}(z_i \mid \mu_i,  \text{diag}(\sigma_i^2)) \\
	  \mu,\sigma &\sim \text{GCN}_\phi(X,A)
	  \end{split}
	  $$
	  Where $\mathcal{N}$ is the [[Probability Distributions Zoo|Normal Distribution]] and $\text{GCN}$ denotes a [[#Graph Convolutional Network|GCN]].  The prediction is done using
	  $$
	  \begin{split}
	  \mu &= \overline{A} HW_\mu \\
	  \sigma &= \overline{A} HW_\sigma \\
	  H &= \text{ReLU} (\overline A XW_0)
	  \end{split}
	  $$
	  Each $W$ is a learnable parameter.
	* A **decoder** to predict connections between nodes given latent variables. We denote this as $p(A\mid Z)$. We assume conditional independence among possible edges for tractability.  The decoder has no learnable parameters.
	  $$
	  \begin{split}
	  p(A\mid Z) &= \prod_{i=1}^{|V|}\prod_{j=1}^{|V|} p(A_{ij} \mid z_i, z_j) \\
	  p(A_{ij}\mid z_i, z_j) &= \sigma(z_i^T z_j )
	  \end{split}
	  $$
	* The **prior distribution** of latent variables is set to the standard Gaussian. That is
	  $$
	  p(Z) = \prod_{i=1}^{|V|} \mathcal{N} (z_i\mid 0,Is)
	  $$

* The objective is  to learn the following 
  $$ 
  L_\text{ELBO} = \mathbb{E}_{q_\phi(Z\mid X,A)} \left[\log(p(A\mid Z) - \text{KL}(q_\phi(Z\mid X,A) \mid\mid p(Z) \right]
  $$ 
  * The model is lightweight. All parameters are on the encoder. 
  * Some downsides include
	  * Learning latent representations is not a guarantee of performance.
	  * The assumption of independence may be limiting. 
	  * The [[Bayesian Models|prior]] distribution may be a poor choice
	  * Need to account for the sparsity of the graph in the decoder. 
## Deep Graph Infomax
* **Deep Graph Infomax** aims to maximize [[Information Theory|mutual information]] as possible between the latent representation of nodes (local information) and the latent representation of the graph (global information).
* Node representations are obtained using an encoder $\varepsilon$. We have
  $$
  H = \varepsilon(X,A)
  $$
  The local representation for nodes $h_i$ contains local information near node $i$. (i.e., information is passed between neighbors that are $k$ steps away)
  
  Similarly for the graph representation, we use a readout function $R$ (i.e., pooling) such that
  $$
  s = R(H) 
  $$

* Let $\mathcal{C}$ be a classifier that predicts whether $h_i$ and $s$ comes from a [[Contrastive Learning|positive sample]] or a negative sample. Let $N^+$ and $N^-$ be the number of positive and negative samples respectively.  Also let $\overline{h}_j$ e the $j$-th node representation from the negative sample.
  
  The objective is negative binary cross entropy.
  $$
  L = \frac{1}{N+M} \left(\sum_{i=1}^N \mathbb{E} _{(X,A)} \left[\log \mathcal{C}(h_i, s\right] + \sum_{i=1}^M \mathbb{E}_{(\overline{X}, \overline A)} \left[\log (1-\mathcal{C}(\overline h_j, s)\right]\right)
  $$

* We perform positive sampling by sampling nodes from the graph to obtain $(h_i,s)$
* We perform negative sampling using a corruptor function $\mathcal{L}$. applied to the graph data as follows
  $$
  \overline X,\overline A=\mathcal{L}(X,A)
  $$

# Links
* [[Graph Neural Networks -- Foundations, Frontiers and Applications by Wu et al.]]