* **Mechanism Design** pertains to the study of what kinds of mechanisms a central authority can devise to reveal some or all of the private information. *The goal is to reveal relevant private information*.

# Mechanism Design as a Bayesian Game 
* This problem can be framed as a [[Static Games of Incomplete Information|Bayesian Game]]. 
	* We have $N$ players and a set of public alternatives $X$. This set $X$ affects all players. 
	* Each player $i$ privately observes a signal (type) $\theta_i\in \Theta_i$. 
	* $\theta = (\theta_1, \dots, \theta_n)$ is the state of the world describing the profile of all players. This is drawn from state space $\Theta$. 
	* *Assume*: every equivalent has a money equivalent value and preferences are additive in money. That is, if player $i$ is given an amount money $m_i\in \mathbb{R}$ and if the public alternative is $x\in X$, then the payoff is 
	  
	  $$
	  v_i(x, m_i, \theta_i) = u_i(x,\theta_i) + m_i
	  $$
	  
	  Where $u_i$ is the money equivalent value of the alternative $x$ given type $\theta_i$. This assumption pertains to **quasilinear preferences**.
	* Outcomes are combinations of player choice of the public alternatives and the monetary amounts gained or paid. In particular, denote $Y$ as the set of outcomes.
	  $$
	  Y = \left\{(x, m_1,\dots, m_n) \mid x\in X, m_i \in \mathbb{R}, \sum_{i=1}^N m_i \le 0 \right\}
	  $$

* The **mechanism designer** is the central authority. They have the objective of achieving an outcome depending on the player types .
	* *Assume*: they do not have a source of funds to pay the players. 
	* They have a a choice rule that takes the form 
	  
	  $$
	  f(\theta) = (x(\theta), m_1(\theta) , \dots, m_n(\theta)). 
	  $$
	  
	  Where $x(\theta)$ denotes the **decision rule** and $(m_1,\dots, m_n)$ as the **transfer rule**.
	* The mechanism designer desires to implement a choice rule $f:\Theta \to Y$. 

* A **mechanism** $\Gamma$ is a Bayesian Game wherein 
	* Each player is given an action set $A_1,\dots, A_n$ and an outcome function $g:A_1\times \dots \times A_n \to Y$.
	* A pure strategy in the mechanism is a function mapping types into actions $s_:\Theta_i\to A_i$.
	* They payoffs are given as a function $v_i(g(s),\theta_i)$.
	* The inequality for a Bayesian Nash Equilibrium becomes 
	  $$
	  \mathbb{E}_{\theta_{-i}} \ \bigg[  v_i( g(s_i^\ast (\theta_i )  \ , s_{-i}^\ast (\theta_i)) \ , \theta_i) \mid \theta_i \bigg] \ge \mathbb{E}_{\theta_{-i}} \bigg[v_i( g(a_i,s_{-i}^\ast (\theta_{-i})), \theta_i) \mid \theta_i\bigg] 
	  $$
	  That is, we always follow the behavior prescribed by $s_i^\ast(\theta_i)$ regardless of which type player $i$ actually is. 

* A mechanism **implements** the choice rule $f$ if there exists a Bayesian Nash Equilibrium of the mechanism $\Gamma$, $(s_1^\ast(\theta_1), \dots, s_n^\ast(\theta_n))$ such that $\forall \theta\in \Theta$ 
  
  $$
  g(s^\ast_1(\theta_1) , \dots, s_n^\ast (\theta_n )) = f(\theta)
  $$

* *Summary*: In other words, the mechanism designer would like to know $\theta$ and choose $f(\theta)$ using the mechanism with equilibrium strategies given any $\theta$ which leads the player to choose a strategy (profile) $s$ whose outcome $g(s)$ matches what the mechanism designer wants them to do (their choice rule. )

# Revelation Principle 
* $\Gamma=(\Theta, f)$ is a **direct revelation mechanism** for choice rule $f$ if $A_i=\Theta_i$ $\forall i\in N$ and $g(\theta)=f(\theta)$ for all $\theta \in \Theta$.  In other words, it is a game where players simply announce their types  and an outcome is determined based on these types

* The choice rule $f$ is **truthfully implementable in Bayesian Nash Equilibrium** if $\forall \theta$, the direct revelation mechanism $\Gamma$ has a Bayesian Nash Equilibrium $_i^\ast (\theta_i)=\theta_i$. 
  
  That is, *all players believe all other players report truthfully, and so they themselves report truthfully*.

