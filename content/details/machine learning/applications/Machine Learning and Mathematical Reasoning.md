* Mathematical Reasoning is like [[Reinforcement Learning]], except we have an infinite search space due to an infinite number of axioms applicable. It is also non-adversarial and "binary" in the sense that proofs are either valid or invalid (unlike games which can be assessed on a continuum).
# Papers
* *Generative Language Modeling for Automated Theorem Proving by Polu and Sutskever (Sep 7, 2020)* - introduces the $\text{GPT-}f$ automated prover and proof assistant which makes use of a pre-trained transformer model and a proof verification system to generate valid proofs. It also demonstrates self-sufficiency as it can expand its training set with proofs it discovers during each iteration.

* *NATURALPROOFS -- Mathematical Theorem Proving in Natural Language by Welleck et. al (Jun 7, 2021)* - introduces NATURALPROOFS, a multi-domain dataset for bridging the gap between formal mathematical reasoning and informal reasoning through proofs worded in natural language. It also establishes benchmarks for the task of retrieving and generating references to be used in a proof. 

* *How Much Coffee Was Consumed During EMNLP 2019-- Fermi Problems -- A New Reasoning Challenge for AI by Kalyan et. al (Dec 21, 2021)* - introduces the Fermi Problem challenge which provides open-ended problems that require life experience, long chains of thoughts, creativity, and numerical estimation skills to solve. 

* *Formal Mathematics Statement Curriculum Learning by Polu et. al (Feb 3, 2022)*-  explores the use of Expert Iteration and curriculum learning. The goal is to have models close opened proofs much quicker by incentivizing shorter proofs. 

* *HyperTree Proof Search for Neural Theorem Proving by Lample et. al (May 23, 2022)* - introduces Evariste which makes use of a MCTS-like pipeline to generate and prove theorems. This pipeline is called HyperTree Proof Search. The model makes use of two encoder-decoder transformer models (one for policy and one for evaluation) trained via online learning, which the paper demonstrates as being effective over expert iteration.

* *A Survey of Deep Learning for Mathematical Reasoning by Lu et. al. (Dec 20, 2022)* - survey for Mathematical Reasoning through Deep Learning.

* *Draft, Sketch, and Prove -- Guiding Formal Theorem Provers with Informal Proofs by Jiang et. al (Feb 20, 2023)* - introduces Draft, Sketch, Proof (DSP) an approach for mathematical proving which involves using LLMs to translate informal proofs into a formal proof using autoformalization to create a high-level proof sketch and an automated prover to fill in any gaps.
