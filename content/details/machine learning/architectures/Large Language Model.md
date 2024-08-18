* A **Large Language Model** is a machine learning model for language embedding and text generation and is characterized by the large number of parameters (on the order of hundreds of billions) and being trained on very large datasets (trillions of tokens)
* It is debatable whether or not LLMs actually learn to reason or whether they simply perform sophisticated pattern recognition.
# Key Facts
* LLMs are capable of being fine-tuned using only a small amount of data. This makes them more economical to use (ignoring the hardware costs)
* LLMs can be preconditioned to take or speak in certain roles or tuned for specific tasks.
* LLMS scale not only due to the amount of parameters but also on the amount of training data used.
* At scale, LLMs have a bunch of useful, emergent behavior such as:
	* In-context learning (Language Models are Few-Shot Learners by Brown et. al, (Jul. 22, 2020)|Brown et. al (2020)) and zero shot generalization to unseen tasks.
	* Instruction Tuning Amenability (Finetuned Language Models are Zero Shot Learners by Wei et al. (Feb 8, 2022)|Wei et al (2022))
	* Chinchilla scaling (i.e., increased performance with more tokens used on training) (Training Compute-Optimal Large Language Models by Hoffmann et. al (Mar 29, 2022)|Hoffman et. al (2022))
	* Chain of Thought Prompting (Chain-Of-Thought Prompting Elicits Reasoning in Large Language Models by Wei et. al (Jan 10, 2023)|Wei et al (2023))
* LLMs acquire the biases that are present in the training sets.

# Workflows
* [^w1] suggests that when building complex workflows we can get good results when we exploit the increasing context length of models (i.e., use many shot learning or very fine tuned prompts).
  
  This leads to a pipeline
	* Quick and simple prompts.
	* Iteratively flesh out the prompt based on where the output falls short. This may lead to **mega prompts**
	* Consider few-shot or many-shot learning, or iine tuning.
	* Breakdown the task into subtasks and use an agentic workflow

[^w1]: [OpenAI's Rules for Model Behavior](https://info.deeplearning.ai/openais-rules-for-model-behavior-better-brain-controlled-robots-alphafold-3-covers-all-biochemistry-ai-oasis-in-the-desert)

# Variants
* According to Pre-train Prompt and Predict- A systematic survey of prompting methods in Natural Language Processing by Liu et. al (Jul 28, 2021)|Liu et. al (2021): 
	* Left-to-right LMs are the most commonly used. They scan in the manner of an Encoder
	* Masked LMs are used for bidirectional contexts, similar to that of a decoder.
	* Prefix Language Models are left-to-right LMs that decodes an output conditioned on an input, which is encoded by the same model parameters but with a fully connected mask and possibly some corruption on the input.
	* Encoder-Decoder architectures mimic the full transformer.
# Topics
* [[Prompt Engineering]] - an increasingly important technique in using LLMs  which involves tuning the input prompts.
* [[Instruction Tuning]] - all about instruction tuning, a technique to get an NLP model to understand instructions.
# Papers
* TransferTransfo -- A Transfer Learning Approach for Neural Network based Conversational Agents by Wolf, Sanh, Chaumond, and Delangue (Feb 4, 2019)

* ⭐ BERT -- Pre-Training of Deep Bidirectional Transformer for Language Understanding by Devlin, Chang, Lee, and Toutanova (May 24, 2019) 

* Towards a Human-like Open-Domain Chatbot by Adiwardana et. al (Feb 27, 2020) 

* ⭐ Language Models are Few-Shot Learners by Brown et. al, (Jul. 22, 2020) 

* Dense Passage Retrieval for Open-Domain Question Answering by Karpukhin et. al (Sep 30, 2020) 

* TOD-BERT -- Pre-trained Natural Language Understanding for Task-Oriented Dialogue by Wu, Hoi, Socher, and Xiong (November 2020) 

* ⭐Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks by Lewis et. al., (2020) 

* ⭐ LaMDA- Language Models for Dialog Applications by Thoppilan et. al (Feb 10, 2022) 

* Language-Agnostic BERT Sentence Embedding by Feng et. al (Mar 8, 2022) 

* ⭐ Training Compute-Optimal Large Language Models by Hoffmann et. al (Mar 29, 2022)

* Generating Training Data with Language Models- Towards Zero-Shot Language Understanding by Meng, Huang, Zhang, Han (Oct 12, 2022)

* ⭐ LLaMA- Open and Efficient Foundation Language Models by Touvron et. al (Feb 27, 2023) 

* ⭐ OpenAGI--When LLM Meets Domain Experts by Ge et. al (Apr 12, 2023) 

* HuaTuo- Tuning LLaMA Model with Chinese Medical Knowledge by Wang et. al (Apr 14, 2023)
# Links
* [[Transformer Model]] - discusses one of the most common mechanisms used in LLMs.
* [[Language Model]] - a discussion on some of the earlier and smaller Language Models.

* [How To Generate](https://huggingface.co/blog/how-to-generate) - Hugging Face article on decoding strategies
* [Flowise](https://flowiseai.com) - A tool for working with LLMs.