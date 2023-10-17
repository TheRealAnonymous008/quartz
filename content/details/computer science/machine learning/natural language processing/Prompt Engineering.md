[Prompt Engineering](https://en.wikipedia.org/wiki/Prompt_engineering)
# Techniques for Prompting
* These techniques exist because *not all prompts lead to the same accuracy*.
* The best way to use LLMs is not to craft perfect prompts, but to *use LLMs interactively*, allowing it to modify its output.
* The trick is to *give the system context and constraints*. This introduces specificity in the response. 
	* Give the system a *role*. Tell the system "who" it is.
	* Add constraints to *writing style* such as by having it phrase it in a specific way or avoid repeating itself.
	* *Provide data* as additional context. This can be used for summarization tasks as well.
* *Think about prompting as programming in English*. Give the AI instructions.
	* Use **Chain of Thought Prompting** where the AI is given an example of how it is to reason before making the request.
* Some fun things to ask the AI:
	* To make any assumptions it needs.
	* To remove practical constraints.
	* To provide sources for responses.
	* To state how to do something step-by-step.
	* Tell a developer how to use its generated code.
	* To write a draft or provide an example.
* *Prompt Engineering appears to be a product of scale*.
# Papers
* Commonsense Knowledge Mining from Pretrained Models by Feldman, Davison and Rush (2019) 

* ⭐ Prefix Tuning -- Optimizing Continuous Prompts for Generation by Li and Liang (Jan 1, 2021)

* GPT Understands Too by Liu et. al (Mar 18, 2021) 

* Calibrate Before Use -- Improving Few-Shot Performance of Language Models by Zhao et. al (Jun 10, 2021)

*  ⭐Pre-train Prompt and Predict- A systematic survey of prompting methods in Natural Language Processing by Liu et. al (Jul 28, 2021) - A survey of different prompting techniques.

* KnowPrompt -- Knowledge-aware Prompt-tuning with Synergistic Optimization for Relation Extraction by Zhang et. al (Jan 23, 2022)

* P-Tuning v2 - Prompt Tuning can be comparable to Fine-tuning Universally Across Scales and Tasks by Liu et. al (Mar 20, 2022)

* ⭐ Chain-Of-Thought Prompting Elicits Reasoning in Large Language Models by Wei et. al (Jan 10, 2023)

* Complexity-Based Prompting for Multi-Step Reasoning by Fu et. al (Jan 30, 2023)
# Links
* [[Large Language Models]] - for a discussion on LLMs in general. 

* [Guide for Prompting AI (for what it's worth)](https://www.oneusefulthing.org/p/a-guide-to-prompting-ai-for-what) 
* [Prompt Engineering](https://lilianweng.github.io/posts/2023-03-15-prompt-engineering/) -  more on prompt engineering.
* [Prompt Engineering Guide](https://github.com/dair-ai/Prompt-Engineering-Guide) - additional resources for Prompt Engineering