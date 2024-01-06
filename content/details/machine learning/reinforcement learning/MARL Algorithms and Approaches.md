# Training and Execution Paradigms 
* **Centralized Training** - a training paradigm where we only make use of  all the information gathered by the agents in the entire system 
* **Decentralized Training** - a training paradigm where we make use of only the local information of each agent. 
* **Decentralized Execution** - the policies of the agents are only conditioned on their local history of observations 
* **Centralized Execution** - the policies of the agents are conditioned based on the information gathered from all agents. 

## CTCE 
* **CTCE** - a special case is **Centralized** models involve each agent pooling experience feeding back to a single learner. Policies are them returned for local execution. 
	* In effect, *we have more agents to help with experience* 
	* All agents have similar policies 
	* We can have a *local independent actor, but a centralized critic*. 
	* This requires that we *transform joint reward into a single scalar reward.* This is a non-trivial task
	* Another challenge is that *it is less scalable* especially when the action space grows exponentially with the number of agents. 
	* It also means that *observations are not localized* and training is based on globally gathered data 


* **Centralized Q-learning** is an approach to learning a policy for stochastic games where we maintain joint action values for joint actions.  It is essentially [[Temporal Difference Learning#Q-Learning|Q-learning]] but on the joint actions and values 

![[Central Q-Learning.png]]
<figcaption> CQL. Image taken from Albrecht, Christianos and Schafer</figcaption>


## DTDE
* A special case is **Independent Learning**, where each agent learns its own policy using only its own local history of observations, actions and rewards, ignoring the existence of other agents.  
	* This allows *adaptation to local perception of the environment*. 
	* A decentralized approach helps when there is an asymmetry in what agents can do. 
	* Each agent uses a copy of the same learning algorithm. 
	* It avoids combinatorial explosion of action spaces 
	* It can be used for problems that require local policies. 
	* It does not require a reward function to be converted to a scalar function. 
	* From the perspective of agent $i$, the other policies $\pi_j$ $j\ne i$ become a part of the environment's state transition function 
	* *They serve as good baselines* which are SOTA. 
	* We are unable to use standard experience replay buffers since the environment now has multiple agents. 
	* *Agents are unable to distinguish between non-stationarity due to other agents or due to the environment itself*
	* *From the perspective of the agent, the environment is non-stationary* because each agent makes a decision that affects the environment. *Learning is more unstable*.
	  
	  $$
	  \mathcal{T}_i(s^{t+1} \mid s^t, a^t) \propto \sum_{a_{-i} \in A_{-i}} \mathcal{T} (s^{t+1} \mid s^t , \braket{a^t_i , a_{-i}}) \ \prod_{j\ne i} \pi_j (a_j \mid s')
	  $$
* Another special case is [[Agent Modeling]]
* *Despite its simplicity, independent learning has been shown to perform competitively to more sophisticated algorithms in multi-agent deep RL*

* **Independent Q-Learning** is a similar approach to CQL but in the context of independent learning 
	* For certain classes of [[MARL from a Game Theoretic Perspective|Stochastic games]], an infinitesimal (using infinitely small learning steps) IQL is guaranteed to converge to a Nash Equilibrium. While, for others it may not converge at all or only under certain conditions. 

![[Independent Q- Learning.png]]
<figcaption> IQL. Image taken from Albrecht, Christianos and Schafer</figcaption>

## CTDE 
* They enable conditioning [[Function Approximation in Reinforcement Learning|approximate value functions]] on privileged information in a computationally tractable manner. 
* They are common since we only need a policy during inference time, but the policy relies on the value function which can be made accurate through Centralized Training. 
* [[Deterministic Policy Gradient#DDPG|DDPG]] plus a centralized learning - decentralized execution approach works (called **MADDPG**). This mixes DDPG's mode-free stability with the centralized approach. This also requires considering the outcome of the choices of all other agents. 

## Fundamental Approaches  to Independent Learning 
* **(Algorithm) Self Play** - agents use the same learning algorithm or same policy. 
	* It helps reduce the non-stationarity that would come from having all agents learn using different algorithms . 
* **(Policy-based) Self-play** -  Algorithms [^self_play] [^self_play_2]  where the agent plays directly against itself to exploit its own weakness. 
	* **Population-based training** - extends self-play by training policies against a [distribution] of other policies, including past versions of themselves. 
	* These may learn faster than algorithm self-play since the experiences of all agents can be used to train a single policy. 
	* It is more restricted in *requiring agents have symmetrical roles and egocentric observations*. 

* **Mixed Play** - agents use different learning algorithms. 
	* **Ad-hoc teamwork** - agents collaborate with previously unknown agents whose behaviors may be unknown. 

* Some algorithms also bridge algorithm self-play and mixed play. 

[^self_play]: Mainly in the context of zero-sum sequential games. 
[^self_play_2]: In usual context, both algorithm and policy-based self play are shortened to simply "self-play"

# Stochastic Game Algorithms 
* [[Joint Action Learning]]
* [[Agent Modeling ]]
* [[Policy-Based Learning]]
* [[Regret Matching]]
* [[MARL Deep Learning]]


# Links 
* [[Multi-Agent Reinforcement Learning -- Foundations and Modern Approaches by Albrecht, Christianos and Schafer|Albrecht, Christianos, and Schafer]] - Ch. 5,6,9 

* [[MARL Problem Statement]]
* [[MARL from a Game Theoretic Perspective]]