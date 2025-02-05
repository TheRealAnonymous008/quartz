* Proposed by [^yang_2018]
* *Interactions within the population of agents are approximated by those between a single agent and the average effect from the overall population or neighboring agents.*
* It aims to address non-stationarity and convergence of [[MARL Problem Statement|MARL problems]] and the instability of various [[MARL Algorithms and Approaches|MARL approaches]]. 

* The $Q$ function is factorized using only pairwise local interactions.  Let $N(j)$ be the index set of the neighboring agents of agent $j$ as defined by the problem.
  
  $$
  Q_j (s,a) = \frac{1}{|N(j)|} \sum_{k\in N(j)} Q_j (s,a_{j}, a_k) 
  $$

* The pairwise interaction $Q_j(s,a_j,a_k)$ is approximated using [[Mean Field Theory]]. 
  
  Let $a_j$ be represented using a one-hot encoding of each of the $D$ possible actions.
  
  The **mean action** denoted $\overline{a}_j$ based on neighborhood $N(j)$ is defined as follows
  $$
  \begin{split}
  \overline{a}_j &= \frac{1}{|N(j)|} \sum_k a_k \\
  a_k  &=  \overline a_j + \delta a_{j,k} 
  \end{split} 
  $$
  Where $\delta a_{j,k}$ is a small perturbation to the mean action. 

* The $Q$ function can then be expressed as 
  $$
  Q_j(s,a) = Q_j (s,a,\overline{a}_j) + \frac{1}{2|N(j)|} \sum_{k} R_j^{s,a_j} (a^k)
  $$
  Where
  $$
  \begin{split}
  R_j^{s,a_j}(a_k) &= \delta a_{j,k} \cdot \nabla^2{\tilde{a}_{j,k}} Q_j (s,a_j,\tilde a_{j,k}) \cdot \delta a_{j,k} \\
  \tilde{a}_{j,k} &= \overline{a}_j + \epsilon_{j,k}\cdot \delta a_{j,k} \\
  \epsilon_{j,k} &\in [0,1]
  \end{split} 
  $$
  Essentially $R_j^{s,a_j}(a_k)$ acts as a random variable which serves as a small perturbation near zero. 

