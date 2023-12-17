# Soft Q Learning 
* *Aims to learn maximum entropy policies* [^Haarnoja_2017]. It expresses the optimal policy via a [[Probability Distributions Zoo|Boltzmann distribution]] (using the property that Boltzmann distributions maximize [[Information Theory|entropy]]). 
* Instead of learning the best way to perform the task, *the resulting policies try to learn all of the ways of performing the task*
* We reframe the task as finding the optimal policy $\pi^\ast$ such that 
  
  $$
  \pi^\ast = \underset{\pi}{\text{argmax}} \sum_{t} \mathbb{E}_{(s_t,a_t)\sim\pi} \left[ r(s_t,a_t) + \alpha \ H(\pi(\cdot \mid s_t))\right]
  $$
  Where $\alpha$ is the **temperature parameter** for balancing reward and entropy.

* Policies are represented as
  
  $$
  \pi(a_t\mid s_t) \propto \exp(-\mathcal{E} (s_t, a_t))
  $$
  Where $\mathcal{E}$ is an energy function.

* *(Haarnoja Thm. 1)* Let the **soft $Q$ function** and **soft $V$ function** be defined as
  
  $$
  \begin{split}
  Q_{\text{soft}}^\ast(s_t,a_t)  &= r_1 + \mathbb{E}_\pi \left[\sum_{k=1}^\infty \gamma ^k (r_{k+t} +\alpha \ H(\pi^\ast (\cdot \mid s_{t+k}) \ ))\right] \\
  V_{\text{soft}}^\ast(s_t ) &= \alpha \log \int_{\mathcal{A}} \exp\left(\frac{1}{\alpha} Q_\text{soft}^\ast (s_t,a')\right) \ da'
  \end{split}
  $$
  
  The optimal policy for maximum entropy RL is given as 
  
  $$
  \pi^\ast _\text{MaxEnt}(a_t\mid s_t) = \exp\left(\frac{1}{\alpha}Q ^\ast _\text{soft} (s_t,a_t) -V^\ast _\text{soft}(s_t)\right) 
  $$

* **Soft [[Backups in Reinforcement Learning|Bellman equation]]** (*Haarnoja  Thm. 2*) 
  
  $$
  
  \mathcal{T}^\pi Q(s_t,a_t)  = Q^\ast_\text{soft} (s_t,a_t) = r(s_t,a_t)+\gamma \mathbb{E}_{s_{t+1}\sim \pi} [V^\ast _\text{soft} (s_{t+1})]
  $$

* **Soft Q-iteration** (*Haarnoja  Thm. 3*)  The following is a soft version of Bellman Backup 
   
  Assume that $Q_\text{soft}$ and $V_\text{soft}$ are bounded 
  $\log \int_{\mathcal{A}} \exp\left(\frac{1}{\alpha} Q_\text{soft}^\ast (\cdot,a')\right) \ da' < \infty$, and
  $Q_\text{soft}^\ast <\infty$ exists 
  
  Then we can perform the following fixed point iteration to converge to $Q^\ast_\text{soft}$ and $V_\text{soft}^\ast$ 
  
  $$
  \begin{split}
  Q_\text{soft}(s,a) &\gets r(s_t,a_t) +\gamma \mathbb{E}_{s_{t+1}\sim \pi} \left[V_\text{soft} (s_{t+1} )\right] &, \forall s_t, a_t \\
  
  V_\text{soft} (s_t) &\gets \alpha \log \int _\mathcal A \exp \left(\frac{1}{\alpha} Q_\text{soft} (s_t,a')\right) \ da' &, \forall s_t
  \end{split} 
  $$ 
* A stochastic version involves optimizing via [[Importance Sampling]] using $q_a$ as an arbitrary distribution over action space. We compute $V_\text{soft}^\theta$ and a general loss function $J_Q(\theta)$ as follows 
  
  $$
  \begin{split}
  V_\text{soft}^\theta (s_t) &= \alpha \log \mathbb{E}_\pi \left[\frac{\exp(\frac{1}{\alpha} \ Q_\text{soft}^\theta(s_t, a'))}{q_{a'}(a')}\right] \\
  
  J_Q(\theta) &= \mathbb{E}_\pi \left[ \frac{1}{2} \left(\hat{Q}_\text{soft} ^\theta (s_t,a_t) -Q_\text{soft}^\theta (s_t,a_t\right)^2 \right] \\ 
  
  \hat{Q}^\theta_\text{soft} (s_t,a_t) &= r(s_t,a_t) + \gamma \mathbb{E}_\pi \left[V_\text{soft}^\theta (s_{t+1} )\right]
  \end{split}
  $$
  
  The stochastic version is computed using Approximate Sampling and Stein Variational Gradient Descent 

![[Soft Q Learning.png|300]]
<figcaption> Soft Q Learning. Taken from Haarnoja  et al. (2017)</figcaption>

[^Haarnoja_2017]:  Haarnoja, Tang, Abbeel, and Levine (2017). [Reinforcement Learning with Deep Energy-based Policies](https://arxiv.org/pdf/1702.08165.pdf)
# SAC
* **Soft Actor Critic** [^Haarnoja _2018]  Extends [[#Soft Q Learning]] by having an actor also maximize both expected reward and entropy. *To succeed in performing a task while performing as randomly as possible*. This approach is very stable and can achieve SOTA performance on continuous tasks. 
	* Previous methods such as [[Trust Region Policies]] require new samples to be collected for each gradient step, which becomes expensive as tasks become more complex. 
	* Using [[Deterministic Policy Gradient#DDPG|DDPG]], while sample efficient, is challenging to use due to extreme brittleness and hyperparameter sensitivity. 
	* Soft Q Learning requires complex approximate inference procedures in continuous action spaces. 

* SAC relies on three components 
	* An *actor-critic architecture* with separate policy and value function networks. The actor itself is stochastic. 
	* An *off policy formulation* that enables reuse of previously collected data for efficiency 
	* *Entropy maximization* to enable stability and exploration.

*  **Soft Policy Evaluation** (*Haarnoja Lem. 1*) - Let $Q^0:\mathcal{S}\times \mathcal{A} \to \mathbb{R}$ where $|\mathcal{A}|<\infty$. Let $Q^{k+1}=\mathcal{T}^\pi$. The sequence $Q^k$ converges to the soft $Q$ value of $\pi$ as $k\to \infty$. In other words, we can compute the soft $Q$ value using repeated applications of the soft Bellman operator.  
* We restrict the choice of policy $\pi$ to be in some set of policies $\Pi$. TO that end, we use the Kullback-Liebler divergence. Thus, for each improvement step, we update according to 
  
  $$
  \pi_\text{new} = \underset{\pi'\in \Pi}{\text{argmin}} \ \text{KL}\left(\pi(\cdot \mid s_t) \ \bigg{|}\bigg{|} \   \frac{\exp (Q^{\pi_\text{old}} (s_t,\cdot))}{Z^{\pi_\text{old}}(s_t)} \right)
  $$
  Where $Z$ is a partition function that normalizes the distribution, but can largely be ignored. 

* **Soft Policy Improvement** (*Haarnoja  Lem. 2*) Let $\pi_\text{old}\in \Pi$ and $\pi_\text{new}$ be as defined above. Then $\forall s_t \in \mathcal{S}, a_t \in \mathcal{A}$ and where $|\mathcal{A}| <\infty$ we have that 
  $$ 
  Q^{\pi_\text{new}}(s_t,a_t) \ge Q^{\pi_\text{old}}(s_t,a_t)
  $$

 * **Soft Policy Iteration** (*Haarnaja Thm. 1*) repeated application of soft policy evaluation and soft policy improvement from any $\pi \in \Pi$ converges to a policy $\pi^{\ast}$, assuming $|\mathcal{A}|<\infty$. $\pi^\ast$ is the optimal policy among all $\Pi$. 
	 * In other words, we can generalize [[Dynamic Programming for Reinforcement Learning#Generalized Policy Iteration|GPI]] for soft RL. 


* **Soft Actor-Critic** approximates Soft Policy Iteration by using [[Function Approximation in Reinforcement Learning|Function Approximation]] using 
	* A parameterized state value function $V_\psi(s_t)$ to approximate the soft value. *This helps stabilize training, even if strictly speaking there is no need for this.*
	  
	  Its goal is to minimize the squared residual error using the distribution of previously sampled states and actions $\mathcal{D}$.
	  
	  $$
	  \begin{split}
	  J_V(\psi) &= \mathbb{E}_{s_t\sim \mathcal{D}}\left[\frac{1}{2} \left(V_\psi (s_t) - \mathbb{E}_{a_t\sim \pi_\phi} [Q_\theta (s_t,a_t)-\log \ \pi _\phi(a_t\mid s_t)]\right)^2 \right]  \\
	  
	  \nabla_\psi J_V(\psi) &= (V_\psi(s_t) - Q_\theta (s_t,a_t) + \log\pi_\phi (a_t\mid s_t)) \ \nabla_\psi V_\psi(s_t)
	  \end{split}
	  $$
	  
	* A soft $Q$-function $Q_\theta(s_t,a_t)$ which is trained to minimize the soft Bellman residual 
	  
	  $$
	  \begin{split}
	  J_Q(\theta) &= \mathbb{E}_{(s_t,a_t)\sim\mathcal{D}} \left[\frac{1}{2} \left(Q_\theta(s_t,a_t) - \hat{Q}(s_t,a_t\right)^2 \right] \\
	  
	  \hat{Q}(s_t,a_t) &= r(s_t,a_t) + \gamma \ \mathbb{E}_{s_{t+1}\sim \pi}\left[V_\bar{\psi} \ (s_{t+1})\right] \\ 
	  
	  \nabla_\phi J_Q (\theta) &= (Q_\theta(s_t,a_t) - r(s_t,a_t) -\gamma V_{\bar\psi}(s_{t+1})) \ \nabla_\theta Q_\theta (s_t,a_t)
	  \end{split}
	  $$
	  
	  Where $V_{\bar{\psi}}$ is a target value network. We optimize the above with stochastic gradients
	  
	* A Tractable policy $\pi_{\phi}(a_t\mid s_t)$   This is learned by minimizing the expected KL divergence given by 
	  
	  $$
	  J_\pi(\phi) = \mathbb{E}_{s_t\sim \mathcal{D}} \left[\text{KL}\left(\pi(\cdot \mid s_t) \ \bigg{|}\bigg{|} \  \frac{\exp (Q^{\pi_\text{old}} (s_t,\cdot))}{Z^{\pi_\text{old}}(s_t)}\right)\right]
	  $$
	  
	  *Optimizing requires reparameterizing the policy using a neural network transformation since the target is a differentiable neural network*
	  $$
	  a_t = f_\phi (\epsilon_t, s_t)
	  $$
	  
	  $\epsilon_t$ is an input noise vector. With this, the objective can be written as follows.
	  
	  $$
	  \begin{split}
	  J_\pi(\phi) &= \mathbb{E}_{s_t\sim \mathcal{D} \ ,\  \epsilon_t\sim \mathcal{N}}\left[ \log\pi_\phi (f_\phi (\epsilon_t \ , \ s_t)\  \mid \ s_t)  - Q_\theta (s_t, f_\phi (\epsilon_t \ ,\  s_t)) \right] \\ 
	  
	  \nabla_{\phi} J_\pi (\phi) &= \nabla_\phi \log \pi_\phi(a_t\mid s_t) + \nabla_\phi f_\phi(\epsilon_t \ , \ s_t)\big(\nabla_{a_t} \log \pi_\phi (a_t\mid s_t) - \nabla_{a_t} Q(s_t,a_t)\big)
	  \end{split}
	  $$
	  $a_t$ is evaluated at $f_\phi (\epsilon_t \ , \ s_t)$ 

* We use two Q-functions in a similar manner to double Q.  This speeds up training. 
 
![[SAC.png]]
<figcaption> Soft Actor Critic. Image taken from Haarnoja et al. (2018) </figcaption>

[^Haarnoja _2018] Haarnoja, Zhou, Abbeel, and Levine (2018). [Soft Actor Critic--Off Policy Maximum Entropy Deep Learning with a Stochastic Actor](https://arxiv.org/pdf/1801.01290.pdf)
# Links 
* [[Policy Gradient Method Algorithms]]