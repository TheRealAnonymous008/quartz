* [[The Language of Patterns|A pattern language]] for various game design mechanics in tabletop games.
# Game Structure
* **Competitive Games** - A game with two or more players and a single winner.  
	* Competitive Games need to be [[Game Balancing|balanced]]
* **Cooperative Games** - Players coordinate their actions to achieve a common win condition or conditions. Players all win or lose the game together. 
	* These tend to be more forgiving for novices.
	* Requires scaling the game difficulty with respect to the number of players.
	* Another consideration is player agency -- do players have to reach a consensus or can they act on their own.
	* One problem that needs to be addressed is one player dominating and overriding the rest of the group.
* **Team Based Game** - Teams of players compete with one another to obtain victory.
	* Allows for a mix of both cooperation and competition.
	* Teams can either be fixed or flexible (i.e., alliances can be freely made or broken)
	* Consider giving players different roles per team. The challenge here is teaching the player each role.
	* Teams can be asymmetric (i.e., one vs all games). The challenge here is balance.
* **Solo Game** - a game intended for a single player. 
	* The challenge is to design the game's [[Artificial Intelligence|AI]] system so that it is fun to play against.
* **Semi-Cooperative Game** - A game which ends with either no winners or the players winning as a group but a single player being recognized as the individual winner as well.
	* Prone to sabotage, especially when players have to weigh between individual loss and group victory, and group loss.
	* Incorporates individual motivations per player.
* **Single Loser Game** - A game with three or more players in which players are not assigned to static teams and which ends with only one loser.
	* Incentivizes players to not perform better than everyone else but be better than one other person.
	* Encourages players to impede with one another or dogpile on the losing players.
* **Traitor Game** - a team or cooperative game with a betrayal mechanism. The traitors win by triggering the fail condition for players. The identity of traitors is hidden at the start.
	* Consider how the game plays at different stages of knowing the traitor's identity. Make sure the game is still fun even if the traitor's identity is deduced
	* Make sure the traitor always has [[The Fundamentals of Game Design|meaningful]] choices.
* **Scenario Games** - Games which feature a narrative or campaign using different game configurations.
* **Score and Reset Games** - Players play until reaching a stopping condition, then record scores, reset the game, and play one or more additional rounds. The game concludes after some number of rounds, and the cumulative score is calculated to determine a winner.
* **Legacy Game** - a multisession game where permanent and irreversible changes of the game state carry over from session to session
	* Difficult to playtest 
	* Requires consideration for player progression

# Turn Order and Structure
* **Fixed Turn Order** - Turn order is set at the start of the game and never varies. Each player takes a turn in the same sequence until the end of the game.
	* Often results in an imbalance favoring the players going first. This imbalance can be offset by giving bonuses to the players behind in turn order
	* All players should have an equal number of turns
	* [[Dynamic Games of Incomplete Information|Knowledge about when the game ends]] can be used to meta-game.
* **Stat Turn Order** - The turn order within each Round is set by some statistic relating to the players’ resources or position in the game.
	* If players who are ahead on the score track during the game are penalized by turn order, it will give increased weight to strategies that maximize end-game points
	* When the advantages of turn order are extreme, manipulating turn order may become a dominant feature of gameplay
* **Bid Turn Order** - Players [[Auction Theory|bid]] for turn order.
	* Allows players to decide the merit of certain turn orders.
	* Can slow down the game.
	* The auction mechanism needs to be integrated into the game.
	* Auctions rely on players understanding the value of what they are bidding on. Miscalculations on the value of a bid affects the player's enjoyment and the balance of the game.
* **Progressive Turn Order** - One player has the First Player token. At the end of the round, the token passes to the next player in the sequence who becomes the new First Player for that round. 
	* Naturally rotates who the first player is in a predictable way, allowing for planning.
	* Being first in a round is immediately followed by being last in the next round.
	* Can leave a large gap between player turns.
	* Games that use Progressive Turn structure are played to the end of the round in which the end-game condition is triggered.
	* A variant of this is a **Regressive** structure where the last player in the current round goes first in the next round. This can give an advantage to last players.
* **Chain Turn Order** - There is an action that may be taken to claim a place in the turn order (typically, but not always, first) for the next round, with play proceeding clockwise from the First Player. If no one takes the action, turn order remains unchanged
	* Gives control with regards to turn order.
	* Requires balancing the cost between giving up an action now to gain advantage later.
	* Players next to the First Player can go second without having to pay a cost (the cost is paid by the First Player playing their action)
	* Need to avoid obviously best moves by players.
	* A variant of this involves multiple players being able to do this. The order for these players is determined by the order they played their Special Action.
* **Pass Order** -  On their turn, players may either take an action or pass. The first player who passes becomes the new first player for the next round. The second player who passes becomes the second player for the next round, and so on. 
	* Reversing pass order and turn order is also possible when going later in turn order is more advantageous.
	* Games in which players are very likely to take an equal number of actions in a round are a poor fit for this mechanism
	* The mechanism works best when turn order preference is strong, when players act many times over the course of a single round, and when there is some hard limit on the total number of actions a player can take
	* Need to consider the ability to track turn order.
	* Need to consider the downtime in performing Pass actions.
* **Real Time** - There are no turns. Players play as quickly as possible, subject to certain constraints, until the game or phase is completed. Playing quickly confers some type of advantage.
	* In a tabletop setting, they need to be short and simple due to cognitive load.
	* Need to address timing issues when players perform conflicting actions.
	* Design needs to address issues of accidental or intentional cheating (if it is [[Games as Rules#Subverting Rules|even a problem]]),
	* Real time is often structured in two phases -- 
		* Action - where real time action occurs
		* Resolution - the results of the Action phase are determined with no time pressure.
	* Real time has two possible phase endings
		* When the end phase condition is met, the phase ends immediately.
		* The Phase end trigger sets up bonus time and informs them that the phase will end soon.
* **Punctuated Real Time** - There are no turns. Players play as quickly as possible, subject to certain constraints, until the game or phase is completed. Play is also interrupted by specific player actions, which are resolved before resuming the real-time action.
	* Adds tension because players do not necessarily see the stoppage of play coming.
	* Allows more complex mechanisms in a real time setting. Also allows games to be longer than pure real time games since the game can pause and players have a breather
* **Simultaneous Action Selection** - Players plan their turn simultaneously and secretly. Then, they reveal their plans at the same time.

# Links
* [[Game Mechanics Design]]
* [[Lenses for Game Design - Notes]]

* [[Building Blocks of Tabletop Game Design - An Encyclopedia of Mechanisms by Engelstein and Shalev]]