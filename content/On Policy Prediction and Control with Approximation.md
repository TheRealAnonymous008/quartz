* In an on-policy context, we refer to $\mu$ as the on-policy distribution.
	* In continuing tasks, $\mu$ is the stationary distribution under policy $\pi$.
	* In an episodic task, we calculate the following.
	  
	  Let $h(s)$ be the probability that an episode begins with state $s$.
	  $\eta(s)$ the number of time steps spent, on average, in $s$ within an episode with discounting rate $\gamma$ $$\eta(s)=h(s)+\gamma\sum_{\bar{s}}\eta(\bar{s}) \sum_{a}\pi(a\mid \bar{s}) \ p(s\mid \bar{s},a)$$We then have $$\mu(s)=\frac{\eta(s)}{\sum_{s'} \eta(s')}$$
* The objective function for On-Policy prediction is called the **mean square value error** defined as $$\overline{VE} = \sum_{s\in S}\mu(s) \left[v_\pi(s)-\hat{v}(s,w)\right]^2$$
# Policy Prediction

# Links
* [[$Reinforcement Learning - An Introduction by Sutton and Barto|Sutton and Barto Ch. 9]]