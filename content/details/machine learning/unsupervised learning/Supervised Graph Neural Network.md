
 * We can use a simple dense [[Neural Network|layer]] to extract outputs from $H^T$. This gives us 
   $$
   \hat{y}_v = \text{softmax}(WH^T_v)
   $$
   Where $\hat{y}\in\mathbb{R}^{|V|}$, and $W\in\mathbb{R}^{|L|\times F}$ for $|L|$ labels.
   
   This can then be optimized using a [[Loss Function]] on each $\hat{y}_v$ assuming ground truth $y_v$
   $$
   L = \frac{1}{n_l}\sum_{i=1}^{n_l} \text{loss}(\hat{y}_i , y_i)
   $$
   Where $n_i\le |V|$ is the number of labelled vertices. 
   
   The loss function is then optimized with [[Neural Network#Backpropagation|backpropagation]]. 

## Graph Convolutional Network 
* A **Graph Convolutional Network (GCN)**  is a GNN architecture that makes use of [[Convolutional Neural Network|convolutions]]. In particular, the update rule is defined as 
  $$
  H^{t+1} = \sigma(\overline{D}^{-\frac{1}{2}} \overline{A}^{-\frac12} H^t W^t)
  $$
  Where $\overline{A}$ is the adjacency matrix with an additional self-loop of weight $1$ added so that a node's old representation is also considered.
  $$
  \overline{A}= A(G) + I
  $$
  And $\overline{D}$ is a diagonal matrix defined similar to the degree matrix.
  $$
  \overline{D}_{ii}= \sum_j\overline{A}_{ij}
  $$
  And $\sigma$ is an activation function

* We can decompose the update rule into Aggregation and Combination as in the General Framework.
	* The decomposition is stated as follows: 
	  $$
	  H_i^t = \sigma\left(\sum_{j\in N(v)\cup v} \frac{\overline{A}_{ij}}{\sqrt{\overline{D}_{ii} \overline{D}_{jj}}} H_j^{t-1} W^t\right) = \sigma\left(\sum_{j\in N(v)} \frac{\overline{A}_{ij}}{\sqrt{\overline{D}_{ii} \overline{D}_{jj}}} H_j^{t-1} + \frac{1}{\overline{D}_{ii}}H_i^{t-1} W^t\right) 
	  $$
	* Aggregation is done as the weighted average of neighbor node representations.
	* The weighting factor $\frac{\overline{A}_{ij}}{\sqrt{\overline{D}_{ii}\overline{D}_{jj}}}$ is the weight of the edge between $i$ and $j$ normalized by their respective degrees.
	* Combination is defined as the summation of aggregated messages and the node representation itself. 

* The "Convolution" comes from [[Spectral Convolution|Spectral Convolutions]].

## Graph Attention Network
* Takes inspiration from [[Transformer Model|The Attention Mechanism]]. The **Graph Attention Network (GAT)** makes use of the following layers.
* The graph attention layer defines how new node representations attend to old node representations. 
  
  We use the shared attention mechanism $a:\mathbb{R}^{F'}\times \mathbb{R}^{F'} \to \mathbb{R}$ to derive
  $$
  e_{ij} = a(WH_i^{t-1}, WH_j^{t-1})
  $$
  To get the attention coefficients, we simply apply softmax
  $$
  a_{ij} = \text{softmax}_j (\set{e_{ij}}) = \frac{\exp (e_{ij})}{\sum_{k\in N(i)} \exp (e_{ik})}
  $$
* An alternative to the above definition is to use a Leaky ReLU as the activation function so that 
  $$
  e_{ij} = \text{LeakyReLU} (W_2 [WH_i^{t-1} \mid\mid WH_j^{t-1}])
  $$
  Where $(\cdot \mid\mid \cdot)$ denotes concatenation of two tensors.

* The new representation is then obtained using 
  $$
  H_i^t = \sigma\left(\sum_{j\in N(i)} a_{ij} WH_j^{t-1}\right)
  $$
## Neural Message Passing Networks
* The underlying idea behind **Neural Message Passing Networks (NMPN)** is to simulate message passing between nodes. We define two functions:
	* **Message** $M_t(\cdot,\cdot,\cdot)$ which encodes the message between node $i$ and $j$ in the $t$-th layer based on information in edge $e_{ij}$. 
	* **Update** $U_t$ combines the aggregated messages from the neighbors and the node representation. This functions as *Combine* in a similar manner to the general framework 

* More formally, the message at the $t$-th layer for node $i$ is
  $$
  m_i^t = \sum_{j\in N(i)} M_k(H_i^{t-1}, H_j^{t-1}, e_{ij})
  $$
  The update is done as follows
  $$
  H_i^t = U_t (H_i^{t-1}, m_i^t) 
  $$

## Continuous Graph Neural Networks 
* Inspired by [[Diffusion Network|Diffusion models]] and [[Network Epidemiology|Network epidemics]]. 
* Define $A$ as the regularized characteristic matrix with hyperparameter $\alpha\in [0,1]$ and degree matrix $D$
  $$
  A = \frac\alpha 2 (I + D^{-\frac{1}{2}} AD^{-\frac{1}{2}})
  $$
* The [[Matrix Diagonalization|eigenvalues]] of $A$ lie in the interval $[0,\alpha]$ which means that $A^k$ [[Matrix Limit|converges]]
	* $\alpha$ controls the diffusion rate. 
* If we *Assume* independent feature channels, we have the following propagation equation
  $$
  H^{t+1} = AH^t + H^0
  $$
  Where $H^0 = X$. 
  
  We can unroll this to be equal to 
  $$
  H^t = \left(\sum_{i=0}^t A ^i\right) H^0 = (A-I)^{-1}(A^{t+1} -I)H^0 
  $$
  The precise dynamics are then encapsulated using the following [[Differential Equation|differential equation]]
  $$
  \frac{dH^t}{dt} = \log{AH^t} + X \approx(A-I)H^t + X
  $$

	* In words: *The representation of a node is dependent on the influence of neighbors ($AH^t$), how much the node resists external influence ($IH^t$) and the inherent characteristics of the node ($X$)*

* If we relax the assumption such that we allow feature channels to interact with each other we have the following model. Let $W\in \mathbb{R}^{F\times F}$ be the weight matrix that models interactions between feature channels. We have
  
  $$
  H^{t+1} = AH^t W + =H^0
  $$
  The dynamics are given by the following differential equation 
  $$
  \frac{dH^t}{dt} = (A-I)H^t + H^t (W-I) + X
  $$
  Where, as before, $H^0 = X$. 

## Lanczos Network
* *Motivation*: The main issue with [[#Graph Convolutional Network|GCN]] is that it only propagates information over one step. That is, from a node to its nearest neighbor. 
	* *Naively stacking does not work*. First, it may make the network too deep which means [[Pathologies of Deep Learning#Gradients and Learning Rate|Vanishing Gradients]]. 
	* *Exponentiating the Laplacian is too costly*. It is also unclear how to add learnable parameters to the Laplacian.
* The **Lanczos Network** makes use of the Lanczos algorithm to obtain a matrix $V$ and compute a low rank approximation of the [[Graph Laplacian|Laplacian]]
  $$
  L\approx VRV^T
  $$
  The column vectors of $V$ are denoted $v_1,\dots, v_M$. Implicitly, because it is low rank, the size of the approximation is significantly less than the Laplacian.
* The update rule is then defined as follows. Let $f_\theta$ be a learnable spectral filter parameterized by $\theta$. Also, let $\set{l_1,\dots, l_U}$ 
  
  We have
  $$
  \hat{L} = \sum_{m=1}^M  f_\theta(r_m^{l_1}, \dots ,r_m^{l_u}) v_m v_m^T
  $$
  And
  $$
  H^{(t + 1)} = \hat{L} H^{(t)} W
  $$
  Where $H^{(t)}$ means the representation at the $t$-th layer. 


 * The main limitation of this approach is that it uses a [[Low Rank Approximation|low rank approximation]]
# Links
* [[Graph Neural Networks -- Foundations, Frontiers and Applications by Wu et al.]]