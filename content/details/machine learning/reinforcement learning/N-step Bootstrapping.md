* These methods act as intermediates in the spectrum between [[Monte Carlo Methods in Reinforcement Learning|Monte Carlo]] (update at the end of the episode) and [[Temporal Difference Learning|TD]](0) (update immediately after),
* **$n$-step TD methods** are those that update based on the temporal difference over $n$ steps.
# Prediction
* The return for an $n$-step update is defined as
  $$
  G_{t:t+n}=R_{t+1}+\gamma R_{t+2}
  +\dots+\gamma^{n-1}R_{t+n}+\gamma^n V_{t+n-1}(S_{t+n})
  $$
  For all $n\ge 1$ and $0\le t < T-n$ 
* The n-step return is an *approximation to the true return by truncating it after $n$ steps*.
* We learn the state updates by using the following (simply substitute the n-step return for the formula in [[#TD Prediction]]
  $$
  V_{t+n}(S_t)=V_{t+n-1}(S_t)+\alpha\left[ G_{t:t+n} -V_{t+n-1}(S_t)\right]
  $$
  
* To compensate for the fact we do not perform updates at the first $n-1$ steps in the beginning, we make the updates at the end of the episode after termination and before starting the next episode.
* Like Monte Carlo, the n-step return can be *written as a sum of TD errors*.  
  $$
  G_{t:t+n}-V_{t+n}(S_t)=\sum_{k=t}^{t+n-1}\gamma^{k-1}\delta _k
  $$
  
[^1]
* **The Error Reduction Property** of $n$-step returns means that the worst error of the expectation of an $n$-step return is guaranteed to be a better estimate of $v_\pi$ than $V_{t+n-1}$ is. 
  $$
  \max_s\left|\mathbb{E}_\pi \left[ G_{t:t+n} \mid S_t=s\right] - v_\pi(s)\right| \le \gamma^n \max_s \left|V_{t+n-1}(s)-v_\pi (s)\right|
  $$
  
	* This implies convergence to correct predictions as our n-step returns get progressively closer to the true value.

[^1]: Deriving this is a straightforward substitution, assuming the value function doesn't change.

# n-step SARSA
* A generalization of SARSA. 
* It still makes uses of sample transitions.
* We simply redefine the $n$-step return to make use of $Q$. 
  $$
  G_{t:t+n}=R_{t+1}+\gamma R_{t+2} +\dots +\gamma^{n-1}R_{t+n}+\gamma^n Q_{t+n-1}(S_{t+n},A_{t+n})
  $$
  And $G_{t:t+n}=G_t$ if $t+n\ge T$. 

* The update rule becomes 
  $$
  Q_{t+n}(S_t,A_t)=Q_{t+n-1}(S_t,A_t) + \alpha\left[G_{t:t+n} -Q_{t+n-1}(S_t,A_t)\right]
  $$
  
* The value of other states remain unchanged. That is $Q_{t+n}(s,a)=Q_{t+n-1}(s,a)$ for all $s,a$ such that $s\ne S_t, a\ne A_t$. 

# n-step Expected SARSA
* It makes use o sample transitions, except for the last state which is fully branched.
* Extends $n$-step SARSA as follows. We redefine the $n$-step return as 
  $$
  G_{t:t+n}=R_{t+1}+\gamma R_{t+2} +\dots +\gamma^{n-1}R_{t+n}+\gamma^n \hat{V}_{t+n-1}(S_{t+n})
  $$
  And $G_{t:t+n}=G_t$ if $t+n\ge T$. 
* We call $\hat{V}$ the **expected approximate value** which is defined as 
  $$
  \hat{V}_t(s)=\sum_{a}\pi(a\mid s)Q_t(s,a)
  $$
  
* If $s$ is a terminal state, then the expected approximate value is defined as $0$.

# $n$-step Off-Policy Learning
* We make use of the [[Importance Sampling#N-step Returns|importance sampling ratio for n-step returns]] $\rho$.
* The update rule then becomes weighted with $\rho$ as follows 
  $$
  V_{t+n}(S_t)=V_{t+n-1}(S_t)+\alpha \rho_{t:t+n-1}\left[ G_{t:t+n} -V_{t+n-1}(S_t)\right]
  $$
  
* For using the Q function we use $\rho_{t+1:t+n}$ since we update on state-action pairs. 
* For expected SARSA, we use $\rho_{t+1 : t+n-1}$. All possible actions are taken into account in the last state; the one actually taken has no effect and does not have to be corrected for.

* *The drawback with off-policy methods is shown here -- it requires slower training since it has higher variance updates*.

# Control Variates
* *One problem with importance sampling is high variance, especially when actions may not be taken*
* We modify the definition of the return in this case to make use of an *off-policy definition*
  $$
  G_{t:h}=\rho_t(R_{t+1}+\gamma_{t+1:h}) + (1-\rho_t)V_{h-1}(S_t)
  $$
  and where $G_{h:h}=V_{h-1}(S_h)$. 
	* Here we remove the problem of high variance by having the target equal the estimate (i.e., do not change when $\rho_t=0$).
* For action values, we apply importance sampling to actions except the first.
	* *Rationale*: The first action is being evaluated and has already been taken, so the reward must be learnt in full.
	* The formula becomes 
	  $$
	  G_{t:h}=R_{t+1}+ \gamma \rho_{t+1} \left( G_{t+1:h} -Q_{h-1}(S_{t+1},A_{t+1})\right)+\gamma\hat{V}_{h-1}(S_{t+1})
	  $$
	  
	* If $h<T$, we have $G_{h,h}=Q_{h-1}(S_h,A_h$)
	* Otherwise, $G_{T-1:h}=R_T$.

# Tree Backup Algorithm
* It makes use of all state transitions fully branched without sampling.
* In Tree-backup, *updates are performed from the leaves of the tree. The actual actions taken do not participate*.
* Each leaf contributes to the target with a weight proportional to its probability of occurring under target policy $\pi$.
* Actions taken contribute to the probability of the leaves in the next level down.
* At the last node of the tree backup diagram, we consider all actions as untaken.

* We use the same one step return target $G_{t:t+1}$ as [[#Expected SARSA]]. This form is generalized as follows 
  $$
  G_{t:t+n}=R_{t+1}+\gamma\sum_{a\ne A_{t+1}} \pi(a\mid S_{t+1} ) \ Q_{t+n-1}(S_{t+1}, a) + \gamma\pi(A_{t+1}\mid S_{t+1}) G_{t+1:t+n}
  $$
  For $t<T-1$, $n\ge 2$. 
* A special case: $G_{T-1:t+n}=R_T$.

* The target is then used for the usual action-value update from [[#n-step SARSA]].

# n-Step $Q(\sigma)$
* Unifies [[#n-step SARSA]], [[#Expected SARSA]], and [[#Tree Backup Algorithm]] by providing  a choice. Either we fully branch or take samples based on some probability $\sigma_t$ at time step $t$.
	* If we fully branch all the time we get Tree Backup.
	* If we take samples, all the time we get SARSA.
	* If we take samples except for the last state we get Expected SARSA.
* $\sigma_t$ may be a function on a state, action, or state-action pair at $t$
* We use $\sigma_t$ as an interpolator. The return is now defined as 
  $$
  G_{t:h}=R_{t+1} + \gamma\left(\sigma_{t+1}\rho_{t+1} + (1-\sigma_{t+1})\pi(A_{t+1}\mid S_{t+1})\right) \left(G_{t+1:h} -Q_{h-1} (S_{t+1},A_{t+1})\right) + \gamma \hat{V}_{h-1}(S_{t+1})
  $$
  
  For $t<h<T$.
  
  If $h<T$, we end with $G_{t:h}=Q_{h-1}(S_h,A_h)$. 
  
  If $h=T$, we end with $G_{T-1:T} = R_T$.

* We then perform the update defined in [[#Control Variates|n-step SARSA with control variates]] except without importance sampling ratios. 

![[Qsigma.png]]<figcaption> General N-step bootstrapping. Image taken from Sutton and Barto (2017) </figcaption>

# Links
* [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto Ch. 7]]
	* 7.2 - n-step SARSA
	* 7.4 - Control Variates
	* 7.5 - Tree Backup
	* 7.6 - $Q(\sigma)$. 