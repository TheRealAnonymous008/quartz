* In an on-policy context, we refer to $\mu$ as the on-policy distribution.
	* In continuing tasks, $\mu$ is the stationary distribution under policy $\pi$.
	* In an episodic task, we calculate the following.
	  
	  Let $h(s)$ be the probability that an episode begins with state $s$.
	  $\eta(s)$ the number of time steps spent, on average, in $s$ within an episode with discounting rate $\gamma$ 
	  $$
	  \eta(s)=h(s)+\gamma\sum_{\bar{s}}\eta(\bar{s}) \sum_{a}\pi(a\mid \bar{s}) \ p(s\mid \bar{s},a)
	  $$
	  We then have 
	  $$
	  \mu(s)=\frac{\eta(s)}{\sum_{s'} \eta(s')}
	  $$
	  
* The objective function for On-Policy prediction is called the **mean square value error (MSVE)** defined as 
  $$
  \overline{VE} = \sum_{s\in S}\mu(s) \left[v_\pi(s)-\hat{v}(s,w)\right]^2
  $$
  
	* Note *minimizing MSVE does not necessarily give optimal policies* .
# Policy Prediction
* Assume that states appear in distribution $\mu$.
### Gradient Descent
* We can use gradient descent methods (specifically Stochastic Gradient Descent) to adjust the weight vector at each step. 
	* In supervised learning terms: *Treat the estimate $\hat{v}$ as the predicted value and $v_\pi$ as the ground truth value.*
	* $$
	  w_{t+1}=w_t+\alpha\left[U_t-\hat{v}(S_t,w_t)\right]\nabla\hat{v}(S_t,w_t)
	  $$
	  Where $U_t$ denotes some  to the true value $v_\pi(S_t)$ (i.e., one obtained from bootstrapping using $\hat{v}$ or it may be $v_\pi + \epsilon$ )
	* If $U_t$ is [[Statistical Estimators#Properties of Good Estimators|unbiased]] then we can guarantee convergence via SGD.
		* For example, if $U_t=G_t$ as in [[Monte Carlo Methods in Reinforcement Learning|Monte Carlo]] approximation.
	* If $U_t$ is derived from bootstrapping, then we cannot guarantee convergence with Gradient Descent because the estimates also depend on $w_t$.
### Semi-Gradient Descent and TD-0
* Modifies the Gradient Descent based approach by including only part of the gradient.
* Suitable for bootstrapping since they take into account the effect of changing $w$ on the estimate, but ignore its effect on the target.
* Convergence to global optima not guaranteed, but enables much faster learning, and allows continual, online learning.
* An example is semi-gradient TD-0 where
  $$
  U_t=R_{t+1}+\gamma\hat{v}(S_{t+1},w)
  $$
  
### State Aggregation
* Group states together with one estimated value (one component of $w$).
* We typically see a **staircase effect** where the approximate value within a group abruptly changes.
* A special case of SGD where the gradient is $1$ for $S_t$'s group's component, and $0$ for all other components
* We may think of state aggregation as a special case of [[#Coarse Coding]] where the features correspond to the group the state belongs in.
### Using Supervised Learning
* We may consider using [[Linear Models]] where each state is encoded with a series of feature vectors.
	* Linear semi-gradient $\text{TD}(0)$ converges to the **TD fixed point** where 
	  $$
	  \begin{split}
	  w_{\text{TD}}&=A^{-1}b \\ 
	  b&=E[R_{t+1} \ x_t] \\
	  A&= E\left[x_t(x_t-\gamma x_{t+1})\right]
	  \end{split}
	  $$
	  Where $x_t$ denotes the estimate of state $S_t$. [^1]
	* At the TD fixed point, 
	  
	  $$
	  \overline{\text{VE}}(w_{\text{TD}})\le\frac{1}{1-\gamma}\min_w \overline{\text{VE}}(w)
	  $$
	  Note that, $\gamma$ close to $1$ means the error of TD approximation can be quite high.
* Some tips for choosing the basis function
	* High degree polynomial bases give more accurate approximations but the number of features blows up exponentially, necessitating [[Dimensionality Reduction Models|dimensionality reduction]].
	* When using a Fourier cosine basis, it may be helpful to use a different step size for each feature. In particular, for feature $x_i$, we have the $i$-th learning rate as 
	  
	  $$
	  \alpha_i=\frac{\alpha}{\sqrt{(c_1^i)^2+\dots+(c_k^i)^2}}
	  $$
	* It is easy to select features with Fourier bases by setting the seeds $c^i$ to account for suspected interactions among state variables. However, Fourier bases are better suited for global properties not local properties of states.
	* RBF does not seem to be a good basis function. Too complex for little benefit.
* *We may use neural nets to create our features for us*.
	* ANNs can use [[Temporal Difference Learning|TD errors]] to learn value functions.
	* ANNs can be used to maximize expected reward (see [[The Exploitation-Exploration Trade-Off#Gradient Bandits|Gradient bandits]])
### State Representations
#### Coarse Coding
* Represent a state as *a subset of present features*. Features can overlap with each other.
* *Essentially, states are represented with non-mutually exclusive features*.
* Generalization from state $s$ to $s'$ depends on the number of their features whose receptive fields overlap. 
* Features with large receptive fields give broad generalization. The finest discrimination possible between states depends on the total number of features.
#### Tile Coding
* A form of coarse coding for multidimensional continuous spaces that is flexible and computationally efficient
* *Think of tile coding as bucketing but where we have many flavors of buckets. When two data points belong to the same bucket in a certain flavor, we can perform generalization.*. 
* The receptive fields of the features are grouped into partitions of the state space. Each such partition is called a **tiling**, and each element of the partition is called a **tile**.
* A coarse coding is obtained using multiple tilings, shifted around.
* Generalization occurs to states other than the one trained if those states fall within any of the same tiles,
* Prefer asymmetrical offsets for better generalization. *Intuition, irregular offsets = irregular overlap*.
* *Denser tilings = more importance given during generalization*.
* We may use *hashing* to reduce memory requirements -- each bin in the hash set corresponds to a tile.

[^1]: Convergence is guaranteed because $A$ is positive definite and so the inverse exists. See [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto 9.12]]. 


### Step Size
* Suppose we want to learn $\tau$ experiences with feature vector $x$. The step size should be set as 
  
  $$
  \alpha = \left(\tau E[x^Tx]\right)^{-1}
  $$
* This method works best if the feature vectors do not vary greatly in length
### Least Squares TD
* *Optimizes Semi-Gradient TD(0) by computing it iteratively.*. 
  
  $$
  \begin{split}
  \hat{A_t} &= \sum_{k=0}^{t-1}x_k(x_k-\gamma x_{k+1})^T+\epsilon I \\
  \hat{b_i} &= \sum_{k=0}^{t-1}R_{k+1}x_k 
  \end{split}
  $$
  
  We add $\epsilon I$ to make the matrix [[Matrix Inversion|invertible]]. $\epsilon>0$ is taken to be really small.
  
  For computation's sake, we make use of the [[Matrix Inversion|Sherman-Morrison formula]].

* The $\epsilon$ functions similarly to the step size parameter $\alpha$. 
* Since LSTD has no step-size parameter, it never forgets (this is both an advantage and a disadvantage).

### Memory-Based Function Approximation
* Non-parametric method that saves training examples in memory as they arrive without updating parameters.
* When we need an approximation for a query state, we simply fetch from the stored training examples (aka, *we do lazy learning*).
	* *These methods improve with more data*.
	* We are also not reliant on global approximations. We instead rely on local approximations.
* **Local learning** involves approximating the value function using the local neighborhood of the current query state.
	* One approach is doing *(weighted) kNN* with the incoming query state as input, and the stored states as memory.
	* Another approach is *locally weighted regression* where we fit a surface to the values of a set of nearest states. The weights we use are dependent on distance.
### Kernel-Based Function Approximation
* We make use of  a **kernel function** that assigns a number to indicate the similarity between two states.
* We may view the kernel function $k(s',s)$ as *the strength of generalization from $s$ to $s'$*. 
	* If we have feature vectors, we may have the following kernel 
	  
	  $$
	  k(s,s') = x(s)^Tx(s)
	  $$
	* And, of course, we can use the kernel trick as needed.
* **Kernel Regression** involves using a kernel weighted average of the targets of all examples stored in memory.  In particular if we have samples $\mathcal{D}$ and targets $g(s')$ we have
  
  $$
  \hat{v}(s,\mathcal{D}) = \sum_{s'\in\mathcal{D}} k(s,s') g(s')
  $$

### Interest and Emphasis
* *Rationale*: Relax our assumption of updating all states equally.
* Let $I_t$ be the **interest** - indicating the degree to which we are interested in state $S_t$.
* Let $M_t$ be the **emphasis** which multiplies the learning update, and thus emphasizes or de-emphasizes the learning done at time $t$.
* The distribution $\mu$ for $\overline{VE}$ then depends on $I_t$.
* The *update rule with emphasis* becomes 
  
  $$
  w_{t+1}=w_t+\alpha M_t\left[U_t-\hat{v}(S_t,w_t)\right]\nabla\hat{v}(S_t,w_t)
  $$

* The emphasis is related to the interest with the formula 
  
  $$
  M_t=I_t+\gamma^nM_{t-n}
  $$
  
  And $M_t=0$ for $t<0$.
# Policy Control
* Update rules are based on $\hat{q}(s,a,w)$.  
  
  $$
  w_{t+1}=w_t+\alpha\left[U_t-\hat{q}(S_t,A_t,w_t)\right] \nabla \hat{q}(S_t,A_t,w_t)
  $$
### Episodic Semi-Gradient Control
* **Episodic, Semi-Gradient One-Step [[Temporal Difference Learning#SARSA|SARSA]]** The update rule makes use of $U_t=R_{t+1}+\gamma\hat{q}(S_{t+1},A_{t+1},w_t)$  
* **Episodic, Semi-Gradient [[Temporal Difference Learning#n-step SARSA|n-step SARSA]]** is obtained by using the following as $U_t$
  
  $$
  G_{t:t+n} = R_{t+1}+\gamma R_{t+2} +\dots+\gamma^{n-1}R_{t+n} + \gamma^n \hat{q}(S_{t+n}, A_{t+n}, w_{t+n-1})
  $$Where $G_{t:t+n}=G_t$ if $t+n>T$. 

### Handling Continuing Tasks
* One concern is *how do we handle action selection when actions are selected on a continuum*.
* We can use the [[A Unified View on Reinforcement Learning Approaches#Average Reward Formulation|average reward]] formulation. It is in fact, questionable if we should even be using the [[A Unified View on Reinforcement Learning Approaches#Discounted Formulation|discounted setting]].
	* To account for variance in return, in the discounted setting we would have to take the average.
	* *For continuing tasks, discounting has no effect* because the average of the discounted returns is proportional to the average reward. *The ordering of all policies in the average discounted return setting and the average reward setting are the same*.
	* A formal proof is given in [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto 10.4]].

* **Differential Semi-Gradient n-step SARSA** is defined using the differential form of the return as
  
  $$
  G_{t:t+n}=R_{t+1}-\overline{R}_{t+n-1}+\dots+R_{t+n} - \overline{R}_{t+n-1} +\hat{q}(S_{t+n}, A_{t+n}, w_{t+n-1})
  $$
  
  Where $\overline{R}$ estimates $r(\pi)$. As usual $G_{t:t+n}=G_t$ if $t+n>T$. 

# Links
* [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto Ch. 9-10]]
	* 9.3 - Gradient Monte Carlo Algorithm, and Semi-Gradient $\text{TD}(0)$.
	* 9.5 - Different Basis Functions 
	* 10.1 - Episodic Semi-Gradient SARSA
* [Tile-Coding: An Efficient Sparse-Coding Method for Real-Valued Data](https://medium.com/criteo-engineering/tile-coding-an-efficient-sparse-coding-method-for-real-valued-data-e787eddf630a) 

* [[Linear Models]] - more on basic supervised learning models.