* *Rationale*: Regular [[#Multi-Agent PGMs|PGM]]- based approaches are difficult because (1) it can be difficult to learn a centralized value function that scales with exponential action space; and (2) centralized value functions do not imply efficient decentralized execution.  [^valdec_1]
[^valdec]: One approach is to use the observation that not all agents interact with each other. 


* The goal is to decompose the following where $r$ is the common reward. 
  
  $$
  Q(h^t, z^t, a^t ; \theta) = \mathbb{E}\bigg[ \sum_{\tau=t}^\infty \gamma^{\tau-1} r^\tau \ \ \ \bigg\vert \ \ \ h^t, z^t, a^t  \bigg]
  $$
* A simpler **utility function** can be used for each agent, conditioned only on individual observation history and actions. We denote this with $Q(h_i,a_i; \theta_i)$

* The **Individual-Global-Max (IGM) property** states that greedy joint actions with respect to the centralized action-value function should be equal to the joint action composed of the greedy individual actions of all agents that maximize their individual utilities. 
	* More formally, define both forms of greedy actions as follows 
	  
	  $$
	  \begin{split}
	  A^\ast (h, z;\theta) &= \underset{a\in A}{\text{argmax}} \ Q(h,z,a;\theta) \\ 
	  A_i^\ast (h_i; \theta) &= \underset{a_i \in A_i}{\text{argmax}} \ Q(h_i, a_i; \theta_i)
	  \end{split}
	  $$

	* The IGM property is satisfied if the following holds for all histories $\hat{h}$ with joint observation histories $h=\sigma(\hat{h})$. individual observation histories $h_i=\sigma_i(\hat{h})$ and centralized information $z$.
	  
	  $$
	  \forall a =(a_1,\dots,a_n)\in A : a\in A^\ast (h,z;\theta ) \iff \forall i \in N: a_i \in A_i^\ast (h_i;\theta _i )
	  $$

	* *Because of IGM, we can have all agents follow a policy based on their local utility* (which is more efficient to compute)  and it would be equivalent to the original Centralized Value Function-based policy 
	* It also *helps establish reward credit* since the reward is "common" to all agents. 
	* *The IGM property is not necessarily satisfied for all environments*

## Linear Value Decomposition 
* *Assume a linear decomposition of common rewards*. That is 
  $$
  r_t = \sum_{i\in N} \overline{r}_i^t 
  $$
* The decomposition is as follows. It is guaranteed to satisfy the IGM property 
  $$
  Q(h^t, z^t ,a^t; \theta) = \sum_{i\in N} Q(h_i^t ,a_i^t; \theta_i )
  $$
* **Value Decomposition Networks (VDN)** maintain a replay buffer containing the experience of all agents and jointly optimizes the loss function 
  
  $$
  \begin{split}
  \mathcal{L} (\theta) &= \frac{1}{|\mathcal{B}|} \sum_{(h^t , a^t, r^t ,h^{t+1}) \in \mathcal{B}} \bigg(r^t + \gamma \max_{a\in A} \ Q(h^{t+1}, a;\bar{\theta}) - Q(h^t,a^t;\theta) \bigg)^2  \\ 
  
  Q(h^t,a^t;\theta) &= \sum_{i\in N} Q(h_i^t, a_i^t; \theta ) \\ 
  
  \max_{a\in A} Q (h^{t+1},a;\overline{\theta}) &= \sum_{i\in N} \max_{a_i\in A_i} \ Q(h_i^{t+1}, a; \overline{\theta}_i)
  \end{split}
  $$

![[VDN.png]]
<figcaption> VDN. Image taken from Albrecht, Christianos , and Schafer </figcaption>

## Monotonic Value Decomposition 
* Extends [[#Linear Value Decomposition]] to apply to cases when the contribution of each agent to the common reward is non-linear. 

* **QMIX** extends VDN by ensuring that the centralized action-value function is strictly monotonic with respect to individual utilities. That is 
  
  $$
  \forall i \in N, \forall a \in A: \frac{\partial  Q(h,z,a;\theta)}{\partial Q(h_i,a_i; \theta_i)} > 0 
  $$
	* In other words *the utility of any agent for its action must increase the decomposed centralized action value function*. 

* QMIX uses a mixing network which is simply a standard feedforward [[Neural Network]] $f_{\text{mix}}$ that combines individual utilities 
  
  $$
  Q (h,z,a,\theta) = f_\text{mix} \bigg(Q(h_1,a_1; \theta_1), \dots, Q(h_N, a_N; \theta_N)  \ ; \ \theta_{\text{mix}} \bigg)
  $$
	* To ensure monotonicity, we assume the mixing network only allows for positive weights. 
	* $\theta_{\text{mix}}$ is obtained using a [[Hypernetwork|hypernetworks]] $f_{\text{hyper}}$, which also receives $z$ as input. When it outputs $\theta_{\text{mix}}$, it applies an absolute value.  Because the hypernetwork receives $z$ as input, we add $z$ to the replay buffer. 
	* The loss function optimized is 
	  
$$
\mathcal{L}(\theta) = \frac{1}{|\mathcal B| } \sum_{(h^t,z^t,a^t,r^t, h^{t+1}, z^{t+1}) \in \mathcal{B}}  \bigg(r^t  +\gamma \max_{a\in A} Q(h^{t+1}, z^{t+1}, a;\overline{\theta})- Q(h^t,z^t,a^t;\theta)  \bigg)
$$

![[QMIX.png]]
<figcaption> QMIX. Image taken from Albrecht, Christianos and Schafer </figcaption>

## QTRAN
* Monotonic Value Decomposition only provides a sufficient condition but not a necessary condition.
* The following decomposition gives both sufficient and necessary (under affine transformations) conditions. 
  
  $$
  \sum_{i\in N} Q(h_i,a_i;\theta_i) - Q(h,z,a;\theta^q) + V(h,z;\theta^v)= 
  \begin{cases}
  0 & \text{if } a= a^\ast  \\
  \ge 0  & \text{otherwise}
  \end{cases}
  $$
  
  Where  $a^\ast$ is the greedy joint action , $Q(h,z,a;\theta^q)$ is the unrestricted centralized action-value function, and $V$ denotes a utility function 
  $$
  V(h,z;\theta^v) = \max_{a\in A} Q(h,z,a;\theta^q) - \sum_{i\in N} Q(h_i, a_i^\ast; \theta_i) 
  $$

* *$V$ is conditioned on centralized information since the individual utility functions of each agent may lack information* (especially if the environment is partially observable). 

* **QTRAN** trains a network that optimizes the following: 
	* For each agent, their individual utility functions $Q(h_i,a_i;\theta_i)$ 
	* A single network for the global utility function $V(h,z;\theta^v)$ 
	* A single network for the centralized action-value function $Q(h,z,a,\theta^q)$. 

* For the centralized action-value function the following loss function (a TD-error) is minimized 
  
$$
\mathcal{L}_{\text{id}} (\theta^q) = \frac{1}{|\mathcal{B}|} \sum_{(h^t, z^t,a^t,r^t,h^{t+1},z^{t+1}) \in \mathcal{B} }  \bigg(r^t + \gamma Q(h^{t+1}, z^{t+1}, a^{\ast t+1}; \overline{\theta}_q) - Q(h^t,z^t, a^t;\theta) \bigg)^2
$$
* For the utility functions, we minimize additional regularization terms given by the following (for the first case in the condition specified above where $a=a^\ast$)
  
  $$
  \mathcal{L}_{\text{opt}} (\{\theta_i\}_{i\in N}, \theta^v) = \frac{1}{|\mathcal{B}|} \sum_{(h^t,z^t,a^t, r^t, h^{t+1}, z^{t+1})\in\mathcal{B}} \bigg(\sum_{i\in N} Q(h_i^t,a_i^{\ast t}; \theta_i) - Q(h^t,z^t, a^{\ast t}; \theta^q) + V(h^t,z^t; \theta^v) \bigg)^2
  $$

* For the second case, we apply the following 
  
$$
\begin{split}
m &=  \sum_{i\in N} Q(h_i^t, a_i^t; \theta_i) -Q(h^t,z^t, a^t,\theta^q) + V(h^t,z^t;\theta^v) \\
\mathcal{L}_{\text{nopt}} (\{\theta_i\}_{i\in N}, \theta^v) &= \frac{1}{|\mathcal{B}|}  \sum_{(h^t,z^t,a^t, r^t, h^{t+1}, z^{t+1})\in\mathcal{B}} \min(0,m)^2
\end{split}
$$ 

* QTRAN gas a few limitations
	* It does not scale well due to relying on joint action space 
	* It does not directly enforce the necessary and sufficient conditions for IGM, instead using regularization terms. Hence, IGM is not guaranteed. 

## MaVEN 
* [^Mahajan_2020] suggest that representational constraints on the joint action values lead to poor exploration and suboptimality.  This is because none of these methods are able to perform **committed exploration** wherein a specific set of actions (probabilistically unlikely to be chosen in that exact sequence )are required to perform further exploration
* The monotonicity constraint can prevent the Q-network from correctly remembering the true value of the optimal action (currently perceived as suboptimal
* **Multi-Agent Variational Exploration** *learns an ensemble of monotonic approximations of QMIX via latent space representation*
	* Each model can be seen as a mode of committed joint exploration. 
	* A shared latent variable $z$ is controlled by a hierarchical policy that offloads $\epsilon$-greedy with committed exploration. Fixing $z$ gives a monotonic approximation to the optimal action-value function. 
	* The loss function becomes as follows 
	  
	  $$
	  \mathcal{L}_{\text{QL}}(\phi, \eta, \psi) = \mathbb{E}_{\pi}\bigg[\bigg( Q(s_t,a_t;z) - [r(s_t,a_t) + \gamma\max_{u_t+1} Q(s_{t+1}, u_{t+1}; z)]\bigg)^2\bigg]
	  $$
	* A hierarchical policy objective is obtained through parameter freezing 
	  
	  $$
	  \mathcal{L}_\text{RL} = \int r(\tau \mid z) \ p_\theta (z\mid s_0) \ \rho (s_0) \ dz \ ds_0
	  $$
	* Another objective makes use of mutual information to encourage diverse but identifiable behavior among policies derived from $z$. The actions in the trajectory are encoded by an [[Recurrent Neural Network|RNN]]. $\sigma$ is an operator that returns a per-agent Boltzmann policy with respect to the utilities at each time step $t$. 
	  
	  A tractable lower bound is provided using a variational distribution $q_0$ parameterized by $v$ as a proxy for the posterior over $z$.
	  
	  $$
	  \mathcal{L}_{\text{MI}}  = \text{MI} (\sigma(\tau), z)  \ge H(z) + \mathbb{E}_{\sigma(\tau), z} [\log(q_0 (z\mid \sigma(t)))] = \mathcal{L}_V(v,\phi,\eta, \psi)
	  $$

* The complete objective is the following 
  
  $$
  \max_{v.\phi, \eta, \psi, \theta} \mathcal{L}_{\text{RL}}(\theta) + \lambda_\text{MI} \mathcal{L}_V (v,\phi,\eta,\psi)  - \lambda_{\text{QL}} \mathcal{L}_{\text{QL}} (\phi, \eta, \psi)
  $$
![[__images/MAVEN.png]]
<figcaption> Maven Architecture.  Image taken from Mahajan et al. (2020) </figcaption>

![[MAVEN 1.png]]
<figcaption> MAVEN Algorithm. Image taken from Mahajan et al. (2020</figcaption>

[^Mahajan_2020]: Mahajan, Rashid, Samvelyan, Whiteson (2020) [MAVEN: Multi-Agent Variational Exploration](https://arxiv.org/pdf/1910.07483.pdf)

# Links
* [[Multi-Agent Reinforcement Learning -- Foundations and Modern Approaches by Albrecht, Christianos and Schafer|Albrecht, Christianos, and Schafer]] - Ch. 9
	* 9.5.2 - derivation of Linear Value Decomposition as well as a proof of it satisfying the IGM property.