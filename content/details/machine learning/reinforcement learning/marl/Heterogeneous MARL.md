* In the heterogeneous setting, we no longer assume that agents necessarily have the same observation space, action space, or reward functions.

* The core issues with Heterogeneous [[Multi-Agent Reinforcement Learning|MARL]] is that the usual [[MARL Algorithms and Approaches|approaches]] are typically for Homogeneous MARL which does not necessarily extend well to the Heterogeneous setting. 

* One approach is to allow for heterogeneity among agent policies. That is, $\pi_i$ and $\pi_j$ are different functions when $i\ne j\in N$. 
	* *Caveat*: For joint rewards, we have the problem of **Credit Assignment** -- that is, how to determine an agent's contribution to a state.
	* *Caveat*: The **Miscoordination Problem** Even with proper credit assignment, policy updates for agent $i$ may interfere with updates for agent $j$ resulting in a poor joint policy over all. 
* According to [^bettini_2023], there are two classes of heterogeneous systems (which are not necessarily mutually exclusive).
	* **Physical heterogeneity** comes from differences in the agents in terms of hardware (sensors and actuators) or physical constraint.  This implies different observation and action spaces.
		* *Physical heterogeneity can be addressed through homogeneous solutions but with added constraints on the agents.*
	* **Behavioral heterogeneity** comes from components having distinct policy outputs when observing the same input. 
		* **Same Objective Heterogeneity** means that the agents have the same objective function but optimized through heterogeneous behavior.
		* **Different Objective Heterogeneity** means that the agents have different objective functions that they optimize.

* *The inherent trade off between homogeneity and heterogeneity is that of sample efficiency (homogeneous) and resilience / performance (heterogeneous)*.

