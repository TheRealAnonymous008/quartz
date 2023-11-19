# TRPO
* **Trust Region Policy Optimization** [^Schulman_2015]. It aims to optimize large non-linear policies (i.e., those that use neural networks) by using a surrogate loss function. In particular, this is based on the [[Information Theory|KL divergence]]
* For convenience, we let
  
  $$
  \text{KL}(\pi_{\theta_\text{old}}, \pi) = \text{KL}\left(\pi_{\theta_\text{old}}(\cdot\mid s_t) \mid\mid \pi_{\theta}(\cdot\mid s_t)\right)
  $$


* [[Policy Gradient Methods#Advantage function|The notes here are helpful as a background for why we have TRPO]].  The theoretical bound is then given for old policy $\pi_0$ and new policy $\pi_1$ as 
  
  $$
  \begin{split}
  \eta(\pi_1) &\ge J_{\pi_0}(\pi_1) - C \max_s \text{KL} (\pi(\cdot \mid s) \mid\mid \bar\pi(\cdot \mid s))\\
  
  C &= \frac{4\epsilon\gamma}{(1-\gamma)^2} \\ 
  \epsilon &= \max_{s,a} |\hat{A}_\pi(s,a) |
  \end{split}
  $$
* This gives the following algorithm for policy improvement. 
![[TRPO.png]]
<figcaption> Theoretical TRPO from Schulman et al. (2015). TRPO itself is an approximation of this </figcaption>

* TRPO reframes the objective as maximizing $\eta(\pi_1)$ (see above). However, we use the approximation $L_{\theta_\text{old}}$. More specifically, we can use the [[Importance Sampling]] ratio $\rho_{\theta_\text{old}}$and replace the advantage with $Q$.  That is, the objective becomes 
  
  $$
  \begin{split}
  J_{\theta_{\text{old}}} &= \mathbb{E}_{\ s\sim \rho_{\theta_\text{old}}, \  a\sim \pi_{\theta_\text{old}} } \left[\frac{\pi_\theta(a\mid s)}{\pi_{\theta_\text{old}}(a\mid s)} Q _{\theta_\text{old}} (s,a) \right]    \\
  \end{split}
  $$
  
* In practice, we do not use $C$ because this gives small step sizes. Instead we maximize $L_{\theta_\text{old}}(\theta)$ subject to the constraint that for threshold $\delta$. 
  $$
  \begin{split}
  \overline{\text{KL}}(\theta_1, \theta_2) &=  \mathbb{E}_{s\sim p}\left[\text{KL} (\pi_{\theta_1}(\cdot \mid s) \mid\mid \pi_{\theta_2} (\cdot \mid s))  \ \right]\\
  \overline{\text{KL}} (\theta_\text{old}, \theta) &\le \delta
  \end{split}
  $$
  This is the **trust region constraint** 
* The trust region constraint guarantees that old and new policies do not diverge too much while guaranteeing monotonic improvement.  [^TRPO_2]
* The $Q$ value can be replaced with an empirical estimate. 
	* **Single Path** - Estimates for $Q$ comes from a single trajectory
	* **Vine** -Given a single trajectory, sample states, and from each sampled state, sample actions. From there, perform a [[Decision Time Planning|rollout]] and estimate $Q$ from the rollout trajectories. 
	* *Vine gives a better estimate with lower variance* at the cost of requiring more calls as well as not being feasible for systems where "undoing" is not possible .

[^Schulman_2015]: Schulman et al. (2015) [Trust Region Policy Optimization](https://arxiv.org/pdf/1502.05477.pdf)
[^TRPO_1]: Note the original paper uses $D_{\text{TV}}$ and $D_\text{KL}$ in place of their respective divergences
[^TRPO_2]: The KL divergence makes this intuitive since it measures the similarity between two probability distributions, and recall that policies are probability distributions.

# PPO
* **Proximal Policy Optimization** [^Schulman_2017]. These alternate between sampling data through interaction with the environment, and optimizing a “surrogate” objective function using SGD.
* The goal is scalability since [[#TRPO]] is complicated and not good for noisy architectures. 

### PPO-CLIP
* It introduces the **clipped surrogate objective**. Let $r_t(\theta)$ denote the probability ratio 
  
  $$
  r_t(\theta) = \frac{\pi_\theta(a_t\mid s_t)}{\pi_{\theta_\text{old}} (a_t\mid s_t )}
  $$
  
  The surrogate objective becomes 
  
  $$
  J^{\text{CLIP}} (\theta) =  \hat{\mathbb{E}}_t \left[\min \left(r_t(\theta) \ \hat{A}_t\  , \ \text{clip}( r_t(\theta), 1-\epsilon, 1+\epsilon) \right)\hat{A}_t\right]
  $$
  
  The first term in the min function above is the same objective as [[#TRPO]]. The second modifies the surrogate objective by clipping the probability ratio, removing the incentive for moving $r_t$ outside the interval $[1-\epsilon, 1+\epsilon]$. 
  
  *The final bound given by the loss function above is a lower bound (i.e., a pessimistic bound) on the unclipped objective.* 
  
  Thus, we ignore $r_t$ when it makes the objective better and include it when it makes the objective worse. 

### PPO-KL 
* An alternative is **KL Penalization**  -- *we use a penalty on the KL divergence* and adapt the penalty based on a targeted KL divergence.  This can be done by alternating between the following
	* Use Minibatch SGD to optimize 
	  
	  $$
	  J^{\text{KLPEN}} = \hat{\mathbb{E}}_t\left[r(t) \ \hat{A}_t - \beta \text{KL}(\pi_{\theta_\text{old}},\pi_\theta )\right]
	  $$

	* Compute $d=\hat{E}_t[ \text{KL}(\pi_{\theta_\text{old}},\pi_\theta )]$
		* If $d < d_{\text{targ}}/1.5$, then $\beta\gets \beta/2$
		* If $d > d_{\text{targ}} * 1.5$, then $\beta\gets \beta*2$. 

	* We use the updated $\beta$ for the next policy update. The constants are magic but the algorithm is not sensitive to them.
	* Note that we can alternatively use the backward version which involves $\text{KL}(\pi_{\theta_\text{old}}, \pi_\theta)$. This yields no difference. 
	* Techniques presented [[Basic Methods#A3C - Asynchronous Advantage Actor-Critic|here]] may be combined with the loss function above. For example , introducing entropy loss $H(s,\pi_\theta)$. as a penalty term, or using [[Off Policy Prediction and Control with Approximation#DQN|Experience replay]].  
	* Using entropy loss gives us this loss function 
	  
	  $$
	  J^{\text{CLIP+VF+S}} = \hat{\mathbb{E}}_t\left[J_t^\text{CLIP}(\theta) - 
	  c_1 (V_\theta(s) - V_\text{target})^2 + 
	  c_2 H(\pi_\theta(s))	  
	  \right]
	  $$
	  

![[PPO.png]]
<figcaption> PPO Image from Schulman et al. (2017) </figcaption>

### Failure Modes 
* [^Hsu_2020] revisited PPO to examine two common design choices. 
	* The clipped probability ratio 
	* Parameterizing the policy action space by a continuous [[Probability Distributions Zoo|Gaussian]] or a discrete softmax.

* The following happens in standard PPO 
	1. *When we have reward signals with bounded support* This is problematic when the reward causes the policy to end up in regions with low rewards which would allow it to recover. 
		* This is common when we have unknown action boundaries or sparse rewards. 
	2. *High dimensional discrete action spaces*.  This causes PPO to get stuck at suboptimal actions.
	3. *Locally optimal actions close to initialization*. PPO is sensitive to initialization and will converge to locally optimal actions close to initialization.

* The following are the proposed solutions
	* Use KL regularization instead of the usual clipped loss.  That is, we perform. This solves failure modes 1 and 2.
		* KL *forces large steps to have a large opposite gradient* from the KL penalty so that we do not immediately leave the trust region. 
	* Instead of a Gaussian, use a Beta distribution as a parameterization for continuous action spaces. This solves failure modes 1 and 3
		* Compared to Gaussian policies where actions in the tails are given more importance, Beta policies give tails  lower importance. *All actions are weighted evenly*
		* Additionally it is easier to integrate a uniform prior on a Beta distribution by setting $\alpha=\beta=1$.
		* It eliminates the bias towards the boundaries in truncated Gaussian on bounded action spaces. 

[^Schulman_2017]: Schulman et al. (2017) [Proximal Policy Optimization Algorithms](https://arxiv.org/pdf/1707.06347.pdf)
[^Hsu_2020]: Hsu, Mendler-Dummer, and Hardt (2020) [Revisiting Design Choices in Proximal Policy Optimization](https://arxiv.org/pdf/2009.10897.pdf)

# PPG
* **Phasic Policy Gradient** [^Cobbe_2020] extends PPO to have two separate training phases for policy and value functions. This leads to significant improvements on sample efficiency .
* It provides an alternative to sharing network parameters which have the disadvantages of: 
	* Being hard to balance so that competing objectives do not interfere with each other. *This interference can impact performance*. 
	* Enforcing a hard restriction that policy and value function objectives are trained on the same data subject to the same sample reuse. *Value functions tend to tolerate a higher level of sample reuse*

* In PPG, we have disjoint policy and value networks. 
	* The policy network has policy $\pi_\theta$ and auxiliary value head $V_{w}$ .
	* The value network has a value head of $V_{\theta}(s)$ 
* PPG introduces two training phases. Learning proceeds by alternating between them. 

	* **Policy Phase** - train the agent with PPO using $J^{\text{CLIP}}$ for the policy, and $J^{\text{value}}$ for the value function of the policy network 
	  
	  $$
	  J^\text{aux}= \frac{1}{2} \cdot \hat{\mathbb{E}}\left[(V_{\theta} -\hat{V}_t ^\text{targ} )^2\right] 
	  $$
	  
	* **Auxiliary Phase** - distill features from the value function into the policy network for training future policy phases. We use the following loss function 
	  
	  $$
	  \begin{split}
	  J^{\text{joint}} = J^{\text{aux}} + \beta_\text{clone} \cdot \hat{\mathbb{E}}_t \left[\text{KL}(\pi_{\theta_\text{old}}\ , \ \pi_\theta)\right] 
	  \end{split} 
	  $$
	  
	  Where $\pi_{\theta_\text{old}}$ is the policy before the auxiliary begins.
	  $\beta_\text{clone}$ is a hyperparameter controlling the tradeoff between the auxiliary objective and the original policy
	  $J^\text{aux}$ is the auxiliary objective, which can be anything. The paper gives the following 
	  
	  $$
	  J^\text{aux}= \frac{1}{2} \cdot \hat{\mathbb{E}}\left[(V_{w} -\hat{V}_t ^\text{targ} )^2\right] 
	  $$

![[PPG.png]]
<figcaption> PPG. Image taken from Cobbe et al. (2020) </figcaption>

* In the figure
  $N_\pi$ controls the number of policy updates performed in each policy phase 
  $E_\pi$ controls sample reuse for the policy 
  $E_V$ controls sample reuse for the true value function 
  $E_\text{aux}$ controls the sample reuse during the auxiliary phase. We increase this to increase sample reuse for the value function. 

[^Cobbe_2020]: Cobbe et al. (2020) [Phasic Policy Gradient](https://arxiv.org/pdf/2009.04416.pdf)

# ACKTR
* **Actor Critic using Kronecker-factored trust region**  [^Yuhai_Wu_2017] 

* It builds upon [[#TRPO]]. It Proposes to use the Kronecker-factored approximation curvature (K-FAC) to perform the gradient updates for both the actor and the critic. 

* We make use of natural gradients rather than our usual gradients. This means that our step sizes are based on the KL divergence from the current network. 
* KFAC approximates the gradient using Kronecker products between smaller matrices 

[^Yuhai_Wu_2017]:  Wu et al. (2017) [Scalable trust-region method for deep reinforcement learning using Kronecker-factored approximation](https://arxiv.org/pdf/1708.05144.pdf)
