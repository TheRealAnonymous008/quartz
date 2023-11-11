# DPG 
* Introduces deterministic policy gradient algorithms for RL with continuous actions [^Silver_2014]
* The goal is to learn a deterministic policy from a stochastic behavior policy via an off-policy actor-critic algorithm.
* Specific to this, let $\mu_\theta$ be  a deterministic policy with parameter $\theta$,  and let $\rho^\mu(s)$ be the discounted state distribution defined as
  
  $$
  \rho^\mu(s') = \int_S \sum_{t=1}^\infty \gamma^{k-1} \rho_0(s) \ p(s\to s',t) \ ds
  $$
  
  The objective becomes 
  
  $$
  J(\mu_\theta) = \int_S \rho^\mu(s) \ Q^\mu(s,\mu_\theta(s)) \ ds
  $$
  
* **Deterministic Policy Gradient Theorem**. 
  $$
  \begin{split}
  \nabla_\theta J(\mu_\theta) &= \int _S \rho^\mu (s)\nabla_aQ^\mu (s,a) \ \nabla_\theta \mu_\theta(s)\mid _{a=\mu_\theta(s)} \ ds \\ 
  &= \mathbb{E} _{s\sim \rho^\mu} \left[\nabla_\theta \mu_\theta(s)\mid _{a=\mu_\theta(s)} \right]
  \end{split}
  $$

* *(Silver Th.2)* If the stochastic policy $\pi_{\mu_\theta,\sigma}$ is re-parameterized to deterministic policy $\mu_\theta$ and variation variable $\sigma$, the stochastic policy is eventually equivalent to the deterministic case is eventually equivalent to the deterministic case where $\sigma=0$. However, this will require more samples . More formally 
  
  $$
  \lim_{\sigma\to 0} \nabla_\theta J(\pi_{\mu_\theta, \sigma}) = \nabla_\theta J (\mu_\theta)
  $$
  
  Which implies *stochastic policy gradient algorithms can be applied to deterministic policy gradient.*

#### On-Policy Deterministic Actor Critic 
* Actor takes actions deterministically $a=\mu_\theta(s)$. We then use [[Temporal Difference Learning#SARSA|SARSA]] update and combine it with the Deterministic Policy Gradient Theorem .
  
  $$
  \begin{split}
  \delta_t &= r_t + \gamma Q^w(s_{t+1}, a_{t+1}) - Q^w(s_t,a_t) \\ 
  w_{t+1} &= w_t + \alpha_w \delta_t \ \nabla_w Q^w(s_t,a_t) \\ 
  \theta_{t+1} &= \theta_t + \alpha_\theta \ \nabla_\theta \mu_\theta (s_t) \nabla_a Q^w (s_t,a_t) \mid _{a=\mu_\theta(s)}  
  \end{split}
  $$
* *Disadvantage*: No guarantees of optimality when we do not explore enough. 

#### Off-Policy Deterministic Actor-Critic 
* The objective is now arranged over the state distribution of the behavior policy $\beta$

$$
\begin{split}
J_\beta(\theta) &= \int_S \rho^\beta Q^\mu(s, \mu_\theta(s)) \ ds  \\ 
\nabla_\theta J_\beta (\theta) &= \mathbb{E}_{s\sim\rho^\beta} \left[ \nabla_a Q^\mu (s,a) \nabla _\theta \mu_\theta (s) \mid_{a=\mu_\theta(s)}\right]
\end{split} 
$$
* The update is then done by performing the same update as the on-policy case. 
* *Note*: We typically use [[Importance Sampling]] when using off-policy methods. However, because the deterministic policy gradient removes the integral over actions, we do not need importance sampling in the actor and the critic.

* (*Silver Th.3*)  - We can find a critic $Q^w(s,a)$ such that the gradient $\nabla_aQ^\mu(s,a)$ can be replaced by $\nabla_aQ^w(s,a)$ without affecting the policy gradient if the following holds:
1. $\nabla_a Q^w(s,a) \mid_{a=\mu_\theta(s)} = \nabla_\theta \mu_\theta(s)^T w$ 
2. $w$ minimizes the MSE 
   $$
   \begin{split}
   \text{MSE}(\theta,w) &= \mathbb{E}\left[\epsilon(s\mid\theta,w) ^T \epsilon(s\mid\theta,w)\right] \\
   \epsilon(s\mid\theta,w) &= \nabla_{a}Q^w(s,a) \mid _{a=\mu_\theta(s)} - \nabla_{a}Q^\mu(s,a) \mid _{a=\mu_\theta(s)}
   \end{split}
   $$
* For any deterministic policy, we can take the following as the function approximator
  $$
  Q^w(s,a) = (a-\mu_\theta(s))^T \nabla_\theta (\mu_\theta(s))^T w + b(s) 
  $$
  
  Where $b(s)$ is a baseline function independent of the action. 
* A linear function approximator is sufficient to select the direction in which the actor should adjust its policy parameters.

[^Silver_2014]: Silver, et al. (2014) [“Deterministic policy gradient algorithms."](https://hal.inria.fr/file/index/docid/938992/filename/dpg-icml2014.pdf) 
# DDPG
* Presents an actor-critic model free algorithm using DPGs operating on continuous action spaces. [^Lillicrap_2015]. 
* We make use of **soft target updates**. This is done by creating a copy of the actor and critic networks $Q^w(s,a)$ and $\mu^\theta(s)$. The weights are then updated by having them slowly track the learned networks. 
  
  $$
  \theta' \gets \tau\theta + (1-\tau)\theta' \ \ \ \ \tau \ll 1
  $$
*  *This makes target values change slowly and improves stability. At the cost of slowing learning.*
  
* This also makes use of *batch normalization* to minimize covariance shift during training. 
* To do better exploration, the exploration policy $\mu'$ is constructed [^ddpg-a] by *adding noise* $\mathcal{N}$
  
  $$
  \mu'(s) = \mu_\theta(s) +\mathcal{N}
  $$

![[DDPG.png]]

[^Lillicrap_2015]: Lillicrap, et al. (2019) [Continuous Control with Deep Reinforcement Learning](https://arxiv.org/pdf/1509.02971.pdf)
[^ddpg-a]: The authors make use of an Ornstein-Uhlenbeck process to generate temporally correlated exploration for exploration efficiency in physical control problems with inertia. 
# D4PG
# TD3
