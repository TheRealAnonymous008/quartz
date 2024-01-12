# Research 
* [^Oguntola__2023] Test 
	[^Oguntola_2023]: Oguntola et al. (2023) [Theory of Mind as Intrinsic Motivation for Multi-Agent Reinforcement Learning](https://arxiv.org/pdf/2307.01158.pdf)

* [^Swamy_2020] Characterizes the performance of model based and model-free learning in the context of Human-Robot Interactions. 
	* *Rationale*: There is debate for whether or not to prefer model-based and model-free learning, especially in the context of HRI. 
	* The paper examines an HRI system where the robot optimizes a reward function in the presence of a human who optimizes theirs in response to the robots actions.
	* *Key Findings*: 
		* If we had a perfect theory of mind, we’d *reduce the sample complexity of learning* compared to black-box model-based learning, and we could learn off of off-policy data.
		* *It is possible for black box model based approaches to fail* to improve even with a lot of data, unless that data comes from the right distribution
		* *Theory of Mind is robust* to the wrong assumptions, and even when the human deviates but this was due to ToM's wrong predictions. 
		* *Theory of Mind is easily transferrable*. 
		* Based on the researchers experiments, *model-based methods do not sufficiently explore* the search space and are stuck in low reward local minima. 
		* *If we have a good model, learning its parameters leads to good performance compared to learning from scratch*.
	* *Limitations*: The "human" aspect of the simulated HRI system may not be representative of real life.  The results were also only derived from one particular task. 
	* *The robot figures out the human's reward function via inverse RL*. 
		* *Off policy approach:* Collect a training dataset of human interactions and fit  a neural network to estimate the human's cost function.  This ignores the fact that the predictive model influences the behavior of the human. 
		* *On policy approach*: Data collection and training are done iteratively.
		* *Idealized Exploration approach* : Aims to address exploration issues in both off-policy and on-policy approaches. Data is collected on the optimal policy. This data is mixed with the on-policy data.
		* *Model free learning approach*: Use [[Policy Gradient Methods]] to train the model.

	[^Swamy_2020]: Swamy et al. (2020) [On the Utility of Model Learning in HRI](https://arxiv.org/pdf/1901.01291.pdf)

# Links 
* [[Reinforcement Learning]]