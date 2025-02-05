* **Contrastive Learning** is a technique for [[Unsupervised Learning|unsupervised]] [[Representation Learning|representation learning]].


* We frame the problem as follows. Let $\set{x_i}$ be the input samples each with label $y_i\in\set{1,\dots,L}$ belonging to one of $L$ classes. 
  
  The goal is to learn an embedding function $f_\theta(\cdot) : \mathcal{X}\to\mathbb{R}^d$ such that *similar instances are close together and dissimilar instances are far apart*

# Training Objectives
* For the following:  $||\cdot||_2$ denotes the L2 norm [^cont_loss] . For a provided input, a positive sample is one from the same class and a negative sample from different class. 
  
  We give various [[Loss Function|loss functions]] that can be used in the setting.

* The **Contrastive Loss** is defined as follows
  $$
  \mathcal{L}(x_i,x_j\mid \theta) = \mathbb{1}[y_i=y_j]||f_\theta(x_i) - f_\theta(x_j)||^2_2 + \mathbb{1}[y_i\ne y_j]\max(0, \epsilon -||f_\theta(x_i) - f_\theta(x_j)||_2)^2  
  $$
  Where $\epsilon$ defines the lower bound distance between different samples.

[^cont_loss]: In theory, we can replace this with any [[Inner Product Space|norm]] we please. 

* The **Triplet Loss** is defined as follows.  Select an anchor point $x$ and samples $x^+,x^-$ which are positive and negative respectively (preferably choose challenging samples).
  
  The goal is to minimize the distance between $x$ and $x^+$ and maximize the distance between $x$ and $x^-$
  
  $$
  \mathcal{L}(x,x^+,x^-) = \sum_{x\in\mathcal{X}} \max(0, ||f(x) - f(x^+)|| ^2 _2 - ||f(x) - f(x^-)||_2^2 + \epsilon)
  $$

* **Lifted Structure Loss** uses all pairwise edges.  For convenience, let $d_{ij}= ||f(x_i)-f(x_j)||_2$ and denote $\mathcal{P}, \mathcal{N}$ as the set of positive and negative sample pairs respectively. Then:
  $$
  \begin{split}
  \mathcal{L} &= \frac{1}{2|\mathcal{P}|} \sum_{(i,j)\in \mathcal{P}} \max(0,\mathcal{L}^{(ij)})^2 \\
  \mathcal{L}^{(ij)} &=  d_{ij} + \max\left(\max_{(i,k)\in \mathcal{N}} \epsilon-d_{ik}, \max_{(j,l)\in\mathcal{N}} \epsilon - d_{jl}\right) \\
  &\approx d_{ij} + \log\left(\sum_{(i,k)\in\mathcal{N}} \exp(\epsilon-d_{ik}) + \sum_{(j,l)\in\mathcal{N}} \exp(\epsilon-d_{jl})\right)  
  \end{split} 
  $$
  The last  equation above is a smooth relaxation of $\mathcal{L}^{(ij)}$ to make it more amenable for learning.

* **Multi-Class $N$ pair loss** generalizes triplet loss. Samples are arranged into tuples $(x,x^+,x_1^-,\dots,x^-_{N-1})$ and we calculate
  $$
  \begin{split}
  \mathcal{L} \left(x,x^+, \set{x_i^-}_{i=1}^{N-1}\right) &= \log\left(1 + \sum_{i=1}^{N-1} \exp\left(f(x)^Tf(x_i^-) - f(x)^Tf(x^+)\right)\right) \\
  &= -\log \frac{\exp(f(x)^Tf(x^+))}{\exp(f(x)^Tf(x^+) + \sum_{i=1}^{N-1} \exp(f(x)^Tf(x_i^-)))}
  \end{split}
  $$

* **Noise Contrastive Estimation (NCE)** involves distinguishing signal from noise. We define $x^+_i\sim p_{\theta}$ and $x^-_i\sim q$ as positive and negative samples respectively. 
  Let $\sigma(\cdot)$ denote the sigmoid. Then 
  $$
  \begin{split}
  \mathcal{L} &= -\frac{1}{N}\sum_{i=1}^N \left[\log \sigma(l_\theta(x_i)) +\log(1-\sigma(l_\theta(x_i^-)) \right] \\
  l_\theta(x) &= \log p_\theta(x) - \log q(x)
  \end{split}
  $$ 
* **InfoNCE Loss** uses the categorical cross entropy loss for positive and negative samples. e
  
  Let $c$ be a context vector. Generate $x^+\sim p(x\mid c)$ and $\set{x^-_i}_{i=1}^{N-1}\sim q(x)$. Also let $X=\set{x^+} \cup \set{x_i^-}_{i=1}^{N-1} = \set{x_i}_{i=1}^N$. 
  
  Now, the probability of detecting the positive sample correctly is 
  $$
  \begin{split}
  p(C=+ \mid X,c) &= \frac{p(x^+\mid c) \prod_{i=1}^{N-1}p(x_i^{-})}{\sum_{j=1}^N\left[p(x_j\mid c) \prod_{i=1; i\ne j}^N p(x_i)\right]} \\
  &= \frac{\frac{p(x^+\mid c)}{p(x^+)}}{\sum_{x'\in X} \frac{p(x'\mid c)}{p(x')}} \\
  &= \frac{f(x^+, c)}{\sum_{x'\in X} f(x',c)}
  \end{split}
  $$
  Where $f(x,c)\propto \frac{p(x\mid c)}{p(x)}$. The approximator is used to maximize [[Information Theory|Mutual Information]] between $x$ and $c$. 
  
  The InfoNCE loss is then
  $$
  \mathcal{L}= -\mathbb{E}\left[\log\frac{f(x,c)}{\sum_{x'\in X} f(x'c)}\right]
  $$

* The **Soft-Nearest Neighbors Loss** extends InfoNCE to use multiple positive samples.
  
  Let $f(\cdot,\cdot)$ measure the similarity between inputs and $\tau$ be a temperature parameter. Then for a batch $\set{x_i,y_i}_{i=1}^B$ we have
  $$
  \mathcal{L} = \frac{1}{B}\sum_{i=1}^B\log\frac{\sum_{j=1 \ : \ i\ne j, y_i=y_j}^B \exp(-f(x_i,x_j)/\tau)}{\sum_{k=1 \ : \ i\ne k}^B \exp(-f(x_i,x_k)/\tau)}
  $$
  A high temperature means representations will tend to be more concentrated.


# Links
* [Contrastive Representation Learning by Lillian Weng](https://lilianweng.github.io/posts/2021-05-31-contrastive/)