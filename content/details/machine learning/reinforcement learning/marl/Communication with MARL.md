# RIAL / DIAL
* [^Foerseter_2016] introduces **Reinforced Inter-Agent Learning (RIAL)** and **Differentiable Inter-Agent Learning (DIAL)** to facilitate learning communication strategies in cooperative MARL settings.
	* We assume a Dec-POMDP in the CTDE setting. In addition to environment action $u\in U$, agents also have a communication action $m\in M$. 
	* **RIAL** uses a [[Off Policy Prediction and Control with Approximation|DQN ]] with a [[Recurrent Neural Network|RNN]] for partial observability.
		* Here, we use [[MARL Deep Learning#Independent Learning|Independent Learning]] for action and communication selection. We use two networks for environment and communication actions respectively. This way, we do not need $|U||M|$ model outputs. 
		* For performance, we train the model with the following in mind:
			* We disable experience replay since the environment is not stationary. 
			* To account for partial observability, feed the actions taken by each agent as inputs to the next time step.
		* This can be extended to the Parameter Sharing case. 
	* **DIAL** extends RIAL by allowing it to also be end-to-end trainable between agents by passing real-valued messages (gradients) to be shared between agents during centralized learning.
		* *Rationale*: RIAL does not allow agents to give feedback on communication actions. 
		* During centralized learning, communication actions are replaced with direct connections between the output of one agent’s network and the input of another’s
		* The **C-Net** network used here outputs two values -- the $Q$-values for environment actions and $m_t^a$, the real-valued message to other agents that bypasses the action selector and is processed by the discretize/regularize unit.
			* During training, the DRU regularizes the output.
			  $$
			  \text{DRU}(m_t^a) = \text{Logistic}(\mathcal{N}(m_t^a, \sigma))
			  $$
			  where $\sigma$ is noise added to the channel
			* During execution, the DRU discretizes the output. 
			  $$
			  \text{DRU}(m_t^a) = \mathbb{1}[m_t^a > 0]
			  $$
		* In DIAL, the gradient term for $m$ is the backpropagated error from the recipient of the message. 
	* In DIAL, we find that *the presence of noise forces messages to be made more distinct*
![[RIAL and DIAL.png]]
<figcaption> RIAL and DIAL. Image taken from Foerster, Assael, de Freitas and Whiteson (2016)</figcaption>


[^Foerseter_2016]: Foerster, Assael, de Freitas, and Whiteson (2016) [Learning to Communicate with Deep Multi-Agent Reinforcement Learning](https://arxiv.org/abs/1605.06676)

# Other
* [^Muller_2024] proposes **ClusterComm**, a fully decentralized MARL framework for communication in collaborative tasks.
	* Discrete messages are created by clustering the output of the policy layer via $K$-means (more specifically, Lloyd's algorithm).
	* *It is based on how humans learned to communicate*. Thus, it does not rely on parameter sharing or differentiable communication. *All agents act independently and training is done fully decentralized*.
	* The rationale behind clustering is that it allows a compact representation of messages. 
	* All policies are based on the current observation and the messages $m^{t-1}_{-i}$ sent by all other agents.
		* $\phi_o^{(i)}$ is an observation encoder that outputs a representation for $o_i^t$. 
		* $\phi_m^{(i)}$ takes the concatenation of $m^{t-1}_{-i}$ and produces a message representation.
		* $\phi_a^{(i)}$ receives the concatenation of representation messages and the local observation too compute the action. 
		* The output of $\phi_o^{(i)}(o_i^t)$ is discretized via Mini-batch [[Clustering|K-means clustering]].  


![[ClusterComm.png|500]]
<figcaption> ClusterComm. Image taken from Muller et al. (2024) </figcaption>


[^Muller_2024]: Muller et al. (2024) [ClusterComm: Discrete Communication in Decentralized MARL using Internal Representation Clustering](https://arxiv.org/abs/2401.03504)


* [^bettini_2023] proposes a [[Graph Neural Network|GNN]] based approach called **[[Heterogeneous MARL|Heterogeneous]] GNN PPO (HetGPPO)** which enables both inter-agent communication and learning in Dec-POMDP environments.
	* *Motivation*: Prior methods address heterogeneity without considering the use of communication to mitigate the partial observability in a Dec-POMDP (i.e., [[Centralized Training Decentralized Execution|CTDE]] relaxes this constraint for the critic during training). Relaxing the assumption to the case of homogeneous agents prevents agents from using heterogeneous actions to achieve their objectives.
	* We can extend the regular [[MARL from a Game Theoretic Perspective|Game theoretic formulation]] by introducing a [[Graph Theoretic Approaches for Swarms|communication graph]] for each agent.
	  
	  At each time step, the observation $o_i^t$ is communicated to an agent in the neighborhood $N_i^t$. 
	  
	  The goal is still the same, however, to learn policies for each agent .
	* The model allows for **behavioral typing** -- where environmental conditions nudge agents to behave in particular ways. 
	* The proposed solution is both performant (compared to Homogeneous parameter sharing) and resilient (i.e., even with observation noise, the agents perform well.)

![[GPPO.png]]
<figcaption> HETGPPO. Image taken from Bettini, Shankar, and Porok (2023) </figcaption>

[^Bettini_2023]: Bettini, Shankar, and Prorok (2023) [Heterogeneous Multi-Robot Reinforcement Learning](https://arxiv.org/pdf/2301.07137)



* [^Bokade_2023] proposes a communication-based MARL framework for Traffic Signal Control. Agents learn what to communicate and to whom in a decentralized manner. 
	* Agents learn to compress observations and action intentions into a message. 
	* The proposed model called **QRC-TSC** improves upon DIAL by: 
		* Using variational inference to maximize [[Information Theory|mutual information]] between sent messages (and the communication action), and the recipient's action.
		* Introduce an entropy regularization term for communication policies to explore the communication action space.
		* Make communication policies differentiable .
	* Let $i$ and $j$ be sender and recipient respectively, $m_{ij}$ the message and $c_{ij}$ the corresponding communication action.
	  
	  $i$ generates a shared latent message distribution from which we sample $m_i$.
	* $c_{ij}$ acts as a mask over messages during execution. It uses the Gumbel-Sigmoid approximation defined as follows. Let $g_l,g_m\sim\text{Gumbel}(0,1)$ and $\lambda$ the temperature parameter
	  $$
	  \sigma(\alpha_l) = \text{sigmoid}\left(\frac{\alpha_i+g_l-g_m}{\lambda}\right)
	  $$
	  The objective  to learn communication $J_c(\theta_c)$ is to maximize the mutual information between the sender's message and the recipient's policy given as 
	  $$
	  I_{\theta_c} (\pi_j(\cdot \mid \tau_j) ; \hat{m}_{ij} \mid \tau_j, \hat{m}_{(-i)j})
	  $$
	  The reward is then formulated as maximizing mutual information while encouraging exploration of policies provided as follows. 
	  
	  Let $\mathcal{D}$ be the replay memory, $\tau\in\mathcal{D}$ a joint local action-observation history and $\text{CE}$ be the cross entropy.  Messages are modeled as a joint distribution $p(m_{ij},c_{ij}) = p(m_{ij}\mid \tau_{ij}) \cdot p(c_{ij}\mid\tau_{ij})$. Posterior estimates are also given by $q_{\theta_r}(\cdot\mid\tau_j,\hat{m}_j^{in})$
	  $$
	  \begin{split}
	  \mathcal{L}_C (\theta_r,\theta_c)  &= \mathbb{E}_{\tau\sim\mathcal D, m_{ij}^{in},c_{ij}^{in}\sim f_c(\tau\mid\theta_c)}\left[ \text{CE}(\pi_j(\cdot \mid \tau_j, \hat{m}_j^{in})\|  q_{\theta_r}(\cdot \mid\tau_j,\hat{m}_j^{in})\right] \\
	  &= \beta_m D_{\text{KL}}(p(m_{ij}\mid\tau_i)\|q_{\theta_r}(m_{ij}\mid \tau_i)) \\ 
	  &+ \beta_c D_{\text{KL}}(p(c_{ij}\mid \tau_i)\| q_{\theta_r}(c_{ij}\mid \tau_i))
	  \end{split}
	  $$



![[QRC-TSC.png]]
<figcaption> QRC-TSC framework. Image taken from Bokade, Jin, Amato (2023) </figcaption>


[^Bokade_2023]: Bokade, Jin, Amato (2023) [Multi-Agent Reinforcement Learning Based on Representational Communication for Large-Scale Traffic Signal Control](https://arxiv.org/abs/2310.02435)

* [^Vanneste_2021] examines communication learning in a mixed cooperative-competitive, partially-observable multi-agent setting where goals are shared between teams and are competitive across teams. 
	* Communication is done via a C-Net which takes in observations and outputs a vector message..
	* An A-Net then uses the vector message and the observations in the environment to determine the next action.
	* Communication is learnt via Differentiable Inter-Agent Learning
	* *Limitation*: In scenarios where communication is shared across teams, performance will decline significantly
	* *Limitation*: Not tested for cases with a large number of agents.
[^Vanneste_2021]: Vaneste et al. (2021) [Mixed Cooperative-Competitive Communication Using Multi-Agent Reinforcement Learning](https://arxiv.org/abs/2110.15762) 


* [^Ding_2020] proposes **Individually Inferred Communication (I2C)** a MARL approach to learning a [[Bayesian Statistics|prior]] for agent-to-agent communication. The prior is learned via causal inference. 
	* Each agent is capable of exploiting its learned prior knowledge to *figure out which agent is relevant and influential* by just local observation (i.e., it does not broadcast messages).
	* Communication works as follows. A prior network $b_i$ takes $o_i$ and index information of agent $j$. It *outputs a belief on whether to communicate with $j$*.
	  
	  Agent $i$ then sends a request to $j$, which then responds with $m_j$. 
	  
	  All received messages for agent $i$ are fed to the encoder $e_i$ to produce the encoded message $c_i$. We learn the policy $\pi_i(a_i\mid c_i,o_i)$.
	* Agents are more likely to communicate to agents which have more influence. The influence of agent $j$ on $i$ is measured via the causal effect $\mathcal{I}_i^j$ defined as follows
	  $$
	  \mathcal I_i^j =\text{KL} (P(a_i\mid a_{-i}, o) \ \| \ P(a_i\mid a_{-ij},o))
	  $$
	  Where $o$ is the joint observation and $a_{-ij}$ is the joint action of all agents other than $i$ and $j$. 
	  
	  The respective distributions are then calculated as follows:
	  $$
	  P(a_i\mid a_{-i}, o) = \frac{\exp(\lambda Q(a_i,a_{-i},o))}{\sum_{a_i'} \exp(\lambda Q(a_i',a_{-i},o))}
	  $$
	  Where $\lambda \in \mathbb{R}^+$ is a temperature parameter. 
	  
	  We also calculate $P(a_i\mid a_{-ij},o)$ as a marginal distribution of $P(a_i,a_j\mid a_{-ij},o)$ 
	  $$
	  P(a_i\mid a_{-i}, o) = \sum_{a_j}\frac{\exp(\lambda Q(a_i, a_j, a_{-ij},o))}{\sum_{a_i', a_j'} \exp(\lambda Q(a_i', a_j' ,a_{-ij},o))}
	  $$
	* The belief network learns the causal effect under the current state. More specifically, it learns using the dataset $\set{(o_i,d_i), \mathcal{I}_i^j}$ during training.
	* We also introduce **correlation regularization** to help the agent correlate other agent's observation to the actions. This is done using the term 
	  $$
	  \text{KL} (P(a_i\mid a_{-i}, o) \ \| \ \pi_i(a_i\mid e_i(o_j, o_k), o_i)
	  $$
	* Accounting for communication gives the following gradient 
	  $$
	  \begin{split}
	  \nabla_{\theta_{\pi_i}} \mathcal{J} (\theta_{\pi_i}) = \mathbb{E}_{o,a} \left[\mathbb{E} _{\pi_i} \left[\nabla_{\theta_{\pi_i}} \log \pi _i (a_i\mid c_i,o_i)  \ Q^\pi (a,o)\right]- \\ \eta \nabla_{\theta_{\pi_i}} \text{KL}(\pi_i(\cdot \mid c_i,o_i) \ \| \
	   P(\cdot \mid a_{-i},o))\right]
	   \end{split}
	  $$
	  The encoder network's gradient is given by
	  $$
	  \begin{split}
	  \nabla_{\theta_{e_i}}\mathcal{J}(\theta_{e_i}) = \mathbb{E}_{o,m,a} \left[\mathbb{E}_{\pi_i} \left[\nabla_{\theta_{e_i}} e_i(c_i\mid m_i) \nabla_{c_i}\log\pi(a_i\mid c_i, o_i) Q^\pi (a,o )\right] \\ 
	  -\eta \nabla_{\theta_{e_i}} e_i(c_i\mid m_i) \nabla_{c_i} \text{KL}(\pi_i(\cdot\mid c_i, o_i)\ \| \ P(\cdot \mid a_{-i},o ))
	  \right]
	  \end{split}
	  $$

![[I2C.png]]
<figcaption> I2C Framework. Image taken from Ding, Huang, Lu (2020) </figcaption>

[^Ding_2020]: Ding, Huang, Lu (2020) [Learning Individually Inferred Communication for Multi-Agent Cooperation](https://arxiv.org/abs/2006.06455)

