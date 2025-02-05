* **Prompt Engineering** pertains to the process of making instructions to produce the best output from a generative AI model. 
# Techniques for Prompting
* These techniques exist because *not all prompts lead to the same accuracy*.
* The best way to use LLMs is not to craft perfect prompts, but to *use LLMs interactively*, allowing it to modify its output.
* The trick is to *give the system context and constraints*. This introduces specificity in the response. 
	* Give the system a *role*. Tell the system "who" it is.
	* Add constraints to *writing style* such as by having it phrase it in a specific way or avoid repeating itself.
	* *Provide data* as additional context. This can be used for summarization tasks as well.
* *Think about prompting as programming in English*. Give the AI instructions.
	* Use **[[Chain of Thought Prompting|CoT Prompting]]** where the AI is given an example of how it is to reason before making the request.
* Some fun things to ask the AI:
	* To make any assumptions it needs.
	* To remove practical constraints.
	* To provide sources for responses.
	* To state how to do something step-by-step.
	* Tell a developer how to use its generated code.
	* To write a draft or provide an example.
* *Prompt Engineering appears to be a product of scale*.

# Links
* [[Large Language Model]] - for a discussion on LLMs in general. 

* [Guide for Prompting AI (for what it's worth)](https://www.oneusefulthing.org/p/a-guide-to-prompting-ai-for-what) 
* [Prompt Engineering](https://lilianweng.github.io/posts/2023-03-15-prompt-engineering/) -  more on prompt engineering.
* [Prompt Engineering Guide](https://github.com/dair-ai/Prompt-Engineering-Guide) - additional resources for Prompt Engineering