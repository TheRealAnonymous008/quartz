# Overview
* The **eligibility trace*** $z_t\in \mathbb{R}^d$ acts as a *short-term memory vector* that parallels the weights in [[Function Approximation in Reinforcement Learning|function approximation]].
* When a component in $w_t\in \mathbb{R}^d$ participates in estimation, the corresponding component to $z_t$ is bumped up and then begins to fade away based on parameter $\lambda$. 
* Learning occurs in a component of $w_t$ if a non-zero TD-error occurs before the trace falls back to zero. 
* Compared to [[Temporal Difference Learning#N-Step Bootstrapping|n-step bootstrapping]], Eligibility traces offer computational advantages. 
	* We no longer need to store $n$ feature vectors, just the $d$-dimensional trace.
	* Learning occurs continually and uniformly rather than being delayed $n$ steps.

* One way to view this is as *an extension of interpolating between Temporal Differencing  and Monte Carlo* methods
	* **On-line updates** perform the updates during the episode itself.
	* **Off-line updates** perform the updates after the episode (possibly in batches of episodes). All updates are accumulated as they happen. 
	* **Error reduction property**  With updates, the $n$-step return $R_{\Sigma}$ converges a better estimate of the value function as $n\to\infty$.
* Another way is to view this as keeping a temporary record of **which components ( states / actions / components in the weight vector) are eligible for learning changes.** 
	* We are concerned with the TD errors in particular. 
* Eligibility traces make use of **compound updates** -- averaging over simpler updates.

# The $\lambda$ return and $\text{TD}(\lambda)$
* $\lambda$ is called the **trace decay**. 
	* $\lambda$ controls how much credit we give to earlier states when we perform updates
* The **$\lambda$-return** is defined as 
  $$
  G_t^\lambda=(1-\lambda)\sum_{n=1}^\infty\lambda^{n-1}G_{t,t+n}
  $$
  
	* Each $n$-step return is weighted with $\lambda^{n-1}$. The whole some is renormalized using the $(1-\lambda)$ term.
	* An alternative formulation if we terminate at time $T$ is as follows: 

$$
  G_t^\lambda=(1-\lambda)\sum_{n=1}^T\lambda^{n-1}G_{t,t+n} + \lambda^{T-t-1}G_t
$$
* In the **off-line update algorithm**, performing the updates follows the usual [[Off Policy Prediction and Control with Approximation#Semi-Gradient Methods|semi gradient approach]] with $G_t^\lambda$ as the target. 
* In $TD(\lambda)$  the eligibility vector is computed as follows:

$$
\begin{split}
z_{-1}&=0 \\
z_t &= \gamma \ \lambda z_{t-1} + \nabla \hat{v}(S_t,w_t) \ \ \ 0\le t\le T
\end{split}
$$

* $TD(\lambda)$ is more preferable than the off-line update algorithm because
	* It performs a backward update -- on every step of an episode rather than only at the end. *Estimates are better sooner than later*
	* Its computations are properly amortized -- distributed in time.
	* It can be applied to continuing problems. 
		* $TD(1)$ is a variation of [[Monte Carlo Methods in Reinforcement Learning|Monte Carlo]] but applicable for continuous tasks.

* Linear $TD(\lambda)$ converges, but not to the minimum-error vector. For the continuing discounted case:

$$
\overline{\text{VE}}(w_\infty) \le \frac{1-\gamma\lambda}{1-\gamma}\min_w \overline{\text{VE}} (w)
$$





* At each time step $E_t(s)=\gamma\lambda E_{t-1}(s)$ That is, *decay the eligibility trace*.
* When state $s$ is visited for the current time step *add a quantity to the eligibility trace*.
	* The best one to use appears to be **Dutch Traces** with step size $\alpha=0.5$
* $E_t(s)$ above is then used to update the value function as follows 
  $$
  \delta=R_{t+1}+\gamma V(S_{t+1})-V(S_{t})
  $$
  
  And $\forall s\in S$
  $$
  V(s)\gets V(s)+\alpha\delta E_t(s)
  $$
  
* *In practice, we only ever really need to keep track of the eligibility of some states since most of the time, the eligibility is effectively $0$*. 
# $\text{SARSA}(\lambda)$
* An extension of SARSA but making use of Eligibility traces. We substitute the value function with a the state-action function $Q(s,a)$ and the eligibility traces are now over the space of state-action pairs.
* Like SARSA, it is an **on-policy** algorithm.
# Watkins' $Q(\lambda)$
* Extends Q-learning to make use of eligibility traces. 
* One caveat of this is that, instead of looking ahead all the way to the end, it only looks ahead *as far as the action after the first exploratory action* (or to the episode's end if none exist)
* Whenever a non-greedy action is taken, the eligibility trace at that point is set to $0$.
* *Note:* This relies on the action sequence of the behavior policy having few exploratory actions, as otherwise this performs no better than one-step Q-learning.
* *Watkins $Q(\lambda)$ is a crude way to perform off-policy tracing.* However, we must consider the following:
	* Use Importance sampling to assign credit for actions, since actions are taken based on a probability distribution so following the greedy action is dependent on this probability.
	* It does not actually bootstrap since it cuts off estimation after the first non-greedy action is taken.
# Varying $\lambda$
* Another (*theoretical*) technique for generalizing the $\lambda$-return is by allowing $\lambda$ to vary from step to step.
* One rationale for this is to give states whose value we are highly certain of, more credit (higher eligibility) for the return.
# Links
* [[Temporal Difference Learning]] - for more info on the basic case $\text{TD}(0)$. 
* [[Monte Carlo Methods in Reinforcement Learning]] - for more on Importance sampling
* [[A Unified View on Reinforcement Learning Approaches]]

* [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto Ch. 7]]
	* 7.4 - explains why the two views of eligibility tracing are equivalent.
	* 7.5 - covers $\text{SARSA}(\lambda)$
	* 7.6 - covers Watkins' $Q(\lambda)$