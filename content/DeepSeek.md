* DeepSeek as described in [^guo_2025], [^shao_2024]

# R1
* The primary goal of DeepSeek R1 is to *have LLMs develop reasoning capabilities without supervised data (i.e., SFT), instead using self-evolution via reinforcement learning*.
* Additionally, the reasoning patterns of larger models *can be [[Knowledge Distillation|distilled]] to smaller models.*

* The algorithm used is [[Trust Region Policies#GRPO|GRPO]] based on the DeepSeekMath model in [^shao_2024] .

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


[^Guo_2025]: Guo et al. (2025) [DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via Reinforcement Learning]

[^Shao_2024]: Shao et al. (2024) [DeepSeekMath: Pushing the Limits of Mathematical Reasoning in Open Language Models](https://arxiv.org/abs/2402.03300)


# Links
* [[Large Language Model]]
* [[Reinforcement Learning]]