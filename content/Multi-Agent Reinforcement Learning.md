* From a [[Game Theory|Game Theoretic]] perspective, we can compute various solution concepts in the stochastic games that MARL captures. However, computation of these solution concepts is known to be [[Complexity Zoo|NP-hard]]. *Any MARL algorithm will be exponentially hard in the worst case*.
	* This necessitates exploiting structures or assumptions (inductive biases) about certain game types .
# Research 
* *Current (2023) trends suggest that mixed play algorithms more or less perform the same*.  
### VM3-AC
* [^Kim_2023] introduces a new mutual information framework for MARL. This leads to the development of an algorithm called **Variational Maximum Mutual Information, Multi-Agent Actor Critic** which allows agents to coordinate simultaneous actions without latency. 

[^Yang_2021]: Yang and Wang (2021). [An Overview of Multi-agent Reinforcement Learning from Game Theoretical Perspective](https://arxiv.org/pdf/2011.00583.pdf)

[^Kim_2023]: Kim, Cho, Jung, and Sung (2023). [A Variational Approach to Mutual Information Based Coordination for Multi-Agent Reinforcement Learning](https://arxiv.org/pdf/2303.00451.pdf)

# Topics 
* [[MARL -- Notation Guide]]
* [[MARL from a Game Theoretic Perspective]] 
* [[MARL Problem Statement]]
* [[MARL Algorithms and Approaches]]

# Links 
* [[Reinforcement Learning]]
* [[Reinforcement Learning -- Industrial Applications of Intelligent Agents by Winder]] 
* [[Multi-Agent Reinforcement Learning -- Foundations and Modern Approaches by Albrecht, Christianos and Schafer ]]