* **importance sampling** is a technique  where the expected value under one distribution is estimated given samples of another.
* In the context of [[Reinforcement Learning]], we use it in off-policy learning to match the target with the behavior.

# Standard Definition

* Given a start state $S_t$, we have the probability of a trajectory $A_{t}, S_{t+1}, \dots, S_T$ as
  $$
  P_\pi(A_t,S_{t+1},\dots,S_T\mid S_{t})=\prod_{k=t}^{T-1}\pi(A_k\mid S_k) \ p(S_{k+1}\mid S_k, A_k)
  $$
  And the **importance sampling ratio** is given as the relative probability of the trajectory under the target and behavior 
  $$
  \rho_{t:T-1} = \frac{P_\pi (A_t, S_{t+1}\dots,S_T \mid S_t)}{P_\beta(A_t, S_{t+1},\dots,S_T\mid S_t)}
  $$
  
* The importance sampling ratio is then applied to $G_t$, the returns in the behavior policy. We have that 
  $$
  \mathbb{E}[\rho _{t:T-1}G_t\mid S_t=s] = v_\pi(s)
  $$
  
* We can perform **ordinary importance sampling** by taking a normal average. Let $\mathcal{T}(t)$ denote the first time of termination after $t$  
  $$
  V(s)=\frac{\sum_{t\in\mathcal{T}(s)} \ \rho_{t:T(t)-1} \ G_t}{|\mathcal{T}(s)|}
  $$
* **Weighted importance sampling** is done using a weighted average. 
  $$
  V(s)=\frac{\sum_{t\in\mathcal{T}(s)} \ \rho_{t:T(t)-1} \ G_t}{\sum_{t\in\mathcal{T}(s)}  \ \rho_{t:T(t)-1}}
  $$
  Or $0$ if the denominator of $0$.

# Variants
### Discounting-Aware
* In the context of discounted returns, we may make use of **discounting-aware importance**. 
	* We interpret the discount rate as a *degree of partial termination*. The return can be written as 
	  $$
	  G_{t} = (1-\gamma)\sum_{h=t+1}^{T-1}\gamma^{h-t-1}\bar{G}_{t:h} + \gamma^{T-t-1}\bar{G}_{t:T}
	  $$
	  Where $\bar{G}_{t:h}=R_{t+1}\dots+R_h$ is the **flat return**  (where discount rate is $1$ and the sum is up to horizon $h$).
	* The estimator is then obtained by using the standard formula for importance sampling (see above), but where $\bar{G}_{t:h}$ is scaled by $\rho_{t:h-1}$ and $\bar{G}_{t:T}$ by $\rho_{t:\mathcal{T}(t)-1}$. $T(t)$ denotes the first termination time step after $t$.

### Per-Step
* The **per-step importance sampling ratio** is defined as follows for target $\pi$ and behavior $\beta$
  
  $$
  \rho_t=\frac{\pi(A_t\mid S_t)}{\beta(A_t,S_t)}
  $$
  
### Per-Decision
* We may also consider **per decision sampling** Based on the observation that 
  $$
  \rho_{t:T-1}G_t=\rho_{t:T-1}(R_{t+1}+\gamma R_{t+2} + \dots +\gamma^{T-t-1}R_T)
  $$
  In place of $G_t$, we use the following in ordinary importance sampling 
  $$
  \bar{G}_t = \rho_{t:t}R_{t+1} +\gamma\rho_{t:t+1} R_{t+2} + \dots + \gamma^{T-t-1}\rho_{t:T-1}R_T
  $$
  And 
  $$
  V(s)=\frac{\sum_{t\in \mathcal{T}(s)} \bar{G_t}}{|\mathcal{T}(s)|}
  $$
  [^a]
[^a]: Note: It is less clear if there is a weighted per-decision importance sampling. These estimators are [[Statistical Estimators#Properties of Good Estimators|inconsistent]]

### N-step Returns 
* We extend importance sampling to apply to [[N-step Bootstrapping|n-step returns]] by using the following importance sampling ratio
  $$
  \rho_{t+h}=\prod_{k=t}^{\min(h,T-1)} \frac{\pi(A_k\mid S_k)}{\beta(A_t\mid S_t)}
  $$
  Where $\beta$ is the behavior function.
	* When an action would never be taken by the policy $\pi$, we no longer explore it.
	* When an action has $\pi>\beta$, it is characteristic of $\pi$ but is rarely explored. To compensate for the rare exploration, we give it higher weight (which is consistent with the importance sampling ratio's properties).

# Links
* [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto Ch. 5, 7]]
	* 5.5 - more information about Information Sampling.
	* 5.8 -  discounting-aware importance sampling.
	* 5.9 - per-decision importance sampling.
	* 7.3 - Importance Sampling for n-step Off-policy Learning.