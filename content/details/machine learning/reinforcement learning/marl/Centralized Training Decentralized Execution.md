* **CTDE** is an approach in training [[Multi-Agent Reinforcement Learning|MARL]]agents.
	* They enable conditioning [[Function Approximation in Reinforcement Learning|approximate value functions]] on privileged information in a computationally tractable manner. 
	* They are common since we only need a policy during inference time, but the policy relies on the value function which can be made accurate through Centralized Training. 
	* [[Deterministic Policy Gradient#DDPG|DDPG]] plus a centralized learning - decentralized execution approach works (called **MADDPG**). This mixes DDPG's mode-free stability with the centralized approach. This also requires considering the outcome of the choices of all other agents. 

# Centralized  Critics
* We can use [[Policy Gradient Method Algorithms#Actor-Critic Methods|Actor Critic Methods]] since a centralized critic can be used to train decentralized actors. Empirically, we can observe that they have the following advantages. 
	* Eased learning 
	* Learning coordinated behaviors
	* Improved performance
	* Reduced variance
	* More robustness.




# Links
* [[Multi-Agent Reinforcement Learning -- Foundations and Modern Approaches by Albrecht, Christianos and Schafer|Albrecht, Christianos, and Schafer]]
* [[MARL Algorithms and Approaches]] 