* A **decision problem** is characterized with the following features: 
	* **Actions** - all the alternatives from which the agent can choose 
	* **Outcomes** - the possible consequences that can result from any of the actions. 
	* **Preferences** - describe how the player ranks the set of possible outcomes from most desired to least desired. 
		* The **preference relation** describes preferences. This is denoted $x\succeq y$  (read $x$ is at least as good as $y$)
		* The **strict preference relation** denotes that $x$ is at least as good as $y$.. This is notated $x\succ y$. 
		* The **indifference relation** denotes that $x$ and $y$ are equally good. This is notated $x\sim y$. 

* *The agent's preferences need not coincide with the best outcome*. 

# Assumptions and Rational Choice
* The **Completeness Axiom** says that *the preference relation is **complete*** -- any two outcomes, $x,y\in X$ can be ranked by the preference relation so that $x\succeq y$ or $y\succeq x$.
* The **Transitivity Axiom** . *The preference relation is transitive*. So that, if $x,y,z\in X$,  
  $$
  x\succeq y \ \wedge\ y\succeq z \ \implies x\succeq z 
  $$

	* *Transitivity guarantees that there is a best outcome*. 

* The **rational preference relation** is one that is both completeness and transitivity axiom. 
	* *Imposing individual rationality does not imply group rationality*. A good example of this is the Condorcet Paradox. 

* The **Rational Choice Paradigm** suggests that when a decision maker is choosing between potential actions, he will be guided by rationality to choose the best action.  Thus, the agent understands and knows: 
	* *All possible actions* $A$. Without this, the agent is probably unaware of the best course of action. 
	* *All possible outcomes* $X$. Without this, the possible outcomes cannot be foreseen
	* Exactly *how each action affects which outcome will materialize* . Without this, the agent cannot know what to do to obtain the desired payoffs. 
	* Via his payoffs, His *rational preferences over outcomes*. Without this, the effects of the action are incorrectly perceived. 

* A player facing a decision problem with payoff function $v$ over actions is rational if he chooses an action $a\in A$ that maximizes his payoff. That is 
  $$
  a^\ast \in A \text{ is chosen} \iff  v(a^\ast) \ge v(a) \ \ \ \ \forall a \in A
  $$
  In the case of stochastic decision processes, we instead maximize the expected payoff
  $$
    a^\ast \in A \text{ is chosen} \iff  \mathbb{E}[u(x)\mid a^\ast]  \ge \mathbb{E}[u(x)\mid a] \ \ \ \ \forall a \in A  
  $$
  If there is a cost involved in any way, we replace the (expected) payoff with the net (expected) payoff which is simply the expected payoff minus the cost.


# Payoffs 
* A **payoff function** $u:X\to \mathbb{R}$ represents the preference relation $z$ for any pair $x,y\in X$ such that 
  
  $$
  u(x) \ge u(y) \iff x\succeq y
  $$

* The payoff is an ordinal construct. 

* *Tadelis 1.1* - If the set of outcomes $X$ is finite then any rational preference relation over $X$ can be represented by a payoff function.
* Payoffs can be represented graphically using a decision tree. 
# Uncertainty 
* We model the uncertainty of a decision problem using [[Random Variables and Probability Distributions]]. 
* We think of the agent as *choosing between two lotteries*. Lotteries are described by a random payoff.

* A **simple lottery** over outcomes $X=\{x_1, \dots, x_n\}$ is a probability distribution $p$ that assigns probabilities for each outcome.  This probability distribution is conditional on the action $a$ chosen by the player.  A **compound lottery** is simply a lottery of lotteries. 
* For continuous action spaces and outcome spaces, we specify the cumulative distribution function $F$ conditioned over actions (so $F(x\mid a)$).

* *To compare two lotteries, we make use of their expected payoff*,  $E_p\left[u(x)\right]$.  

* *When using expected payoff theory, we can no longer assume that the payoffs are simply ordinal.* 
	* Thus, the payoff function that preserves the order of outcomes ranked by the preference relation need not be a valid representation of the preference relation in this case.

* Uncertainty can be used to characterize risk attitudes 
	* A player is **risk neutral** if he is willing to exchange any sure payout with any sure payout with any lottery that promises the same expected monetary payout. 
	* A player is **risk averse** if he is not willing to exchange a sure payout with any lottery that promises the same expected monetary payout.  
	* A player is **risk loving** if he strictly prefers the lottery with the same expected monetary payout over the sure payout
	* *Risk attitudes are related to the fact that the payoff representation of preferences more than the rank order of the outcomes. If we modify the expected payoffs, we can modify the risk attitudes*. 
	* A decreasing marginal payoff function indicates risk aversion. 

# Time 
* When time is involved, *the player will be rational at every stage* when faced with a decision. The player will seek to maximize the expected payoff received at the end of the overall process. 
* We solve this using **backwards induction**, wherein starting at the leaves of the decision tree, we collapse it (i.e., perform a [[Backups in Reinforcement Learning|backup]]) and get the optimal action. We then repeat this process until we only have one collapsed tree.

* We may use a **discount factor** for decision processes when time is involved. 
	* This accounts for future uncertainty. 
	* It also accounts for the case when the nominal payoff decreases over time. 

* The discounted sum of future payoffs is determined by
  $$
  v(x_1,\dots,x_T) = \sum_{t=1}^T \gamma^{t-1} u(x_t)
  $$
# Applications and Practice
* *The decision problem can be extended to games* wherein there is more than one agent within the environment.

* [[Reinforcement Learning]] relies on this. 
* When a decision maker is faced with the option of whether or not to acquire information and how much to pay for it, then by comparing the decision problem with the added information to the decision problem without the additional information, the player will be able to *calculate the value of the information*.
* [[Thinking Fast And Slow]] illustrates that people do not behave rationally, so while the rational paradigm works in theory as a model for decision making, in practice, *due to [[Human Biases|biases]], we do not make the rational choice*
# Links 
* [[Game Theory -- An Introduction by Tadelis|Tadelis Ch. 1-2]] 