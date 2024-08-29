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

# Topics 
* [[Basic Policy Gradient Methods]]
* [[Deterministic Policy Gradient]]
* [[Trust Region Policies]]
* [[Energy-Based Reinforcement Learning Models]]
* [[Distributional Reinforcement Learning]]
	* D4PG

# Links
* [[Function Approximation in Reinforcement Learning]]
* [[Off Policy Prediction and Control with Approximation]]
* [[Policy Gradient Methods]]

