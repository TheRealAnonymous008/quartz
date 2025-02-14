* The DeepSeek suite as described in [^guo_2025], [^shao_2024] [^guo_2024]

# R1
* The primary goal of DeepSeek R1 is to *have LLMs develop reasoning capabilities without supervised data (i.e., SFT), instead using self-evolution via reinforcement learning*.


* The algorithm used is [[Trust Region Policies#GRPO|GRPO]] based on the DeepSeekMath model in [^shao_2024] .
* The initial iteration of the model is R1-Zero.
	* The reward model for the training signal is defined based on two rules:
	  
	  *Accuracy*: The response should be correct. 
	  *Format*: The model should properly put its thinking process between `<think> </think>`.
	* A template is used to guide the model to specific instructions. The template requires DeepSeek to output its reasoning then the answer. Other than this template, the model is free to reason and learn to reason. 
	* Using RL directly allows us to monitor the model's performance when it isn't using SFT. *All reasoning improvements are "naturally acquired" with only a little nudge* .
	  
	  [[Emergence|Emergent]] behaviors include reflection, exploration of new strategies, and the **Aha Moment** where the model allocates more thinking time evaluating its initial approach. 

* R1 is an improvement over R1-Zero in terms of readability of its chain of thought. The training process for R1 is detailed below:
	* *Cold Start* - the model is initialized with long CoT data. This allows the model to produce more readable outputs. The output format is then defined using the template 
	  ```
	  |special token|
	  <reasoning process>
	  |special token|
	  <summary>
	  ```
	  At the same time, this procedure boosts performance.
	* *Reasoning-oriented RL*  - The same RL process used in R1-Zero.  An additional reward is given to incentivize the model to stay consistent with its language (for alignment with human needs)
	* *Rejection Sampling / SFT* - To enhance the model output and its ability to perform general writing capabilities, we use SFT.
		* We expand the training dataset to include its own generated outputs (preprocessed for correctness and readability).
		* For non-reasoning related tasks, we use CoT data generated from DeepSeek-v3.
	* *RL for all scenarios* - we perform another pass of RL to improve AI alignment (do no harm; follow instructions) and to refine its reasoning. This refinement uses the same pipeline as R1-Zero for reasoning tasks, and RLHF for non-reasoning tasks.

* DeepSeek-R1 avoids introducing length bias during GPT-based evaluations (i.e., it can produce concise outputs).

* Additionally, the reasoning patterns of larger models *can be [[Knowledge Distillation|distilled]] to smaller models.*
	* Applying an additional RL step to refine the distilled models improves performance further.
	* Distilling more powerful models into smaller ones gives good performance compared to smaller models using the RL method described. 
	* There is still an intelligence gap between distilled models and large base models. 

* *Potential Future Directions*: The following are some setbacks encountered by the authors.
	* Use a Process Reward Model for solving reasoning tasks. This faces the following challenges.
		* Defining a fine-grain step in reasoning.
		* Determining whether the current intermediate reasoning step is correct.
		* Reward hacking.
	* Use [[Decision Time Planning#Monte Carlo Tree Search|Monte Carlo Tree Search]]  to enhance scalability. This faces the following challenges:
		* The search space for token generation is extremely large. 
		* Limiting the search space risks [[Pathologies of Deep Learning|getting stuck in local optima]].
		* Training a fine-grained value model for reasoning is difficult and hard to iteratively improve. 

# DeepSeek Math
* DeepSeeMath is a domain specific language model for mathematical reasoning. 
* It is trained on a specific corpus crawled based on math pages online (i.e., OpenWebMath). 
	* The crawler itself is equipped with a classifier [[Contrastive Learning|trained]] to distinguish from math and non-math pages to augment performance.
	* Results show (via pretraining DeepSeek-LLM) that the resulting DeepSeekMath Corpus is high quality, large in size compared to prior math datasets. 
		* Models trained on DeepSeekMath exhibit better performance than those trained on other existing models.
		* It is also multilingual compared to prior English-centric datasets.

* It is initialized from DeepSeek-Coder since it was found that coding models can aid in this task, particularly for program-aided mathematical reasoning but  also for tasks without tool use. 
* Supervised Fine Tuning was done via an [[Instruction Tuning|instruction tuning]] dataset covering problems from different fields and complexity levels, paired with solutions in CoT, PoT and reasoning format. 
	* Results show *ArXiv Papers seem ineffective in improving mathematical reasoning.*
	  
	  Though do note the following. The paper has not investigated
		* The effects of arXiv tokens on other tasks not evaluated.
		* The effects of arXiv tokens when combined with other types of data.
		* Whether arXiv tokens can benefit from larger models.

* For training via RL, it makes use of [[Trust Region Policies#GRPO|GRPO]]. 
	* RL enhances the model’s overall performance by rendering the output distribution more robust, in other words, it seems that *the improvement is attributed to boosting the correct response from TopK rather than the enhancement of fundamental capabilities.*
	* Thus, RL can be used to improve the reasoning of a model by learning preference alignment strategies. 

* Evaluation was done via:
	* Few-shot [[Chain of Thought Prompting|chain of thought prompting]] covering elementary to college-level math. 
	* Few-shot program-of-thought prompting with the evaluation taken from the execution result of the program.
	* Informal-to-formal proving -- generate a formal proof from an informal one and vice versa. 
	* Natural language understanding, reasoning, and coding.

* *Points of Improvements* as outlined by the authors' analysis
	* Naive nucleus sampling for sampling outputs. Can be improved using advanced sampling and determining exploration efficiency.
	* An implicit assumption that reward signals are reliable, even with increased task complexity.
	* For the reward model:
		* It could be more generalizable to handle out of distribution questions.
		* It could model uncertainty 
		* It could be more high quality and give more fine grained training signals.

![[DeepSeekMath Crawler.png]]
<figcaption> DeepSeekMath Crawler Pipeline. Image taken from Shao et al. (2024) </figcaption>

# DeepSeek Coder 
* DeepSeek Coder introduces open source models for coding and software development. 
* The models are trained on a large training corpus comprising 87 programming languages.
	* Public repositories created before February 2023 on GitHub were crawled and filtered for low quality code. Most data heavy files were removed. 
	* Dependencies between files are parsed and [[Sorting Algorithms|topologically sorted]] to ensure appropriate context. To preserve file information, we add file paths as comments as the beginning of each file.
	* To enhance performance further, we use a near-deduplication algorithm at the repository level.
	* The dataset is further filtered for low quality code. Code matching solutions to the test dataset is also removed


* Repository-level data construction is incorporated to boost cross-file code generation. 
* Training makes use of an initial pass of Next-Token Prediction followed by Fill-In-Middle training (trained on partitions of each sample into three blocks and rearranging them to be in PSM / Prefix-Suffix-Middle order). 
* The model supports long context windows using RoPE. 
* [[Instruction Tuning]] is also supported by finetuning on Alpaca.


[^Guo_2025]: Guo et al. (2025) [DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via Reinforcement Learning](https://arxiv.org/abs/2501.12948)

[^Shao_2024]: Shao et al. (2024) [DeepSeekMath: Pushing the Limits of Mathematical Reasoning in Open Language Models](https://arxiv.org/abs/2402.03300)

[^Guo_2024]:  Guo et al. (2024) [DeepSeek-Coder: When the Large Language Model Meets Programming -- The Rise of Code Intelligence](https://arxiv.org/abs/2401.14196)

# Links
* [[Large Language Model]]
* [[Reinforcement Learning]]