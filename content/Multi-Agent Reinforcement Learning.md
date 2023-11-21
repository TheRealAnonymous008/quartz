# Problem Statement 
* [^Yang_2021] We formulate the MARL problem using an extension of [[Markov Processes in Machine Learning|MDPs]]. 
* A **stochastic game** is defined as a set of key elements $(N, s, \{A^i\}_{i\in \{1,\dots, N\}}, \  p \ , \{R^i\}_{i\in \{1,\dots, N\}}, \gamma)$
  
  $N$ is the number of agents. 
  $S$ is the set of environmental states shared by all agents. 
  $A^i$ is the set of actions of the $i$-th agent. The set of all action configurations is denoted $\mathbb{A}=\mathcal{A}^1\times\dots\times \mathcal{A}^N$ 
  $p:S\times\mathbb{A}\to S$ for each time step $t\in N$ gives the **transition probability** from state $s$ to $s'$
  $R^i: S\times \mathbb{A} \to S$ is the reward function for the $i$-th agent
  $\gamma\in [0,1]$ gives the discounting factor. 
  
  As a convention, we use the superscript $a^i$ for the $i$-th agent and $a^{-i}$ for all other agents. 

* In this context, *all agents simultaneously make decisions*. Each agent aims to find a policy $\pi^i$ so that its reward function is maximized. 

# Research 
### VM3-AC
* [^Kim_2023] introduces a new mutual information framework for MARL. This leads to the development of an algorithm called **Variational Maximum Mutual Information, Multi-Agent Actor Critic** which allows agents to coordinate simultaneous actions without latency. 

[^Yang_2021]: Yang and Wang (2021). [An Overview of Multi-agent Reinforcement Learning from Game Theoretical Perspective](https://arxiv.org/pdf/2011.00583.pdf)

[^Kim_2023]: Kim, Cho, Jung, and Sung (2023). [A Variational Approach to Mutual Information Based Coordination for Multi-Agent Reinforcement Learning](https://arxiv.org/pdf/2303.00451.pdf)

# Links 
* [[Reinforcement Learning]]