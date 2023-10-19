# Two Views of Eligibility Traces
* One way to view this is as *an extension of Temporal Differencing towards becoming more like Monte Carlo* methods. This is done through $\text{TD-n}$ and $TD(\lambda)$
	* $\text{TD-n}$ involves generalizing $R_{\Sigma}$ to include more terms. Namely $$R_{\Sigma,n}=R_{t+1}+\gamma R_{t+2}+\dots +\gamma^{n}V_t(S_{t+n})$$
	* **On-line updates** perform the updates during the episode itself.
	* **Off-line updates** perform the updates after the episode (possibly in batches of episodes). All updates are accumulated as they happen. 
	* **Error reduction property**  With updates, the $n$-step return $R_{\Sigma}$ converges a better estimate of the value function
* Another way is to view this as keeping a temporary record of **which events (state / action visitation) are eligible for learning changes.**
# $\text{TD}(\lambda)$
* $\text{TD}(\lambda)$ involves *updating based on a weighted average* of all the $\text{TD-n}$ $\forall n\in \mathbb{N}$. More formally the $\lambda$-return is defined as $$L_t=(1-\lambda)\sum_{n=1}^\infty\lambda^{n-1}R_{\Sigma,n}$$
* Mechanically, $\text{TD}(\lambda)$ is computed using the backward view of eligibility tracing. That is, we obey the following rules. The eligibility of state $s$ at time $t$ is given as $E_t(s)$, and is updated as follows:
	* At each time step $E_t(s)=\gamma\lambda E_{t-1}(s)$ That is, *decay the eligibility trace*.
	* When state $s$ is visited for the current time step *add a quantity to the eligibility trace*.
		* The best one to use appears to be **Dutch Traces** with step size $\alpha=0.5$
* $E_t(s)$ above is then used to update the value function as follows $$\delta=R_{t+1}+\gamma V(S_{t+1})-V(S_{t})$$And $\forall s\in S$$$V(s)\gets V(s)+\alpha\delta E_t(s)$$
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

* [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto Ch. 7]]
	* 7.4 - explains why the two views of eligibility tracing are equivalent.
	* 7.5 - covers $\text{SARSA}(\lambda)$
	* 7.6 - covers Watkins' $Q(\lambda)$