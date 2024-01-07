* Notation outlined for [[Reinforcement Learning - Notation Guide|reinforcement learning]] and [[Game Theory - Notation Guide|game theory]]  remains relevant unless overwritten here 

* $\mathcal{T}$ - the transition probability of the environment. 
* $^t_i$ - denotes something for agent $i$ taken at time step $t$. 
* $^t$ - denotes something joint (for all agents) taken at time step $t$. 
* $\mu$ - initial state distribution 
* $O_i$ - the set of observations available to agent $i$
* $\mathcal{O}_i$ - agent $i$'s observation function
* $\mathcal{O}$ - the joint observation function. 
* $o$ - a generic observation. 
* $b$ - a belief state 
* $X_i$ - a generic environment action space for agent $i$
* $M_i$ - a generic communication action space for agent $i$,
*****
* $h^t$ - history at time step $t$ 
* $\hat{h}^t$ - the full history starting from time step $0$ up to and including time step $t$.
* $h_i^t$ - the history of agent $i$ at time step $t$. 
* $\hat{H}$ - the set of full histories 
* $U_i(\pi)$ - the return of agent $i$ under policy $\pi$
* $u_i(\hat{h}^t)$ - the discounted return of the agent $i$ in $\hat{h}^t$
* $s(\hat{h})$ - the last state in history $\hat{h}$. 
* $\sigma(\hat{h})$ - the history of observations  
*****
* $\braket{a,b}$ - concatenation. Sometimes this is dropped in favor of the notation $a,b$
* $\pi_c$ - a special joint policy wherein the actions of the agents can be correlated with each other.
* $\xi_i$ - action modifier for correlated equilibrium 
* $W(\pi)$ - the social welfare of a joint policy 
* $F(\pi)$ - the social fairness of a joint policy.
* $\text{Regret}_i^z$ - the regret of the $i$-th agent when examining the history from episode $1$ to $z$ (inclusive).
***** 
* $\bar{\pi}^z$ - empirical distribution obtained from following policy $\pi$. 
* $M_{i,s}$ - minimax solution for agent $i$ and starting at state $s$.
* $\Gamma_{s}(a)$ - JAL-GT game starting from $s$
* $\Gamma_{s,i}(a)$ - JAL-GT game starting from $s$ and entry for agent $i$
* $\hat{\pi}$ - a model for policy $\pi$.
* $C(a)$ - number of times action $a$ was selected 
* $C(a,s)$ - number of times action $a$ was selected when in state $s$.
* $\text{AV}_i(s,a_i)$ - expected value of agent $i$ for taking action $a_i$ when in state $s$
* $\text{VI}$ - value of information 
* $\overline{\pi}$ - average of past policies. 
****
* $d_i$ - difference reward for agent $i$.
* $\bar{a}_i$ - default action 
* $z$ - common information (in centralized value functions)
* $\overline{r}_i^t$ - the utility of agent $i$ at time step $t$.