* (*Tadelis 14.1*) **The Revelation Principle**. A choice rule $f$ is implementable in Bayesian Nash Equilibrium if and only if it is truthfully implementable in Bayesian Nash Equilibrium. 
	* *If a decision rule can be implemented by the mechanism designer using some mechanism, then it can be implemented by the simple direct revelation game*, in which each player announces his type and the mechanism designer uses his decision rule.
	* The intuition is that any equilibrium strategy from telling the truth is dominated by a strategy that does (simply because by definition $g(s^\ast(\theta)=f(\theta$).

* *Effectively, the mechanism designer's role can be framed as informing the players of the other player's preferences without having the players understand (or need to know)  the exact preferences*.

* A strategy profile $s^\ast$ is a **dominant strategy equilibrium** of the mechanism $\Gamma$ if for every $i \in N$ and $\theta_i\in \Theta_i$ we have that 
  
  $$
  v_i(g(s_i^\ast(\theta), a_{-i}) \ , \ \theta) > v_i(g(a_i' \ , \ a_{-i}') \ , \theta)
  $$
  
  Note that this doesn't require any knowledge of the other player's types or even any correct knowledge at all. 
	* *Corollary*: The revelation principle then states that to do this, we just need to check that $f$ is truthfully implementable in dominant strategies directly.  
# Vickrey-Clarke-Groves Mechanisms 
* (*Tadelis 14.2*) In a quasilinear environment, given a state of the world $\theta$ and alternative $x^\ast \in X$ is Pareto optimal if and only if it is a solution to
  
  $$
  \max_{x\in X} \sum_{i=1}^N u_i(x,\theta_i)
  $$
  We can perform money transfers among players that would ensure the gains of some players compensate for some of the losses.  
	* In a direct revelation game, when no money transfers are made players are incentivized to lie about their preferences since they *want to maximize their individual payoffs rather than society's surplus.*
	* The problem could be solved by *aligning private incentives with social incentives*

* A decision rule is the **first-best decision rule** if for all types $\theta\in \Theta$, $x^\ast(\theta)$ is Pareto optimal. 

* Given announcements $\hat{\theta}$ of player types in a direct revelation game, the choice rule $f(\hat{\theta}) = (x^\ast (\hat{\theta}), m_1(\hat{\theta}), \dots, m_n(\hat{\theta}))$   is a **Vickrey-Clarke-Groves mechanism** if $x^\ast$ is the first-best decision rule and if for all $i$
  
  $$
  m_i(\hat\theta) = \sum_{j\ne i} u_j \left(x^\ast (\hat{\theta}_i, \hat{\theta}_{-i}) \ , \ \hat{\theta}_j \right)  + h_i(\hat{\theta}_{-i})
  $$
  
  Where $h_i$ is an arbitrary function. 

* (*Tadelis 14.3*) Any VCG mechanism is truthfully implementable in dominant strategies. 
	* Intuitively, players want to implement a decision that maximizes total surplus according to their true type, and the other players' announced types. 
	  
	  Each player tries to maximize 
	  
	   $$
	   \max_{\hat{\theta}_i \in \Theta_i} u_i \left(x^\ast (\hat{\theta}_i, \hat{\theta}_{-i} ) \ , \ \theta_i\right)+ \sum_{j\ne i} u_j \left(x^\ast (\hat{\theta}_i, \hat{\theta}_{-i}) \ , \ \hat{\theta}_j \right)  + h_i(\hat{\theta}_{-i})
	   $$

	* The effect is that *each player maximizes three things* -- their own payoff, the transfer rule based on the payoffs of the other players as if they were telling the truth, and an additional payoff based on their announced type (which can be largely ignored)
	* The choice for $m_i$ *does not rely on other players telling the truth* only that it is as if it were the truth, and that the ultimate decision of what to maximize relies on player $i$. *The player is incentivized to follow the Pareto optimal choice because they know they will be compensated and can also seek to maximize this compensation*. 
# Links 
* [[Game Theory -- An Introduction by Tadelis|Tadelis Ch. 14]]
* [[Auction Theory]] - auctions are a special case of this. The public alternative in this case is ownership of a particular item. 