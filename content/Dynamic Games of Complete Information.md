# Nash Equilibrium
* The principles applied [[Static Games of Complete Information|here]] are applicable in the analysis of dynamic games of complete information since *we can convert extensive-form to normal-form* (see [[Fundamental Constructs in Game Theory#Dynamic Games|here]]).  In doing so, we can capture all the Nash Equilibria of the dynamic game. 
	* In an extensive game, every outcome of the game is associated with a *unique path of play* determined by some Nash Equilibrium in the game. 
	  
	  More formally, let $\sigma^\ast=(\sigma_1^\ast,\dots,\sigma_n^\ast)$ be a Nash equilibrium profile of behavioral strategies in an extensive form game. An information set is **on the equilibrium path** if given $\sigma^\ast$ it is reached with positive probability [^1]. 
	  
	  An information set is **off the equilibrium path** if it is never reached.

* In a Nash Equilibrium, players choose to proceed on the equilibrium path because of their beliefs about what the players are doing on and off the equilibrium path. 
	* However, because normal-form games treat all choices as "once-and-for-all" simultaneous choices, *beliefs can never be challenged and the player may not respond optimally*
	* Players only act rationally on the equilibrium path based on the belief on what happens both on and off the equilibrium path. However, *there is no restriction on the beliefs of players off the equilibrium path*. 
	* This is in contrast to what we might expect where players can respond optimally wherever they are called to move.

[^1]: Analogous to support

# Sequential Rationality 
* Given strategies $\sigma_{-i}\in \Delta S_{-i}$, we say that $\sigma_i$ is **sequentially rational** if and only if $i$ is playing a best response to $\sigma_{-i}$ in each of his information sets. 
* A **backward induction** procedure is one where we start from the terminal nodes at the end of the game and work our way up the decision tree to its root.
	* (*Tadelis 8.1*) **Zermelo's Theorem**)- Any finite game of perfect information has a backward induction solution that is sequentially rational. Furthermore if no two terminal nodes prescribe the same payoffs to any player then the backward induction solution is unique.
	* *Tadelis cor. 8.1* - Any finite game of perfect information has at least one sequentially rational Nash equilibrium in pure strategies. Furthermore if no two terminal nodes prescribe the same payoffs to any player then the game has a unique sequentially rational Nash equilibrium.

* *Backward induction cannot be applied to games of imperfect information, nor to games that do not end in finite time*. 

## Subgame-Perfect Nash Equilibrium 
* A **proper subgame** $G$ of an extensive-form game $\Gamma$ consists of only a single node and all its successors in $\Gamma$ with the property that if $x\in G$ and $x'\in h(x)$, then $x'\in G$. The subgame $G$ is a game [[Trees|tree]] that is a subtree of $\Gamma$.  
	* In other words, it is a smaller game within the larger game. 
	* A  player’s best response depends only on his beliefs about what the other players are doing within the subgame

* Let $\Gamma$ be an $n$-player extensive form game. A behavioral strategy profile $\sigma^\ast = (\sigma_1^\ast,\dots,\sigma_n^\ast)$ is a **subgame-perfect Nash equilibrium** if for every proper subgame $G$ of $\Gamma$, the restriction of $\sigma^\ast$ to $G$ is a Nash equilibrium in $G$.
	* $\sigma^\ast$ is a Nash equilibrium in all subgames, even those that are not reached in the equilibrium path.

* For any finite game of perfect information, the set of subgame-perfect Nash equilibria coincides with the set of Nash equilibria that survive backward induction. 
* *At least one of the Nash equilibria in a game will be a subgame-perfect equilibrium.*

# Multistage Games 



# Example Games  
* The **Centipede Game**
![[Centipede Game.png]]
<figcaption> Centipede Game </figcaption>
* Based on empirical experiments with the game: When players are expected to share common knowledge of rationality they indeed play the backward induction solution.

* **Stackelberg Model of Duopoly** - a sequential version of the Cournot game wherein price is fixed and quantity is set. The only difference is firm 1 chooses first before firm 2. 

# Links
* [[Game Theory -- An Introduction by Tadelis|Tadelis Ch. 7 - 11]].
* [[Fundamental Constructs in Game Theory]]