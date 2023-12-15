* The bargaining procedure occurs as follows
	* In the first round. Player $1$ offers shares $(x,1-x)$. Player $2$ can accept and the game will end with payoffs $v_1=x$ and $v_2=1-x$.
	* In the second round, a share $1-\gamma$ of the pie is dissipated. Player $2$ offers $(x,1-x)$.  The payoff then becomes $v_1=\gamma x$ and $v_2 = \gamma(1-x)$.
	* Subsequent rounds continue, alternating between the two players and taking a slice of the pie by discounting it using $\gamma$. 
	* A hard deadline is imposed at time $T$. At which point, the players receive nothing. 

* A special case is the **ultimatum game** where we only have 1 round. Player 1 proposes to Player 2 to "take it or leave it". 
	* (*Tadelis 11.1*) In the bargaining game, if $T=1$, any division of surplus $x^\ast\in [0,1]$, $(v_1,v_2)=(x^\ast, 1-x^\ast)$ can be supported as a Nash Equilibrium. In other words, *any division of surplus can be rationalized*. 
	* (*Tadelis 11.2*) The bargaining game with $T=1$ admits a unique subperfect equilibrium in which player $1$ offers $x=1$ and player $2$ accepts any offer $x\le 1$.  [^barg_1]

* When we have a finite set of rounds, *Tadelis 11.1* suggests that no unique Nash Equilibrium exists. 
	* However, there exists a unique subperfect game equilibrium. *The last player to make the offer has the advantage*, and so for odd $T$, Player $1$ will win, and for even Player $2$.  
	* In particular, it is achieved using a split of $\left(\frac{1+\gamma^T}{1+\gamma}, \frac{\gamma-\gamma^T}{1+\gamma}\right)$
	* (*Tadelis 11.3*) Any subgame perfect equilibrium of the bargaining game must have the players reach an agreement by the first round.  [^barg_2]
	* With a long horizon and patient players, the bargain will settle for a 50-50 split.

* In the infinitely repeating case, a first move agreement must be reached since discounting renders the payoff lower than what it could be. 
	* *This implies that player 1 must offer player 2 a share that they would not reject*. Being rejected is bad when it comes to payoffs since there is now discounting that could have been avoided. 
	* Player 1 offers to keep $\frac{1}{1+\gamma}$. Player 2 only accepts if $x\le \frac{1}{1+\gamma}$. 
	* Then player $2$ offers $\frac{\gamma}{1+\gamma}$ which Player 1 accepts only if $x\ge \frac{\gamma}{1+\gamma}$.

[^barg_1]: This follows from the fact that Player 2 must have a minimum they are willing to accept.  Note that this also implies an extreme strategy -- player 1 takes all and player 2 accepts nothing.
[^barg_2]: Such equilibrium arises from both discounting and the knowledge the game will end in $T$ timesteps. Because of discounting, Player 1 should simply set their partition rather than have this partition be discounted in the payoff. Hence, the game is no different from *Tadelis 11.2*. 

# N Player Bargaining 
* Extends Strategic Bargaining in the context of $N$ players (assumed an odd amount). If a majority approve of the bargain then it is implemented. Additionally, players alternate randomly.

* In the **Closed Rule Variant** the proposer makes an offer of the form $x=(x_1,\dots,x_n)$ and this proposer's offer is consistent.
	* Under the assumption where each player proposes the same split of the pie every time regardless of history, and where voters respond only to the current proposal, the game behaves similarly to the infinite horizon case of strategic bargaining.
	*  *More patient players need to be offered more* to discourage them from waiting their turn to become proposers.
	* *As we have more players, the amount of "bargaining power" required increases.* That is, in order to get the majority vote, the proposer has to spend more than what he could expect to gain. 

* In the **Open-Rule Variant** we allow the option of amending the proposal. Once a proposal is selected, an amender (chosen from the other players) can either second the motion (in which case the game plays out like the closed rule variant) or offers an amendment which the players vote on to use as the baseline for the next timestep (wherein another amender can offer an amendment )
	* The proposer has to deter both the other voters from rejecting the proposal, waiting for their time to be proposers, and the potential that an amender successfully passes an amendment. 
	* *Guaranteed Success*: The original proposer will offer the same share to each of the two potential amenders and in equilibrium, each amender will second the proposal and it will pass.
		* As in the closed-rule variant, the more patient the players are, the more the proposer has to offer. 
		* Unlike the closed-rule variant, amendments make it so that *the proposers cannot simply cater to some of the players* to get them to accept the proposal (since the amender is randomly chosen and if they were not catered to, they will change the proposal).
		* When the discount factor is really high, *the bargaining power of the proposer decreases and the pie is more evenly split*.

	* *Risky Success*: The original proposer will offer a share to only open of the two potential amenders, taking the risk that the other player will be selected as amender. This punishes the original proposer by offering them nothing.
		* When the discount factor is high then players are patient, and it becomes quite costly for the proposer to prevent amendments from both potential amenders. *The strategy emerges from this cost as the proposer would rather risk having an amendment that could hurt him*.

# Links
* [[Game Theory -- An Introduction by Tadelis|Tadelis Ch. 11]]
	* 11.4 - an application of N-player bargaining