* Assuming all agents are homogeneous, the remainders cancel and give us the following approximation
  $$
  Q_j(s,a)  = Q_j(s,a_j,\overline{a}_j)
  $$
  That is *the pairwise interactions are simplified to be between $j$ and a virtual mean agent (from the mean effect of all of $j$'s neighbors)*. 

* The mean-field $Q$ function is updated as follows
  $$
  \begin{split}
  Q_j^{t+1}(s,a_j,\overline{a}_j) &= (1-\alpha) Q_j^t (s,a_j,\overline{a}_j) + \alpha [r_j + \gamma v_j^t (s')] \\
  v_j^t(s') &= \sum_{a_j} \pi_j^t (a_j \mid s',\overline{a}_j) \mathbb{E}_{a_j (a_{-j})\sim \pi^t_{-j}}\big[Q_j^t (s',a_j,\overline{a}_j)\big]
  \end{split}
  $$
* The MARL problem is thus converted to finding $j$'s best response with respect to the mean action of all its neighbors. 

* The policy $\pi_j^t$ can be defined using the virtual mean agent as 
  $$
  \pi_j^t (a_j\mid s,\overline{a}_j) = \frac{\exp(-\beta Q_j^t (s,a_j,\overline{a}_j))}{\sum_{a_{j'}\in A_j} \exp(-\beta Q_j^t (s,a_j',\overline{a}_j))} 
  $$

* For [[Policy Gradient Methods]] we minimize the loss function
  $$
  \begin{split}
  \mathcal{L}(\phi_j) = (y_j - Q_{\phi_j}(s,a_j,\overline{a}_j))^2
  \end{split}
  $$
  Where
  $$
  y_j = r_j + y v_{\phi_{\overline{j}}}(s')
  $$
  is the target mean value. 
  
  The gradient is then given by
  $$
  \nabla_{\phi_j} \mathcal{L} (\phi_j) = (y_j - Q_{\phi_j} (s,a_j,\overline{a}_j)) \nabla _{\phi_j}Q_{\phi_j} (s,a_j,\overline{a}_j)
  $$

* For actor critic methods, the gradient of the actor is trained with the gradient
  $$
  \nabla_{\theta_j} J(\theta_j) \approx \nabla_{\theta_j} \log \pi_{\theta_j} (s) Q_{\phi_j} (s,a_j,\overline a_j ) 
  $$




[^yang_2018]: Yang et al. (2018) [Mean Field Multi-Agent Reinforcement Learning](https://proceedings.mlr.press/v80/yang18d/yang18d.pdf)


* [^Zaman_2024]  introduces a  mean field approach to the problem of cooperative team-based MARL with infinitely many agents -- The **General-Sum LQ Mean-Field Type Game (GS-MFTG)**. The paper also develops the corresponding **Multi-Player Receding-Horizon Natural Policy Gradient (MRPG)** 
	* *Assume* The LQ setting where agent dynamics are linear and costs are quadratic. This is to simplify things.
	  
	  Agents are grouped into $N$ teams. Each team has $M_i$ agents and team $j$ in team $i$ has linear dynamics -- that is, it is driven by a linear function of the agent state, action, and mean state and actions of population $i$. We term this setting as Cooperating-Competing (CC). In particular, the dynamics in the setting is given by
	  $$
	  x_{t+1}^{i,j} = A_t^ix_t^{i,j} +\overline{A}_t^i\overline{x}_t^i + \sum_{k=1}^N (B_t^{i,k}u_t^{i,j,k} + \overline{B}_t^{i,k}\overline{u}_t^{i,k}) + \omega_{t+1}^{0,i} + \omega_{t+1}^{i,j}
	  $$
	  Where each $A, B$ are matrices of appropriate size. and $\omega_t^{i,j}\sim \mathcal{N}(0.\Sigma^i)$ represents noise and $\omega_t^{0,i}\sim\mathcal{N}(0,\Sigma^0)$ represents common noise.  
	  
	  Actions for the $j$-th agent in team $i$ is denoted  $u_t^{i,j,i}$ and $u_t^{i,j,k}$ denotes the adversarial input of player $k$ into the dynamics of $j$ in $i$.
	  
	  The objective is the following for the team (and the $i$-th agent). Here, the $R$'s are positive definite and $Q$ are positive semi-definite symmetric matrices.
	  
	  $$
	  \begin{split}
	  J_M^i(u^i,u^{-i}) &= \frac{1}{M_i} \mathbb{E}\sum_{j\in M_i} \sum_{t=0}^{T-1} \|x_t^{i,j} -\overline{x}_t^i\|_{Q_t^i}^2 + \|x_t^i\| ^2 _{\overline{Q}_t^i} \\
	  &+ \sum_{k=1}^N \|u_t^{k,j,i} -\overline u_t^{k,i}\| _{R_t^{k,i}}^2 + \|\overline{u}_t^{k,i}\|^2_{\overline{R}_t^{k,i}}  + \|x_T^{i,j} -\overline{x}_T^i\|^2_{Q_T^i} + \|\overline{x}_T^i\|_{\overline Q_T^i} ^2 
	  \end{split}
	  $$
	  
	  We also assume the mean field setting. The game itself is termed a **Mean Field Type Game** with the **GS-MFTG** its limit. 
	  
	  We denote $\mathcal{U}^i$ as the set of all policies causally adapted to the state and mean field process for agent $i$. 
	  
	  We will also use, for notation, $_M^i$ pertaining to the $i$-th agent for the $M$-th team. 
		* *Define* $\|x\|_A = (x^TAx)^{\frac{1}{2}}$ see [[Quadratic Form]].

		* The [[MARL from a Game Theoretic Perspective|Nash Equilibrium]] of the MFTG is an $\epsilon$-Nash for the finite agent CC game where  $\epsilon=O(1/\min_i M_i)$. We have that 
		  $$
		  J_M^i (u^{i\ast} , u^{-i\ast}) -\inf_{u^i \in \mathcal{U}_M^i} J^i_M (u^i,u^{-i\ast}) = O(\frac{T\sigma}{\min_i M_i})
		  $$
		* We decompose the MFG into two parts
		  $$
		  \begin{split}
		  J^i(u^i, u^{-i}) &= J_y^i (v^i, v^{-i}) + J_\hat{x} ^i (\overline u^i , \overline u^{-i})) \\ 
		  
		  J_y^i(v^i, v^{-i}) &= \mathbb{E}\left[\sum_{t=0}^T \left[\|y_t\|^2_{Q_t^i} + \|v_t^i\|^2_{R_t^i}\right] + \|y_T\|_{Q_T^i}^2\right] \\
		  
		  
		  J_y^i(\overline{u}^i, \overline u^{-i}) &= \mathbb{E}\left[\sum_{t=0}^T \left[\|\overline x_t\|^2_{Q_t^i} + \|u_t^i\|^2_{R_t^i}\right] + \|\overline x_T\|_{Q_T^i}^2\right]
		  \end{split}
		  $$
		  
		  Where
		  $$
		  \begin{split}
		  y_{t+1} &= A_ty_t + \sum_{i=1}^N B_t^iv_t^i + \omega_{t+1} \\
		  x_{t+1} &= \overline{A}_tx_t + \sum_{i=1}^N \overline{B}_t^i u_t^i + \omega_{t+1}^0
		  \end{split}
		  $$
		  *The above shows that we can decouple the dynamics in the setting as the mean-field setting and the deviation from the mean-field*.  
	* We use the Hamilton-Jacobi-Isaac equations to solve the Nash Equilibrium:
	  $$
	  \pi_i^{t\ast} = \underset{\pi}{\text{argmin}}  C_i^t (\pi, \pi_{-i}^t \mid \pi^{\ast [t+1,T-1]})
	  $$
	  For $t\in \set{0,\dots, T-1}$ and $\forall i$. Here $C_i^t$ is the partial cost of agent $i$ and $\pi^{[t,t']}$ is the set of policies for all agents from time $t$ to $t'$. We use the **Natural Policy Gradient (NPG)** to perform the minimization using the approximator $\overline{\pi}_{i}^t$. 
	  
	  In fact, because of the LQ conditions, $\overline{\pi}_i^t \approx \pi_i^t$ $\forall i, t$.   
		* The key idea is as follows
		  For the deviation dynamics:  find the policies for all agents at a fixed time $t$ and move backwards in time.
		  
		  For the mean field dynamics: find the policies for all agents at a fixed time $t$ and move forwards in time .
		* At each time step $t$, solve for the set of controllers at time $t$, $K_t^i$ which minimize the cost $\overline{J}_{y,t}^{i,1}(K^i, K^{-i})$ while keeping $(K_s)_{t<s<T}$ fixed. More specifically, for process $y$ above,  choose an arbitrary agent (say agent $1$) and: 
		  $$
		  \min_{K_t^i} \overline{J}_{y,t}^{i,1} (K^i,K^{-i}) = \mathbb{E}\left[\|y_t^1\|^2_{Q_t^i + (K_t^i)^T R_t^i K_t^i} + \sum_{s={t+1}}^T \|y_s^1\| ^2 _{Q_s^i + (K_s^i)^T R_s^i K_s^i}\right]
		  $$
		  For $\overline{x}$, we calculate the set of controllers $\overline{K}_t^i$ by minimizing the cost while keeping $(\overline K_s)_{t<s<T}$  fixed. More specifically, for $\overline{x}$, we have: 
		   $$
		  \min_{\overline K_t^i} \overline{J}_{\overline x,t}^{i,1} (\overline K^i,\overline K^{-i}) = \mathbb{E}\left[\|\overline x_t\|^2_{\overline Q_t^i + (\overline K_t^i)^T \overline R_t^i \overline K_t^i} + \sum_{s={t+1}}^T \|\overline x_s\| ^2 _{Q_s^i + (\overline K_s^i)^T \overline R_s^i \overline K_s^i}\right]
		  $$
		* The algorithm proceeds using gradient descent. In particular, we use the Natural Policy gradient. In particular, if we assume that $y_t\sim \mathcal{N}(0,\Sigma_y)$ and $\overline x \sim\mathcal{N}(0, \Sigma_{\overline x})$
		  
		  $$
		  {K^i_t\choose \overline{K}_t^i} \gets {K^i_t\choose \overline{K}_t^i} + \eta_k^i {\overline\nabla _{y,t}^i (K^i, K^{-i}) \Sigma_y^{-1}
		  \choose
		  {\overline\nabla _{\overline x,t}^i (\overline K^i, \overline K^{-i}) \Sigma_{\overline x} ^{-1}}}
		  $$
		  Where the gradients are calculated as follows (the calculation for $\overline{K}$) is done similarly
		  $$
		  \overline{\nabla}_{y,t}^i (K^i, K^{-i}) = \frac{m}{N_br^2}\sum_{j=1}^{N_b} \overline{J}_{y,t}^i (\hat{K}^i(e_j,t), K^{-i}) e_j
		  $$
		  Where $e_j \sim \mathbb{S}(r)$ is a perturbation and 
		  $$
		  \hat{K}^i(e,t) = (K_t^i + e, \dots, K^{i}_{T-1})
		  $$
		  is a controller set perturbed at time $t$. 

![[MRPG.png|300]]
<figcaption> MRPG approach. Image taken from  Zaman, Koppel, Lauriere and Basar (2024)</figcaption>


[^Zaman_2024]: Zaman, Koppel, Lauriere, and Basar (2024) [Independent RL for Cooperative-Competitive Agents: A Mean-Field Perspective](https://arxiv.org/abs/2403.11345)


* [^mondal_2021] gives an approximation bound for applying Mean Field Control to the case of cooperative [[Heterogeneous MARL]] problems where we have  a collection of $N_{\text{pop}}$ agents segregated into $K$ agent types, with $N_k$ agents of each type.  We denote $\mathcal{A}$ and $\mathcal{S}$ as the action and state space of each agent
  
  The bounds are given below, dependent on what the reward and transition dynamics of all agents are a function of:
	* The joint state and action distributions across all classes
	  $$
	  O\left(\frac{\sqrt{|\mathcal{A}|} + \sqrt{|\mathcal{S}|}}{N_\text{pop}} \sum_k\sqrt{N_k}\right)
	  $$
	* The individual distributions of each class
	  $$
	  O\left(\left[\sqrt{|\mathcal{A}}| + \sqrt{|\mathcal{S}|}\right] \sum_k \frac{1}{\sqrt{N_k}}\right)
	  $$
	*  The marginal distribution of the entire population. We define $A,B$ as proportionality constants.
	  $$
	  O\left(\left[\sqrt{|\mathcal{A}}| + \sqrt{|\mathcal{S}|}\right] \left[\frac{A}{N_\text{pop}} \sum_{k} \sqrt{N_k} + \frac{B}{\sqrt{N_{\text{pop}}}}\right]\right)
	  $$



[^mondal_2021]: Mondal et al. (2021) [On the Approximation of Cooperative Heterogeneous Multi-Agent Reinforcement Learning (MARL) using Mean Field Control (MFC)](https://arxiv.org/abs/2109.04024)