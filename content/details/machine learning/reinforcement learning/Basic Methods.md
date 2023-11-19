# Asynchronous Learning 
* The aim is to speed up the process of [[Off Policy Prediction and Control with Approximation#DQN|DQN]] using asynchronous methods -- that is, by running learning in [[Multiprogramming|parallel]].  [^Minh_2016]
* Instead of using replay memory, we rely on different threads running different policies and multiple actors perform exploration (via $\epsilon$-greedy policies where $\epsilon$ is sampled from some distribution)
	* This reduces training time by exploiting parallelism.
	* This allows us to instead use [[On Policy Prediction and Control with Approximation|On policy methods]] with stability guarantees

![[Asynchronous One-Step Q learning.png|300]]<figcaption > Asynchronous Deep Learning. Taken from Mnih et. al (2016)</figcaption>

# A3C 
* **Asynchronous Advantage Actor-Critic**

![[A3C.png]]
<figcaption> A3C. Taken from Algorithm S3 from Mnih et. al (2016) </figcaption>

* Here, critics learn the value function while multiple actors are trained in parallel, and  accumulated updates are performed for more stable and robust training. 
* In practice ,we share some parameters. between the value function and the policy function.

* Updates are performed as follows. Here we let $v(s,w)$ and $\pi_\theta(a_t\mid s_t)$ be the parameterized value and policy respectively and $A_{\pi}(s_t,a_t)$ is the estimated advantage function 
  $$
  \begin{split}
  \nabla_{\theta} \log\pi(a_t\mid s_t,\theta) \ A_\pi(s_t,a_t) \\
  A_\pi(s_t,a_t) = \sum_{i=0}^{k-1}{\gamma^i}R_{t+i} +\gamma^kv(s_{t+k},w) - v(s_t,w)
  \end{split}
  $$
* We may also add the [[Information Theory|entropy]] as a regularization term.
  $$
  \nabla_{\theta} \log\pi(a_t\mid s_t,\theta) \ A_\pi(s_t,a_t)  + \beta \nabla_\theta H(\pi_\theta(s_t))
  $$

# A2C - Advantage Actor-Critic
* A synchronous version of [[#A3C - Asynchronous Advantage Actor-Critic|A3C]] that resolves data inconsistency.
* It introduces a coordinator that waits for all parallel actors to finish their work before updating global parameters. Actors then start from the same policy.
* It can utilize the GPU more efficiently while achieving comparable or better performance to A3C. 

![[A2C.png]]<figcaption>  Image from Lilian Weng https://lilianweng.github.io/posts/2018-04-08-policy-gradient/</figcaption>

[^Minh_2016]: Mnih, et al. (2016) [Asynchronous methods for deep reinforcement learning.](http://proceedings.mlr.press/v48/mniha16.pdf) 

# ACER 
* **Actor Critic With Experience Replay** [^Wang_2017].  It presents an actor-critic method with stable, sample-efficient experience replay.  It is the off-policy counterpart to [[#A3C]]. 
* It makes use of the $Q$ value computed with [[Temporal Difference Learning#Retrace|Retrace]], denoted $Q^\text{ret}$ as a target to train the critic by minimizing 
  
  $$
  (Q^{\text{ret}}(s,a) - Q(s,a))^2
  $$

* To reduce the high variance of the policy gradient, we truncate the importance weights by a constant plus a correction term. We get the gradient $\hat{g}^\text{acer}_t$ as
  
  $$
  \begin{split}
  \hat{g}^\text{acer}_t &=  \min(c,\rho_t) \left(Q^\text{ret} (S_t,A_t) - V_w(S_t)\right) \ \nabla_\theta \ln \pi_\theta (A_t\mid S_t) \\ 
  &+ \mathbb{E}_{a\sim\pi} \left[\max\left(0, \frac{\rho_t(a)-c}{\rho_t} \right) (Q_w(S_t,a) - V_w(S_t)) \nabla_\theta \ln \ \pi_\theta (a\mid S_t)\ \right]
  \end{split}
  $$
  
  
  As a shorthand $\rho_t$ denotes the usual definition of the [[Importance Sampling]] ratio using $A_t$ and $\rho_t(a)$ denotes it on action $a$. 
  
  The first term in the above clips the gradient and adds a baseline $V_w$  to reduce variance.  The second term makes a correction to achieve an unbiased estimation.

* Finally, it makes use of a modified version of [[Trust Region Policies#TRPO|TRPO]] . Instead of using the KL divergence, we maintain a running average of past policies and force the updated policy not to deviate from this average to reduce the variance of policy updates. 

* For continuous actor-critic, we make modifications to the estimate $V_\pi$ and $Q_\pi$ off policy. We compute a stochastic estimate $\tilde{Q_\theta}$  and a deterministic estimate $V_\theta$ given by 
  
  $$
  \tilde{Q_\theta}(x_t,a_t) \sim V_\theta(x_t) + A_\theta (x_t,a_t) - \frac{1}{n}\sum_{i=1}^n A_\theta (x_t,u_i), \ \ \ \ u_i \sim \pi_\theta (\cdot \mid x_t)
  $$
  
  The target then becomes 
  
  $$
  \min\left(1, \frac{\pi(a_t\mid x_t)}{\beta(a_t\mid x_t)}\right) \ (Q^\text{ret} (x_t,a_t) - Q_\theta (x_t,a_t)) + V_\theta (x_t)
  $$
  
  When estimating $Q^\text{ret}$ in continuous domains, we use the following truncated importance weights, where $d$ is the dimensionality of the action space. 
  
  $$
  \rho_t = \min \left(1, \left(\frac{\pi(a_t\mid x_t)}{\beta(a_t \mid x_t)}\right)^{\frac{1}{d}}\right)
  $$
* For trust region updating, we make modify the Retrace estimate by replacing the truncated importance ratio with $1$.

  

![[Discrete ACER.png]]
<figcaption> ACER on discrete actor-critic. Taken from Wang et al. (2017) </figcaption>

![[Continuous ACER.png]]
<figcaption> ACER for continuous actor-ctritic. Taken from Wang et al. (2017)</figcaption>

[^Wang_2017]: Wang et al. (2017) [Sample Efficient Actor-Critic with Experience Replay](https://arxiv.org/pdf/1611.01224.pdf)
