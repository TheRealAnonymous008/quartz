* There are two kinds of auctions 
	* **Open Auction** - the bidders observe some dynamic process that evolves until a winner emerges. 
		* **English Auction**-  the players bid increasing prices until no player is willing to bid. At which point the highest bidder pays. 
		* **Dutch Auction** - the price starts really high and goes progressively down. Once a bidder declares they will buy, the auction ends. 
	* **Sealed Bid** - bidders write down their bids and submit them without knowing the bids of their opponents. Highest bidder wins. 
		* **First-Price** - bidders write down the bid in an envelope. Bidding prices are revealed simultaneously and the highest bidder wins, playing the price equal to their bid. 
		* **Second Price** - similar to first-price but the highest bidder does not pay their bidding price, rather they pay the second highest bidding price

* To frame an auction as a [[Bayesian Statistics|Bayesian]] game, we will set the type of the player to be the value of player $i$ obtaining the good. 
	* Each player knows the type distribution of other players., encapsulated in the cumulative distribution function $F_j(\cdot)$, where $j\ne i$ .
	* Each player's strategy is some bidding price $s_i(\theta_i)$ that is dependent on his valuation $\theta_i$. 
	* The payoff is $0$ if the player loses and if they win and pay price $p$, the payoff is $\theta_i-p$. 
	* We assume **Independent Private Values**, that is, types are sampled independently from the type distribution

## Second-Price Sealed Bid
* (*Tadelis 13.1*) In the second-price sealed bid auction, each player has a [[Static Games of Complete Information#Weak Dominance|weakly dominant strategy]] which is to bid his true valuation. That is $s_i(\theta_i)=\theta_i$ is a Bayesian Nash Equilibrium in weakly dominant strategies. 
	* *Intuition*: It is never worse to bid your true valuation and it's also strictly better. 
		* This is because even if you win, you don't have to pay your bidding price 
		* And if you bid something lower than your bidding price, either you could've win by bidding the maximum amount (i.e., $\theta_i$) or you would still have lost (in which case there is no difference).
	* Additionally, it is worse to bid higher than your true valuation (since in the case you do win, you will have to pay more.)

* This result implies three things
	* Bidders in this scenario do not care about the probability distribution over their opponent types. Hence, *this auction works even when players have no idea about their opponent's preferences*
	* *Independence of type valuation is not necessary*. Players can still bid truthfully even when their beliefs about the type distribution are incorrect.
	* *The auction is Pareto optimal*. The person who values the item most will get the item. 

## English Auction
* For the English Auction, we reframe the problem as follows: The price raises continuously over time. If a player taps out (is unwilling to pay the price), they are permanently out of the game. The last player wins the item.  This is called the **Button-Auction Model** (tapping out in the game is reminiscent to releasing a button). 

* (*Tadelis 13.2*) In the button-auction model, it is a weakly dominant strategy for each player to keep playing as long as $p<\theta_i$, and to stop playing once $p=\theta_i$. This results in a Bayesian Nash equilibrium in weakly dominant strategies that is *outcome-equivalent to the second price, sealed bid auction.*
	* If the player taps out while $p<\theta_i$ they forego  any opportunity to win the item at a price lower than their valuation.  
	* If the player keeps playing while $p\ge \theta_i$, then they may win the item but have to pay more than they are willing to for the item. 
	* The player ends up playing the second highest price (when the last player tapped out). 

* It remains appealing in the same way as [[#Second-Price Sealed Bid]] auctions are.

## First-Price Sealed-Bit Auctions and Dutch Auctions
* (*Tadelis Claim 13.1*) In a first-price sealed bid auction, it is a dominated strategy for a player to bid their valuation. 
	* Bidding the valuation means the players' payoff is zero -- losing implies a payoff of $0$ and winning implies paying the same amount the item is worth
	* *Players will lower their bid to increase payoff at the cost of the probability of winning*. 

* *Assume* that a higher player valuation implies a higher bid. In other words
  
  $$
  \theta_j' >\theta_j'' \implies s_j(\theta_j') > s_j(\theta_j'')
  $$

* The assumption allows us to calculate the payoff as 
  
  $$
  \prod_{j\ne i} \left[F_j (s_j^{-1} (b_i) )\right] \times (\theta_i-b_i)
  $$
  And assuming a symmetric strategy for all players, we have that [^auc], assuming $\theta\in \{\theta^-, \theta^+\}$ 
  
  $$
  s(\theta) = \theta - \frac{\int_{\theta^-}^{\theta^+} \left[ F (x)\right]^{n-1} \ dx}{ [F(\theta)]^{n-1}}
  $$
  
  Where the second term in the RHS of the equation above denotes how much below the valuation player $i$ bid. As expected *the optimal bid is to shade the bid depending on the knowledge of other players' types*

## Revenue Equivalence
* The **Revenue Equivalence Theorem** states that any auction game that satisfies four conditions will yield the same expected revenue, and will yield each type of bidder the same expected payoff. 
	* Each bidder's type is drawn from a well-behaved distribution 
	* Bidders are risk neutral. 
	* The bidder with the highest type wins. 
	* The bidder with the lowest possible type has an expected payoff of $0$. 

[^auc]: For more info, see [[Game Theory -- An Introduction by Tadelis|Tadelis]] Ch. 13.1.3.

## Common Value
* **Common Value** means that the value of obtaining the resource is not solely determined by the player's type -- but it can also be determined by other player's types. 
* The **winner's curse** - players will tend to win when they receive signals (information) that are optimistic, and which means that they have over-estimated the value of the good and are thus overpaying
* Thus *players must bid with the winner's curse in mind* to avoid overpaying for the object. 

# Links 
* [[Game Theory -- An Introduction by Tadelis|Tadelis Ch. 13]]
* [[Static Games of Incomplete Information]]