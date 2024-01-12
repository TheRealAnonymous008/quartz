* Mathematical Reasoning is like [[Reinforcement Learning]], except we have an infinite search space due to an infinite number of axioms applicable. It is also non-adversarial and "binary" in the sense that proofs are either valid or invalid (unlike games which can be assessed on a continuum).
# Papers 
*  [^Jiang_2023] Introduces Draft, Sketch, Proof (DSP) an approach for mathematical proving which involves using LLMs to translate informal proofs into a formal proof using autoformalization to create a high-level proof sketch and an automated prover to fill in any gaps.

	[^Jiang_2023]: Jiang, A. Q., et. al (2023). [Draft, Sketch, and Prove: Guiding Formal Theorem Provers with Informal Proofs](http://arxiv.org/abs/2210.12283 )

*  [^Lu_2023] Survey for Mathematical Reasoning through Deep Learning.

	[^Lu_2023]: Lu, P., et. al (2023). [A Survey of Deep Learning for Mathematical Reasoning](http://arxiv.org/abs/2212.10535)

*  [^Lample_2022] Introduces **Evariste** which makes use of a MCTS-like pipeline to generate and prove theorems. This pipeline is called HyperTree Proof Search. 
	* The model makes use of two encoder-decoder transformer models (one for policy and one for evaluation) trained via online learning, which the paper demonstrates as being effective over expert iteration.
	
	[^Lample_2022]: Lample, G., et. al (2022). [HyperTree Proof Search for Neural Theorem Proving](http://arxiv.org/abs/2205.11491 )

* [^Polu_2022] Explores the use of Expert Iteration and curriculum learning. The goal is to have models close opened proofs much quicker by incentivizing shorter proofs. 

	[^Polu_2022]: Polu, S., et. al (2022). [Formal Mathematics Statement Curriculum Learning](http://arxiv.org/abs/2202.01344 )

* [^Kalyan_2021]  Introduces the Fermi Problem challenge which provides open-ended problems that require life experience, long chains of thoughts, creativity, and numerical estimation skills to solve. 

	[^Kalyan_2021]: Kalyan, A., et. al (2021). [How Much Coffee Was Consumed During EMNLP 2019? Fermi Problems: A New Reasoning Challenge for AI](http://arxiv.org/abs/2110.14207) 

* [^Welleck_2021] Introduces **NATURALPROOFS**, a multi-domain dataset for bridging the gap between formal mathematical reasoning and informal reasoning through proofs worded in natural language. It also establishes benchmarks for the task of retrieving and generating references to be used in a proof. 

	[^Welleck_2021]: Welleck, S., et al. (2021). [NaturalProofs: Mathematical Theorem Proving in Natural Language](http://arxiv.org/abs/2104.01112)

* [^Polu_2020]  Introduces the $\text{GPT-}f$ automated prover and proof assistant which makes use of a pre-trained transformer model and a proof verification system to generate valid proofs. It also demonstrates self-sufficiency as it can expand its training set with proofs it discovers during each iteration.

	[^Polu_2020]: Polu, S., & Sutskever, I. (2020). [Generative Language Modeling for Automated Theorem Proving](http://arxiv.org/abs/2009.03393)
# Links 
* [[Decision Time Planning]]