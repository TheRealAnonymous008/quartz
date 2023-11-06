# All Actions Update
* Update using the following rule
$$
\theta_{t+1} = \theta_t +\alpha \sum_a \hat{q}(S_t,a,w)\ \nabla \pi(a\mid S_t,\theta)
$$
# REINFORCE: Monte Carlo Policy Gradient
* Update, at time $t$ only the action $A_t$.
* We redefine $J(\theta)$ as follows. We replace $a$ by the sample $A_t\sim \pi$ and note that $q_\pi(S_t,A_t)$ is the expected return.

$$
\begin{split}
\nabla J(\theta)
&= \mathbb{E}_{\pi_\theta} \left[\pi_\theta(a\mid S_t,\theta) \ q_{\pi_\theta}(S_t,a) \frac{\nabla\pi_\theta(a\mid S_t)}{\pi_\theta(a\mid S_t)}\right] \\ 
&= \mathbb{E}_{\pi_\theta}\left[q_{\pi_\theta} (S_t,A_t) \frac{\nabla\pi_\theta(a\mid S_t)}{\pi_\theta(a\mid S_t)} \right] \\ 
&= \mathbb{E}_{\pi_\theta}\left[G_t \frac{\nabla\pi_\theta(a\mid S_t)}{\pi_\theta(a\mid S_t)}\right] \\
&= \mathbb{E}_{\pi_\theta}\left[G_t \nabla \ln \pi_\theta(a\mid S_t)\right]
\end{split}
$$
* The above approach makes it so that actions that are updated frequently are updated in small increments (to balance out the frequency).
* The vector $\nabla \ln \left(\pi_\theta(a\mid S_t,\theta)\right)$ is called the **eligibility vector**
* REINFORCE has *high variance and slow learning* being [[Monte Carlo Methods in Reinforcement Learning|Monte Carlo]]. However, it has convergence guarantees.
	* We can add a [[#Baselines|baseline]] to the regular REINFORCE algorithm in order to reduce variance. 

# Actor-Critic Methods
* Act as analogues to [[Temporal Difference Learning]] and [[N-step Bootstrapping]] but for Policy Gradient Methods.
* Rather than have an estimate that solely relies on the full return (as in Monte Carlo approaches such as [[#REINFORCE Monte Carlo Policy Gradient|REINFORCE]]), we instead have an n-step estimate coupled with a learned baseline.

$$
\theta_{t+1} = \theta_t + \alpha \left(G'_t -\hat{v} (S_t,w)\right) \nabla \ln \pi_\theta(a\mid S_t)
$$

Where $G_t'$ is a generalization for our return. It could be the one-step return from regular TD, or the n-step return $G_{t:t+n}$ or even an [[Eligibility Traces|eligibility trace]] $G_t^\lambda$. 

# Off-Policy Methods 
### Asynchronous Learning 
* The aim is to speed up the process of [[Off Policy Prediction and Control with Approximation#DQN|DQN]] using asynchronous methods -- that is, by running learning in [[Multiprogramming|parallel]].  [^Minh_2016]
* Instead of using replay memory, we rely on different threads running different policies and multiple actors perform exploration (via $\epsilon$-greedy policies where $\epsilon$ is sampled from some distribution)
	* This reduces training time by exploiting parallelism.
	* This allows us to instead use [[On Policy Prediction and Control with Approximation|On policy methods]] with stability guarantees

![[Asynchronous One-Step Q learning.png|300]]<figcaption > Asynchronous Deep Learning. Taken from Mnih et. al (2016)</figcaption>

### A3C - Asynchronous Advantage Actor-Critic

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

### A2C - Advantage Actor-Critic
* A synchronous version of [[#A3C - Asynchronous Advantage Actor-Critic|A3C]] that resolves data inconsistency.
* It introduces a coordinator that waits for all parallel actors to finish their work before updating global parameters. Actors then start from the same policy.
* It can utilize the GPU more efficiently while achieving comparable or better performance to A3C. 

![[A2C.png]]<figcaption>  Image from Lilian Weng https://lilianweng.github.io/posts/2018-04-08-policy-gradient/</figcaption>

[^Minh_2016]: Mnih, et al. (2016) [Asynchronous methods for deep reinforcement learning.](http://proceedings.mlr.press/v48/mniha16.pdf) 

# Deterministic Policy Gradients 
### DPG 
* Introduces deterministic policy gradient algorithms for RL with continuous actions [^Silver_2014]

[^Silver_2014]: Silver, et al. (2014) [“Deterministic policy gradient algorithms."](https://hal.inria.fr/file/index/docid/938992/filename/dpg-icml2014.pdf) 
# Links
* [[Off Policy Prediction and Control with Approximation]]
* [[Policy Gradient Methods]]

