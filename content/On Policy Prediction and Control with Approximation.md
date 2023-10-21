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
### Gradient Descent
* We can use gradient descent methods (specifically Stochastic Gradient Descent) to adjust the weight vector at each step. 
	* In supervised learning terms: *Treat the estimate $\hat{v}$ as the predicted value and $v_\pi$ as the ground truth value.*
	* $$
	  w_{t+1}=w_t+\alpha\left[U_t-\hat{v}(S_t,w_t)\right]\nabla\hat{v}(S_t,w_t)
	  $$
	  Where $U_t$ denotes some  to the true value $v_\pi(S_t)$ (i.e., one obtained from bootstrapping using $\hat{v}$ or it may be $v_\pi + \epsilon$ )
	* If $U_t$ is [[Statistical Estimators#Properties of Good Estimators|unbiased]] then we can guarantee convergence via SGD.
	* If $U_t$ is derived from bootstrapping, then we cannot guarantee convergence.
### Semi-Gradient Descent
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
### Using Supervised Learning
* We may consider using [[Linear Models]] where each state is encoded with a series of feature vectors.
	* 

# Links
* [[Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto Ch. 9]]
	* 9.3 - Gradient Monte Carlo Algorithm, and Semi-Gradient $\text{TD}(0)$.
* [[Linear Models]] - more on basic supervised learning models.