[^Bettini_2023]: Bettini, Shankar, and Prorok (2023) [Heterogeneous Multi-Robot Reinforcement Learning](https://arxiv.org/pdf/2301.07137)

# HARL
* [^Juang_2024] introduces **Comparative Advantage Maximization (CAM)** to enhance specialization within multi-agent systems.
	* The general idea is to first *Develop a general policy via CTDE*. and then *guide agents to leverage their comparative advantage*. 
	* On top of the usual [[Policy Gradient Methods|Policy Gradient]]-based approach, we modify the loss function to include the [[Mutual Information|Mutual Information]] written as  follows for two agents $i,j$. 
	  $$
	  J'(\theta) = J(\theta) + \lambda I(a_i; a_j \mid s)
	  $$
	* Agents are identified using IDs (denoted $d$). Implicitly, all localized inputs $Q, \pi, V$ depend on $d$. 
	* In the first stage, The base policy is trained on states and agent IDs with the goal of maximizing mutual information across agent pairs. Mutual information means *agent behaviors are interlinked and aligned while still allowing some room for diversity*. In particular, the goal is to maximize the following 
	  $$
	  \begin{split}
	  \sum_{s,a_i, a_j} \left[Q(s,a_i)\right]\left[\pi_\theta (a_i,a_j\mid s) \log(\pi_{\theta}(a_i,a_j\mid s)) \right] \\
	  - V(s) \left[\pi_{\theta} (a_i,a_j\mid s) \left[\log(\pi_\theta(a_i\mid s))  + \log(\pi_\theta(a_j\mid s))\right]\right]
	  \end{split}
	  $$
	* In the second stage, we use the baseline policy from the first stage. Each agent maximizes its comparative advantage, in such a way that *agents learn to specialize*. The goal is to maximize the $Q$-value of individual actions.
	  
	  To ensure evolution, policies are added to the opponent pool for refinement and competition.
	  
	  Our objective function is to maximize the following. We denote the base model as $f$. For each $i$, $s_i$ denotes the state of the world where $f(a_{-i})$ and agent $i$ does nothing.
	  $$
	  \begin{split}
	  \frac{1}{N}\sum_{i}\sum_{s_i ,a_{-i}}\pi_\phi(a_i\mid s_i) \cdot \left[Q(s_i, a) \log(\pi_\phi(a_i\mid s)) - V(s_i)\log(\pi_\phi(a_i\mid s_i))\right]
	  \end{split}
	  $$

[^Juang_2024]: Juang et al. (2024) [Breaking the mold: The challenge of large scale MARL specialization](https://arxiv.org/abs/2410.02128)

* [^Zhong_2023] proposes Heterogeneous MARL (HARL) algorithms for the cooperative setting designed to coordinate agent updates.  In particular, the key idea of their scheme is to *perform sequential updates on each individual agent's policy rather than update the whole joint policy*,
	* (*[^Zhong_2023] 4*) **Multi-Agent Advantage Decomposition**. In any cooperative Markov games given a joint policy $\pi$, for any state $s$ and agent subset $i_{1:m}$, the following holds for the [[MARL from a Game Theoretic Perspective#Miscellaneous|Multi-agent Advantage]]. 
	  
	  $$
	  A_\pi^{1:m} (s,a^{i_{1:m}}) = \sum_{j=1}^m A_\pi^{i_j}(s,a^{i_{1:j-1}}, a^{i_j})
	  $$
	  That is, *a joint policy can be improved sequentially*.
	* (*[^Zhong_2023] 6*) Let $\pi$ be a joint policy. For any joint policy $\overline\pi$ we have
	  $$
	  J(\overline\pi) \ge J(\pi) + \sum_{m=1}^n L_{\pi}^{i_{1:m}} (\overline\pi_{i_{1:m-1}}, \overline{\pi}_{i_m}) - \text{C} \ \cdot \max{\text{KL}}(\pi_{i_m}, \overline\pi_{i_m})
	  $$
	  Where
	  $$
	  C= \frac{4\gamma \max_{s,a} [A_\pi(s,a)]}{(1-\gamma)^2}
	  $$
	  We define $L$ as follows. Let $\pi$ be the joint policy, $\overline{\pi}_{i_{1:m-1}}$ be some other joint policy of agents $i_{1:m-1}$ and $\hat{\pi}_{i_m}$ be some other policy of $i_m$. Then
	  $$
	  L_\pi^{i_{1:m}} (\overline{\pi}_{i_{1:m-1}}, \hat{\pi}_{i_m}) = \mathbb{E}_{s\sim \rho_\pi, \ \ \ a_{i_{1:m-1}}\sim\overline{\pi}_{i_{1:m-1}} \ \ \ a_{i_m} \sim \hat{\pi}_{i_m}} [A_\pi^{i_m} (s,a_{i_{1:m-1}}, a_m)]
	  $$
	  The sequential update scheme is given below
	
	![[Sequential HARL.png]]
	<figcaption> Sequential HARL. Image taken from ZhonG et al. (2023) </figcaption>
	
	* In performing the sequential update, we take into account the previous agent updates.
	* (*[^Zhong_2023] 7*) The Multi-Agent Policy Iteration with Monotonic Improvement Guarantee monotonically improves. In fact, (*Zhong 8*) The policy converges to the Nash Equilibrium.
		* The algorithm is not practical however since it (1) assumes the use of the full state space and action space and (2) requires the computation of the [[Information Theory|KL Divergence]]. 
	
	
	* The Sequential HARL algorithm can be made more practical using [[Trust Region Policies|TRPO and PPO]] versions as shown below
	![[HATRPO.png]]
	<figcaption> HATRPO. Image taken from Zhong et al. (2023)  
	</figcaption>
	
	
	![[HAPPO.png]]
	<figcaption> HAPPO. Image taken from Zhong et al. (2023) </figcaption>
	
	
	
	
	[^Zhong_2023]: Zhong et al. (2023) [Heterogeneous-Agent Reinforcement Learning](https://arxiv.org/pdf/2304.09870)

# Parameter Sharing Methods
## UAS 
* [^Yu_2024]  introduces the use of a **Unified Action Space (UAS)** which consists of *semantic representations of agent actions from a latent space of all possible agent actions*, particularly in the case when agents are physically heterogeneous (i.e., different constraints or capabilities). 
* Action masks are used to generate the agent policies.
* (*Yu 1*)  There exists a fully-cooperative physically heterogeneous MARL problem such that *the joint reward with parameter sharing is suboptimal*.
  
  More formally if $J^\ast$ is the optimal joint reward, and $J^\ast_p$ is the optimal joint reward under parameter sharing. Also let $\rho_i$ denote the probability of action $a_i$. and there are $N$ agents, we have
  $$
  \frac{J^\ast}{J^\ast_p} =\frac{1}{\left(\frac{\rho_i}{N}\right)^{2N}}, \ \ \ \ \ \ 0 < \frac{\rho_r}{N} < 1
  $$
* Semantic representations come from dividing the action space based on semantics (i.e., what the actions do).
  
  For all $i\in N$, divide the local available action set $A_i$ $k$ sets with different action semantics.  The **Unified Action Space** is defined as 
  $$
  A^U = \bigcup_{k}A_k
  $$
  Clearly $A^U\supseteq A$. 
  
  To identify different action semantics, we use an **Action Mask operator**. That is, given an action mask $\text{AM}$ we extract the actions as
  $$
  A^U \odot \text{AM}
  $$
* *By performing action masking, we are able to use  global parameter sharing while maintaining action semantics*.  We operate on the Unified Action Space with parameter sharing and to extract action semantics, we perform action masking.
* In addition to UAS, we introduce the **Cross Group Inverse Loss** to facilitate learning and predicting the policy of other agents.
  
  It is calculated as follows. Let $AM_i^\text{inv}$ be the action mask for other physically heterogeneous agents. Then the CGI [[Loss Function|loss]] is the mean squared error between $\rho^\text{inv}=\rho^U \odot \text{AM}_i^\text{inv}$ and $\rho$. If each agent has an associated independent network branch parameterized by $\psi_i$, we have
  $$
  L_{\text{CGI}} (\rho_\psi^{\text{inv}} \mid h) = \mathbb{E}_\mathcal{D} [(\rho^\text{inv} - \rho)^2]
  $$
  Where $h$ is the hidden state of an associated [[Recurrent Neural Network|GRU]] which encodes the trajectory. The average is calculated over samples from the replay buffer $\mathcal{D}$
  
  Similarly for value-based algorithms
  $$
  L_\text{CGI}(Q_\psi^\text{inv} \mid h) = \mathbb{E}_\mathcal{D} [(Q^\text{inv} - Q)^2]
  $$
* The overall pipeline is shown below
![[UAS Pipeline.png]]
<figcaption> UAS pipeline. Image taken from Yu et al. (2024) </figcaption>

* A version of [[Trust Region Policies|MAPPO]] using Unified Action Spaces is shown below. The relevant equations for calculations are as follows
  
  $$
  \begin{split}
  L(\pi_\theta) &= \mathbb{E}_\mathcal{D} \left[\min\left(\frac{\pi_\theta(a\mid \tau)}{\pi_{\theta_\text{old}} (a \mid \theta)} A_{\pi_\theta}(s,a), \text{clip}\left(\frac{\pi_\theta(a\mid \tau)}{\pi_{\theta_\text{old}}(a \mid \theta)}, 1\pm \epsilon_p \right)A_{\pi_\theta}(s,a)\right)\right] + \lambda_E\mathbb{E}_\mathcal{D}\bigg[S(\pi_\theta(\tau))\bigg] \\
  
  L(V_\phi) &= \mathbb{E}_\mathcal{D} \left[\max\left((V_\phi(s)-\hat{R})^2 ,((\text{clip}(V_\phi(s), V_{\phi_\text{old}} (s) \pm \epsilon_v))-\hat{R})^2\right)\right] \\ 
  
  L(p_\psi^\text{inv}) &= \mathbb{E}_\mathcal{D} [(\rho^\text{inv} - \rho)^2] \\
  
  L_{U-\text{MAPPO}} &= L(\pi_\theta) + \lambda_V L(V_\phi) + \lambda_I L(\rho^\text{inv}_\psi)
  \end{split}
  $$
  Each $\lambda$ is a hyperparameter that acts as weighting coefficients

![[U-MAPPO.png|400]]
<figcaption> U-MAPPO. Image Taken from Yu et al. (2024)</figcaption>

* We can also extend [[Value Reward Decomposition|QMIX]] similarly. The relevant equations are as follows
  
  $$
  \begin{split}
  L(Q_\theta) &= \mathbb{E}_\mathcal{D} \left[
  (y^\theta - Q_\text{tot}(\tau, s; \theta)^2)
  \right] \\ 
  y^\theta & = r + \gamma \max_{a'} Q_{\text{tot}}^\text{tgt} (\tau',s'; \theta^{\text{tgt}}) \\
  L(Q_\psi^\text{inv}) &= \mathbb{E}_\mathcal{D} \left[(Q^\text{inv} - Q)^2\right]\\
  L_{U-QMIX} &= L(Q_\theta) + \lambda_I L(Q_\psi^\text{inv})
  \end{split}
  $$

![[U-QMIX.png|400]]
<figcaption> U-QMIX. Image taken from Yu et al. (2024) </figcaption>

[^Yu_2024]: Yu et al. (2024) [Improving Global Parameter-sharing in Physically Heterogeneous Multi-agent Reinforcement Learning with Unified Action Space](https://arxiv.org/pdf/2408.07395) 

## SHPPO
* [^guo_2024] proposes  a parameter-sharing based approach but with heterogeneous layers for each agent's policy network, which are given by a latent distribution learned via an encoder network. 
* The strategy pattern of each agent is represented by a latent variable $l$ obtained using the encoder network as follows
  $$
  \begin{split}
  \mu_i , \sigma_i &= \text{ENCODER} (o_i, h_i^{t-1}) \\
  l_i &\sim  \mathcal{N(\mu_i, \sigma_i)}
  \end{split}
  $$
* To learn the parameters for the encoder, we also include an InferenceNet as a critic that learns to minimize the difference between the value function and the reward. It outputs the value $V_I$
	* More formally, let $\mu, \sigma$ be the concatenation of all $\mu_i$ and $\sigma_i$;  $\theta_L$ denotes the parameters of the InferenceNet; $\lambda_e,\lambda_d$ are regularization constants; $\mathcal{H}$ is the [[Information Theory|entropy]] function of the distribution; $\mathcal{D}_i$ is the latent distribution (in this case, a Gaussian parameterized on $\mu_i, \sigma_i$); $\text{Norm}$ pertains to normalization. 
	  $$
	  \begin{split}
	  \mathcal{L}_L (\theta_L) &= -\mathcal{L}_v(\theta_L) + \lambda_e \mathcal{L}_e(\theta_L) -\lambda_d \mathcal{L}_d(\theta_L) \\
	  \mathcal{L}_v(\theta_L) &= V_I(o_g, \mu (o, h^{t-1}\mid \theta_L), \sigma(o, h^{t-1} \mid \theta_L)) \\
	  \mathcal{L}_e(\theta_L) &= \frac{1}{n} \sum_{i}  \mathcal{H}(\mathcal{D_i}(o_i, h_i^{t-1} \mid \theta_L)) \\
	  \mathcal{L}_d(\theta_L) &= \frac{1}{n(n-1)} \sum_i \sum_{j\ne i} \text{Norm}(1-\text{cos\_sim}(l_i(o_i, h_i^{t-1}\mid \theta_L),l_j(o_i, h_i^{t-1} \mid \theta_L))
	  \end{split}
	  $$
		* Minimizing $\mathcal{L}_v$ means learned latent variables help choose better heterogeneous layers (since we maximize value)
		* Maximizing $\mathcal{L}_e$ means latent distributions are more identifiable.
		* Minimizing $\mathcal{L}_d$ means latent distributions are more diverse .


* Each $l_i$ is then used to generate a heterogeneous layer. That is, we get the heterogeneous parameters $w_i$ from $l_i$.

* *Limitation*: The heterogeneous layers chosen are simple.  It is also reliant on the population distribution.
![[SHPPO.png]]
<figcaption> SHPPO. Image taken from Guo et al., 2024</figcaption>

[^guo_2024]: Guo et al., 2024 [Heterogeneous Multi-Agent Reinforcement Learning for Zero-Shot Scalable Collaboration](https://arxiv.org/abs/2404.03869)



