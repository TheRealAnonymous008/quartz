# General Frameworks 
* **Centralized Q-learning** is an approach to learning a policy for stochastic games where we maintain joint action values for joint actions.  It is essentially [[Temporal Difference Learning#Q-Learning|Q-learning]] but on the joint actions and values 

![[Central Q-Learning.png]]
<figcaption> CQL. Image taken from Albrecht, Christianos and Schafer</figcaption>

* **Independent Q-Learning** is a similar approach to CQL but in the context of independent learning 
	* For certain classes of [[MARL from a Game Theoretic Perspective|Stochastic games]], an infinitesimal (using infinitely small learning steps) IQL is guaranteed to converge to a Nash Equilibrium. While, for others it may not converge at all or only under certain conditions. 

![[Independent Q- Learning.png]]
<figcaption> IQL. Image taken from Albrecht, Christianos and Schafer</figcaption>


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


# Links 
* [[Multi-Agent Reinforcement Learning -- Foundations and Modern Approaches by Albrecht, Christianos and Schafer]]

* [[MARL Problem Statement]]
* [[MARL from a Game Theoretic Perspective]]