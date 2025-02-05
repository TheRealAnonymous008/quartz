# Top
* [[DeepSeek]]
* [[Chain of Thought Prompting]]

* [[Numerical Methods]] 
	* ODEs
	* PDEs
* [[Fuzzy Computation]] and Fuzzy Logic
* [Screaming Insects Algorithm](https://www.youtube.com/watch?v=Yu7sF9rcVJY)
* [Look more into Sparse Autoencoder](https://www.youtube.com/watch?v=9-Jl0dxWQs8)
* [Proportional Navigation](https://en.wikipedia.org/wiki/Proportional_navigation)


# Research Papers

* [^Kimenko_2021] discusses limitations for generic learning algorithms for pursuing adversarial goals in competitive environments
	* Let $p_i',p_j''$ be playing programs for a particular game. Define a [[Theory of Computation|Computational Algorithm]] $C$. such that 
	  $$
	  C_{ij}= C(p_i',p_j'') =\begin{cases}
	  +1 & p_i'\succ p_j'' & \text{player 1 wins} \\ 
	  0 & p_i'\sim p_j'' & \text{draw} \\
	  -1 & p_i'\prec p_j'' & \text{player 1 loses}
	  \end{cases}
	  $$
	  We treat $C$ itself as characterizing a [[Game Theory - Games|game]]. 
	  
	  We also assume that each playing program runs within a time limit, and the game only has a finite state. Thus, the set of possible playing programs is large but finite. 
	* Consider the Normal Form representation of the game given by the matrix whose entries are $C_{ij}$.  Each program then represents a [[Game Theory - Strategy|strategy]]. 
	* We can perform the analysis using a [[Turing Machine]]. One particular case to consider is when learning is allowed called **open source competition** . That is Player $1$ can learn Player $2$'s strategy $p_j''$ and vice versa via information exchange. 
	  
	  We do this as follows. Let $U\braket{M}[D_0]\to D_1$ be a universal Turing machine with header $M$ applied to input $D_0$ and produces output $D_1$. The learning algorithms can be defined as 
	  $$
	  \begin{split}
	  U\braket{L'}[C, L''] &\to p_i' \\ 
	  U\braket{L''}[C, L'] &\to p_j'' \\ 
	  \end{split}
	  $$
	  An algorithm $L'$ **wins** over $L''$ either by producing $L'[L'']\to p_i'(L'')\succ p_j'(L')$ where $L''[L']\to p_j''(L')$ or by producing $L'[L'']\to p_i'(L'')$ and the competing algorithm does not halt (i.e., winning requires the program to halt.)
	  
	  $L$' is a **universal winner** for game $C$ when it can defeat every opposing algorithm $L''$. 
	* (*[^Kimenko_2021]Thm. 1*): Any algorithm competing in an open source competition associated with any strongly intransitive game cannot be a universal winner.
	  
	  In fact ([^Kimenko_2021] *Thm 3*) provides the stronger statement: Any algorithm competing in an open source competition cannot be a universal winner.
		* *Proof*:  For Thm 1. A hypothetical universal winner $L_w$ halts so that $L_w[L'']\to p_i'$ . However, by strong intransitivity, take the program that runs $L_w$ first and then obtains $p_j''\succ p_i'$ which is guaranteed to exist. 
		  
		  For Thm. 3, we can show that $L_w$ cannot implement a  universal halting function so it cannot determine whether $L_h$ halts given data $D_h$. Hence $L''[L_w]$ that ignores $L_w$ and executes $L_h[D_h]$ is not defeated by $L_w[L']$. Hence, $L_w$ is not a universal winner.
	* Thus, there is a new strategy: *Refuse to halt while hiding any intention to halt*. 
	* This also implies *No learned algorithm can always win* and *Intransitivity adds complexity*. 

[^Kimenko_2021]: Kimenko, and Kimenko (2020) [On Limitations of Learning Algorithms in Competitive Environments](https://arxiv.org/abs/2011.12728)


* [^Ukorigho_2023] employs competitive learning for modeling physical [[System Science|systems]].
	* In particular,  each model in the agent system makes predictions in localized regimes within the dataset. This allows models to specialize on their own niche within the problem space. The models are extracted from the dataset.
	* This is done by introducing a new [[Loss Function|loss function]] that weighs each sample. Let $\alpha_{i,k}$ be the weight of the $i$-th observation for the $k$-th model. Then 
	  $$
	  \mathcal{L}_k = \frac{1}{S} \sum_{i=1}^S \alpha_{i,k}(y_i - \hat y_{i,k})^2
	  $$
	* The weights are calculated as follows
	  $$
	  \alpha_{i,k} = \frac{\exp(-\kappa(y_i-\hat{y}_{i,k})^2/c_i)}{\sum_{j=1}^Q \exp(-\kappa(y_j-\hat{y}_{j,k})^2/c_j)}
	  $$
	  Where $c_i$ is the squared error of the best model for an observation
	  $$
	  c_i = \min_{k\in Q} \set{(y_i-\hat{y}_{i,k})^2}
	  $$
	  And $\kappa$ determines the degree of separation between models (higher = more distinct). 
	* In this scheme, if a model performs better than others for an observation, that observation is assigned a weight of $1$ to that model alone and to $0$ to the others. *Models influence the loss landscape itself, carving out their own niches*
	* In practice, we use a smoothed version of the weight parameter computed by averaging the weights of its $N$ nearest neighbors. In particular in place of $\alpha_{i,k}$ we use 
	  $$
	  \begin{split}
	  \hat\alpha_{i,k} &= \alpha_{i,k} \overline{\alpha}_{i,k}^\gamma \\
	  \overline{\alpha}_{i,k} &= \frac{1}{N}\sum_{j\in\mathcal{G}} \alpha_{j,k}
	  \end{split}
	  $$
	  Where for a particular sample $\mathcal{G}$ is its $N$ closest neighbors. 
	* *Limitation*: We need too determine $Q$, the number of models to employ.
	* *Limitation*: Convergence to local minima.

[^Ukorigho_2023]: Ukorigho and Owoyele (2023) [A Competitive Learning Approach for Specialized Models: A Solution for Complex Physical Systems with Distinct Functional Regimes](https://arxiv.org/abs/2307.10496)


* [^Yang_2018] introduces **Bayesian Theory of Mind on Policy (Bayes-ToMoP)** which dynamically detects the strategy of an opponent. In particular, it detects unseen strategies and learns a best response. 
	* It addresses the drawbacks of ToM approaches -- that they are designed only for primitive strategies; and it does not adapt to unseen strategies. 
	* It also addresses the drawbacks of Bayesian Policy Reuse -- that they are designed for simple opponents with stationary strategies.
	* Bayes-ToMoP is a recursive algorithm. At order $0$, we assume a zero-order belief about the opponent's strategies, denoted $\beta^{(0)}(j)$ for the belief that the opponent adopts strategy $j$.
	   
	  Given utility $U$, We also have a performance model $P_{\text{self}}(U\mid j, \pi)$ which describes the probability of using a policy $\pi\in\Pi$ against $j$.  
	  
	  At order $1$, the belief that the opponent believes the agent will choose policy $\pi$. We incorporate $\beta^{0}(j)$ as well as a correction term to weigh in first-order prediction $\hat{j}$. This integration function is given as follows where $c_1$ is  a weighting term.
	  $$
	  \begin{split}
	  I(\beta^{0}, \hat{j}, c_1) (j) = \begin{cases}
	  (1-c_1)\beta^{(0)} (j) + c_1 & \text{if } j=\hat{j} \\ 
	  (1-c_1)\beta^{(0)} (j) & \text{otherwise} 
	  \end{cases}
	  \end{split}
	  $$
	  The first-order belief is then updated based on [[Bayesian Statistics|Bayes' Rule]] (see Lines 6 - 11) below.

	* To update the first-order confidence $c_1$. The idea is to *use game outcomes as a signal to determine if previous predictions are correct and adjust the first-order confidence according.* The rule is given below. Let $v_i$ be defined as the win-rate 
	  $$
	  v_i = \frac{1}{l}\sum_{i-l}^ir_{\text{self}}
	  $$
	  We also let $\lambda$ be the adjustment rate, and $\delta$ a threshold parameter. 
	  $$
	  c_1 = \begin{cases}
	  ((1-\lambda)c_1 + \lambda) F(v_i) & v_i \ge v_{i-1} \\ 
	  \left(\frac{lv_i}{l(v_i-\delta)}c_1\right) F(v_i) & \delta < v_i< v_{i-1} \\ 
	  \lambda F(v_i) & v_i \le \delta
	  \end{cases}
	  $$
	  Here $F(v_i)$ is an indicator function to control the direction of adjusting $c_1$.  Its value is adjusted based on its previous value $F'$
	  $$
	  F(v_i) = \begin{cases}
	  1 & (v_i\le \delta \wedge F'(v_i) = 0) \\ 
	0 & (v_i\le \delta \wedge F'(v_i)= 1)
	  \end{cases}
	  $$

	* We also allow for detecting strategies. Consider the win rate $v_i$ over the most recent $h$ episodes ($h$ is a hyperparameter). 
	  
	  The lowest win rate among the best-response policies can be seen as the upper bound for $\delta$. If $v_{ij}$ is the win-rate against policy $j$, then 
	  $$
	  \delta\le \min_{\pi\in \Pi} \max_{j\in \mathcal{J}} v ^{(\pi j)}
	  $$
	  If the win rate of a policy is lower than $\delta$, then that means all existing policies show poor performance against the current strategy. 
	  
	  When we detect a new strategy, we learn a new policy against it. 
	* ([^Yang_2018] *Thm 1* ) The strategy detection described is optimal. 


![[Bayes-ToMoP.png|500]]
<figcaption> Bayes-ToMoP Algorithm. Image taken from Yang et al. (2018)</figcaption>

[^Yang_2018]: Yang et al. (2018) [Towards Efficient Detection and Optimal Response against Sophisticated Opponents](https://arxiv.org/abs/1809.04240)


* [^tessera_2024] introduces **HyperMARL** which uses [[Hypernetwork|hypernetworks]] to balance between Full Parameter Sharing (efficiency) and Independent Learning (specialization). 
	* A **specialized environment** is one where
		* The optimal joint policy $\pi^\ast$ consists of two distinct agent policies.
		* Any permutation of the policies in $\pi^\ast$ results an expected return that is weakly lower or equivalent to the original.   
		  $$
		  \mathbb{E}_{\tau \sim \pi^\sigma} [G(\tau)] \le \mathbb{E}_{\tau\sim \pi^\ast}[G(\tau)]
		  $$
	* A joint policy is **diverse** based on the **System Neural Diversity** defined as 
	  $$
	  \text{SND} \left(\set{\pi_i}\right) = \frac{2}{n(n-1) |\mathcal{O}|} \sum_i \sum_{j>i} \sum_{o\in \mathcal{O}} D(\pi_i(o), \pi_j(o))
	  $$
	  Where $D$ is a distance function (in this case, the [[Information Theory|Jensen-Shannon Divergence]]). 

	* The hypernetwork $h$ takes context vector $e$ and outputs the weights for both the policy and critical networks. That is 
	  $$
	  \begin{split}
	  \theta_i &= h_\psi^\pi (e_i) \\
	  \phi_i &= h_\psi ^V(e_i)
	  \end{split}
	  $$
	  The policy gradient is given with respect to the hypernetwork parameters $\psi$. 
	  $$
	  \nabla_\psi J(\psi) = \mathbb{E}_{\tau \sim \pi_{\theta^i}} \left[\sum_t \sum_i A(o_i^t,a_i^t) \nabla_{\theta_i} \log\pi_{\theta_i} \left(a_t^t\mid o_i^t\right) \cdot \nabla_\psi h_\psi^\pi(e_i) \right]
	  $$
	  *We can decouple the two gradients during training*. 
	  Where $A$ is the advantage
		* The context vectors are learned [[Representation Learning|embeddings]] for each agent.
	* HyperMARL scales efficiently, is robust against variations in architecture, initialization, and conditioning, and maintains performance compared to the two extreme methods.
	* *Limitations*: Uses naive implementation of hypernetworks and can be further optimized.

![[HyperMARL.png|300]]
<figcaption> HyperMARL. Image taken from Tessera, Rahman, and Albrecht (2024) </figcaption>

[^Tessera_2024]: Tessera, Rahman and Albrecht (2024) [HyperMARL: Adaptive Hypernetworks for Multi-Agent RL](https://arxiv.org/abs/2412.04233)


* [^Li_2022] ***UNFINISHED**

[^Li_2022]: Li (2022) [The impact of moving expenses on social segregation: a simulation with RL and ABM](https://arxiv.org/abs/2211.12475)




* [^Weil_2024]  introduces a decentralized approach to MARL using a [[Graph Neural Network|graph]]-based message passing algorithm to pass agent states to their neighbors.  
	* In this approach, agents form a communication network. Agents pass their local states to their neighbors in the network, and aggregate incoming messages to form a local observation of the entire network. 
	* This approach can be used with any RL training algorithm by performing the message passing step in each episode and augmenting agent observations with the local graph observation. 

[^Weil_2024] Wel et al. (2024) [Towards Generalizability of Multi-Agent Reinforcement Learning in Graphs with Recurrent Message Passing](https://arxiv.org/abs/2402.05027)

* Some approaches in RL for learning strategy:
	* [[Transfer Learning]]
	* [[Imitation Learning]]
	* [[Competitive MARL|Competitive Learning]] - learn how to counter an opponent's actions in a simple game. 
	* Continual Learning - the model constantly adapts. 


# File
* [Demo and Writeup for the AI of a Tactical Top Down Shooter](https://www.gamedev.net/blogs/entry/2267533-close-quarters-development-realistic-combat-ai-part-i/)
* [Final Fantasy VII - Game AI Writeup](https://gamefaqs.gamespot.com/ps/197341-final-fantasy-vii/faqs/31903)
* [Predictive Aiming](https://yal.cc/simplest-possible-predictive-aiming/)
* [Introversion Games - Subversion](https://www.youtube.com/watch?v=1giu6sMnAxY)

# Paper Queue
* [Program of Thoughts Prompting: Disentangling Computation from Reasoning for Numerical Reasoning Tasks](https://arxiv.org/abs/2211.12588)

* [^lyu_2023] provides a theoretical and empirical analysis of the use of Centralized Critics in CTDE.

[^Lyu_2023]: Lyu et al. (2023) [On Centralized Critics in Multi-Agent Reinforcement Learning](https://dl.acm.org/doi/pdf/10.1613/jair.1.14386) 

* [^Kim_2023]   introduces a new mutual information framework for MARL. This leads to the development of an algorithm called **Variational Maximum Mutual Information, Multi-Agent Actor Critic** which allows agents to coordinate simultaneous actions without latency. 

[^Kim_2023]: Kim, Jung, Cho, Sung (2020) [A Maximum Mutual Information Framework for Multi-Agent Reinforcement Learning](https://arxiv.org/pdf/2006.02732)

* Branching Reinforcement Learning by Du, and Chen (Jun 15, 2022) 
* Vinyals et al. (2019) [Grandmaster level in StarCraft II using multi-agent reinforcement learning](https://www.seas.upenn.edu/~cis520/papers/RL_for_starcraft.pdf) 
	* Linked in [[Self Play]]
* Wu et al. (2017) [Scalable trust-region method for deep reinforcement learning using Kronecker-factored approximation](https://arxiv.org/pdf/1708.05144.pdf)
	* Linked in [[Trust Region Policies]]
* [Ecoclimates -- Climate-Response Modeling of Vegetation by Palubicki et al. (2022)](https://storage.googleapis.com/pirk.io/papers/Palubicki.etal-2022-Ecoclimates.pdf)
* Ma et al. (2024) [Foundation Methods for Music -- A survey](https://arxiv.org/pdf/2408.14340v2)
* [Human-level play in the game of Diplomacy](https://noambrown.github.io/papers/22-Science-Diplomacy-TR.pdf)

* All these papers from [[Large Language Model]]
	* TransferTransfo -- A [[Transfer Learning|Transfer Learning]] Approach for Neural Network based Conversational Agents by Wolf, Sanh, Chaumond, and Delangue (Feb 4, 2019)
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
* All these papers from Prompt Engineering
	* Commonsense Knowledge Mining from Pretrained Models by Feldman, Davison and Rush (2019) 
	* ⭐ Prefix Tuning -- Optimizing Continuous Prompts for Generation by Li and Liang (Jan 1, 2021)
	* GPT Understands Too by Liu et. al (Mar 18, 2021) 
	* Calibrate Before Use -- Improving Few-Shot Performance of Language Models by Zhao et. al (Jun 10, 2021)
	*  ⭐Pre-train Prompt and Predict- A systematic survey of prompting methods in Natural Language Processing by Liu et. al (Jul 28, 2021) - A survey of different prompting techniques.
	* KnowPrompt -- Knowledge-aware Prompt-tuning with Synergistic Optimization for Relation Extraction by Zhang et. al (Jan 23, 2022)
	* P-Tuning v2 - Prompt Tuning can be comparable to Fine-tuning Universally Across Scales and Tasks by Liu et. al (Mar 20, 2022)
	* ⭐ Chain-Of-Thought Prompting Elicits Reasoning in Large Language Models by Wei et. al (Jan 10, 2023)
	* Complexity-Based Prompting for Multi-Step Reasoning by Fu et. al (Jan 30, 2023)

# Bookstops
* [[Rigid Body Simulation]] - Nonpenetration constraints
* [[Graph Theoretic Approaches for Swarms]] - Resume Ch. 4
* [[Code Complete by McConnell]] - Resume Ch. 10
* [[Philosophy]] - read through [[A New History of Western Philosophy  By Anthony Kenny]] 
* [[Factory Physics]] - Workforce Planning.
* [[Virtues and their Vices by Kevin and Craig]]  -Cardinal Virtues, Intellectual Virtues, Theological Virtues
* [[Linear and Nonlinear Programming by Luenberger and Ye]] - Resume Ch. 5
* [[Drawing on the Right Side of the Brain by Edwards]] - Resume Ch. 8
* [[Ordinary Differential Equations by Arnold]] - Ch. 6 (but restart all of Part 1) with better math background

# Backlogs
* Note, some entries in [[Trivia]] are also interesting.

* Forms of Government

* [[Theory of Computation]]
	* Algorithmic Information Theory
* Japanese Mythology
* [[Graph Neural Network]] - GNNs
* Combinatorial Optimization
* Ballistics
* [HEMA](https://wiktenauer.com/wiki/Main_Page)
* Extreme Performance Artists. Prompted by [this](https://www.youtube.com/watch?v=GrBZuCQAPAw) 
* [Dramaturgy](https://en.wikipedia.org/wiki/Dramaturgy_(sociology))
* [Von Neumann Morgenstern Utility Theorem](https://en.wikipedia.org/wiki/Von_Neumann–Morgenstern_utility_theorem)
* [Petri Nets](https://en.wikipedia.org/wiki/Petri_net#:~:text=A%20Petri%20net%2C%20also%20known,of%20elements%3A%20places%20and%20transitions.)
* [Hopfield Networks](https://www.youtube.com/watch?v=1WPJdAW-sFo&list=WL&index=15)
* General Method of Moments / Simulated Method of Moments
* [AlphaFold](https://en.wikipedia.org/wiki/AlphaFold)
* [Socionics](https://en.wikipedia.org/wiki/Socionics)
* Chess Openings
* [Sound Design](https://www.youtube.com/watch?v=_J56n496u6k)
* [Johnson-Lindenstrauss Lemma](https://en.wikipedia.org/wiki/Johnson–Lindenstrauss_lemma)
* Neuro Evolution of Augmented Topologies and similar algorithms
	* [Evolutionary Acquisition of Neural Topologies](https://en.wikipedia.org/wiki/Evolutionary_acquisition_of_neural_topologies) 
	* [Compositional Pattern Producing Network](https://en.wikipedia.org/wiki/Compositional_pattern-producing_network)
	* [NEAT Particles](https://en.wikipedia.org/wiki/NEAT_Particles)
* Lanczos Algorithm (cited in [[Graph Neural Network#Lanczos Network|Lanczos Networks]])
* [Some interesting things to explore further](https://www.youtube.com/watch?v=-uIwboK4nwE) - PSLQ, Sinkhorn Limits, Kruithoff Limits
	* https://en.wikipedia.org/wiki/Iterative_proportional_fitting 
* [Combinatorial Maps](https://en.wikipedia.org/wiki/Combinatorial_map)
* [Surface Nets](https://bonsairobo.medium.com/smooth-voxel-mapping-a-technical-deep-dive-on-real-time-surface-nets-and-texturing-ef06d0f8ca14)
* [Halton Sequences](https://en.wikipedia.org/wiki/Halton_sequence)
* Bayesian Policy Reuse.
* Theory of Mind
* [Birch and Swinnerton-Dyver Conjecture](https://en.wikipedia.org/wiki/Birch_and_Swinnerton-Dyer_conjecture) 

* Vexillology and Heraldry 
* Sewing / Tailoring
* [F Divergence](https://en.wikipedia.org/wiki/F-divergence)
	* All $f$-divergences with differentiable $f$ look like KL divergence up to second order when $q$ close to $p$. Specifically
	  $$
	  D_f(P_0, p_\theta) = \frac{f''(1)}{2}\theta^T F\theta + O(\theta^3)
	  $$
	  Where $F$ is the Fisher Information matrix for $p_\theta$ calculated at $p_\theta = p_0$.
* [Bergman Divergence](https://en.wikipedia.org/wiki/Bregman_divergence) and in general Information Geometry
* [Haruhi Theorem and Superpermutations](https://en.wikipedia.org/wiki/Superpermutation)