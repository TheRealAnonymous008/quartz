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