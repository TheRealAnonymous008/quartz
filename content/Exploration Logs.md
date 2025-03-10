* [^qu_2019] present **BlockBERT** an efficient [[BERT|BERT]]  model for modeling long-distance dependencies using sparse block structures. 
	* *Rationale*: Memory is a bottleneck in training BERT.  In particular, it grows $O(L^2)$, quadratically with respect to sequence length.
	* It promises to be simpler than the approach by [^child_2019]
	* We design the masking matrix $M$ used in the formulation for (masked) attention to be a sparse block matrix. 

[^Qu_2019]: Qu et al. (2019) [Blockwise Self-Attention for Long Document Understanding](https://arxiv.org/abs/1911.02972)

[^Ainslie_2020]: Anislie et al. (2020) [ETC - Encoding Long and Structured Inputs in Transformers](https://aclanthology.org/2020.emnlp-main.19/)

[^Beltagy_2020]: Beltagy, Peters and Cohan (2020) [Longformer - The Long Document Transformer](https://arxiv.org/abs/2004.05150)

[^Zaheer_2020]: Zaheer et al. (2020) [Big Bird - Transformers for Longer Sequences](https://arxiv.org/abs/2007.14062)

[^Kitaev_2020]: Kitaev, Kaiser and Levskaya (2020) [Reformer - The Efficient Transformer](https://arxiv.org/abs/2001.04451)

[^Gomez_2017]: Gomez, Reen, Urtasun, and Grosse (2017) [The Reversible Residual Network: Backpropagation Without Storing Activations](https://arxiv.org/abs/1707.04585)

[^Roy_2020]: Roy, Saffar, Vaswani, and Grangier (2020) [Efficient Content-Based Sparse Attention with Routing Transformers](https://arxiv.org/abs/2003.05997)

[^Wang_2020]: Wang et al. (2020) [Linformer: Self-Attention with Linear Complexity](https://arxiv.org/abs/2006.04768)

[^Peng_2021]: Peng et al. (2021) [Random Feature Attention](https://arxiv.org/abs/2103.02143)

[^Choromanski_2020]: Choromanski et al. (2020) [Rethinking Attention with Performers](https://arxiv.org/abs/2009.14794)

[^Rahimi_2007]: Rahimi and Recht (2007) [Random Features for Large-Scale Kernel Machines](https://papers.nips.cc/paper_files/paper/2007/hash/013a006f03dbc5392effeb8f18fda755-Abstract.html)


* https://people.idsia.ch/~juergen/artificial-curiosity-since-1990.html#sec9
### LLMs
* Language Models are Few-Shot Learners by Brown et. al, (Jul. 22, 2020) 
* LLaMA- Open and Efficient Foundation Language Models by Touvron et. al (Feb 27, 2023) 
* OpenAGI--When LLM Meets Domain Experts by Ge et. al (Apr 12, 2023) 
* Pre-train Prompt and Predict- A systematic survey of prompting methods in Natural Language Processing by Liu et. al (Jul 28, 2021) - A survey of different prompting techniques.
* Chain-Of-Thought Prompting Elicits Reasoning in Large Language Models by Wei et. al (Jan 10, 2023)

[^Graves_2016]: Graves (2016) [Adaptive Computation Time for Recurrent Neural Networks](https://arxiv.org/abs/1603.08983)

[^Fein-Ashley]: Fein-Ashley (2025) [The FFT Strikes Back: An Efficient Alternative to Self-Attention](https://arxiv.org/abs/2502.18394)

[^Shen_2025]: Shen et al. (2025) [Efficient Reasoning with Hidden Thinking](https://arxiv.org/abs/2501.19201)
* [[Large Language Model#Variants|Pre-train, Prompt and Predict by Liu]]]

# Knowledge
* A **Moore Graph** is a graph with diameter $d$ and girth $2d+1$. 
* A **generalized polygon** is a [[Bipartite Graph|bipartite graph]] with diameter $d$ and girth $2d$. 


 
# Exercises



# Top
* [[Chain of Thought Prompting]]

* [[Numerical Methods]] 
	* ODEs
	* PDEs
* [Look more into Sparse Autoencoder](https://www.youtube.com/watch?v=9-Jl0dxWQs8)
* [Proportional Navigation](https://en.wikipedia.org/wiki/Proportional_navigation)

# Hold

* [^miyake_2024] shows the use of MARL for analyzing and predicting the evolution of social [[Network Science|networks]].  Each node represents a rational agent in an RL setting. 
	* The goal is to design explainable reward and policy functions. Each agent's policy is to add or remove edges or change their attributes. 
	* The NetEvolve system consists of three phases:
		* Learn the reward function for each node. 
			* The reward function consists of a linear combination of interpretable features and represents the desirability of the network to each node. 
			* The weights used in the reward function are learnt. 
			* *Optimization is done by assuming that the input time series evolution of the network is optimized*. 
		* Learn the policy for each node. The policy expresses the tendency to change attributes and edges. 
		* Predict future networks based on the multi-agent simulation using learned policies.

[^Miyake_2024]: Miyake et al. (2024) [NetEvolve: Social Network Forecasting using Multi-Agent Reinforcement Learning with Interpretable Features](https://dl.acm.org/doi/pdf/10.1145/3589334.3647982)


* [^Weil_2024]  introduces a decentralized approach to MARL using a [[Graph Neural Network|graph]]-based message passing algorithm to pass agent states to their neighbors.  
	* In this approach, agents form a communication network. Agents pass their local states to their neighbors in the network, and aggregate incoming messages to form a local observation of the entire network. 
	* This approach can be used with any RL training algorithm by performing the message passing step in each episode and augmenting agent observations with the local graph observation. 

[^Weil_2024] Wel et al. (2024) [Towards Generalizability of Multi-Agent Reinforcement Learning in Graphs with Recurrent Message Passing](https://arxiv.org/abs/2402.05027)