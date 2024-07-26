* **Victory Points and Game State** - An event causes the Game State to be evaluated relative to some scoring condition. Players earn points based on how that state matches the condition. There are a variety of score triggers
	* **Scheduled**  - there are predefined intervals for when scoring will happen, and players know when they are approaching
		* A Scheduled trigger is best suited for more strategic games, as it allows for long-term planning
		* If players [[Dynamic Games of Complete Information|know]] exactly when scoring will occur, the final actions leading up to scoring can be subject to over-analysis and game lengthening delays as players attempt to optimize their scores,
	* **Player Action** - players are the ones who trigger scoring.
		* Sometimes this is completely at the discretion of the players
		* sometimes the precise timing falls within a band of possible values
		* Excellent at creating tension but can reward players who simply happened to be in a superior position when scoring occurs
	* **Random** - there are Scoring cards or tokens that are mixed in with other items. When these are drawn, scoring occurs
		* Can be highly strategic or quite tactical, depending on implementation

* **Victory Points from Player Actions** - Players earn points by performing actions.
	* Consider [[Game Economy|Feedback]]. Does the game make it easier or harder to gain more victory points with a set amount of victory points.
		* Negative feedback loops encourage players to plan when they will pivot from building to scoring 
		* Positive feedback loops encourage players to keep up momentum.

* **Temporary and Permanent Victory Points** - Some Victory Points (VPs) are never lost. Others depend on the game state and may be lost if that state changes.
	* This mechanism is typically used in games where the ending condition is a player reaching a certain number of VPs.
	* Gaining permanent VPs is important to help drive the game to a conclusion. If all points are temporary, it encourages players to try to take down the leader and pull them further away from winning, which can lengthen the game
	* Temporary VPs can provide opportunities for players to suddenly catch up or make a comeback.

* **Victory Points as a Resource** - Victory Points (VPs) may be spent as a currency to impact the game state.
	* Apparent in [[Tabletop Mechanics -- Economics|Economy games]] where money represents victory.
	* This forces players to think about valuation and Return on Investment as key drivers in their decisions.
	* People are more likely to spend VPs if they are [[Framing Effect|framed]] as money rather than something abstract.

 * **Hidden and Exposed Victory Points** - VPs may be [[Game Theory - Games|Public or Private Information]]
	 * If the end is [[Dynamic Games of Complete Information|known]], then players will over-analyze and optimize their last turn. 
	 * the points are hidden or if players are not sure what other players can do, through hidden information, this tendency is alleviated.
	 * Having too many hidden bonus points at the end of the game can lead to an unsatisfying play experience

 * **End-Game Bonuses** - Players earn bonus VPs at the end of the game
	 * Gives players more strategic options. 
	 * Bonuses can either be personal (one person) or public (multiple people)
	 * Public goals provide a natural interaction point for players and can be used where there is not as much player interaction through the other mechanisms.
		 * They can also turn puzzles into a [[Tabletop Mechanics -- Game Structure|competitive]] game.
	* Private goals help differentiate players and can give a strong direction to their play
		* It makes it impossible to determine who is winning.
	* Another consideration is how the goals for bonuses are assigned. 
		* If goals are assigned randomly, later in the game, players may luck into points by being randomly dealt a goal that they have already achieved.
		* Thus, prefer early assignment of bonuses or offsetting random goals with penalties for not achieving them.
	* Consider forcing players to choose only certain goals -- those that they are confident they can do.
	* Consider the ratio between points earned during the game and points earned at the end
		* Bonus / End-game centric points mean that players find it difficult to assess their standing.

* **Race** - The winner is the first player to reach the end of a track.
	* When the game ends, a victor is clear.
	* Any game that has players trying to reach a certain target quantity of VPs is, in essence, a race game.

* **Player Elimination** - The winner is the only player remaining in the game.
	* Considered an anti-pattern because elimination means a player will not participate anymore. Downtime is the downside.
	* It can be effectively used in shorter and lighter games that may be played multiple times in rapid succession
	* It can also be effective if the game is interesting to watch, or the player can still win even if they're eliminated (i.e. their team one).

* **Fixed Number of Rounds** - The game ends after a set number of rounds.
	* If possible, a more natural way of tracking the current round is advised (i.e., not using a dedicated token for this)
	* If the players know that this is the final round, it may change their behavior, which may be undesirable.

* **Exhausting Resources** - The game end is triggered by a resource being exhausted. Players can affect the length of the game by how these resources are used.
	* A nice balance between driving the game toward a conclusion and giving the players some control over the pacing
	* This technique is frequently used as a loss condition for cooperative games.

* **Completing Targets** - The game ends after a set number of targets or goals are completed.
	* Gaining accomplishments is thematically more coherent in most cases than exhausting “mission accomplished” tokens.
	* As there is no reason to end the game if you’re not going to win, this type of trigger can lead to over-analysis. Some techniques to mitigate this:
		* Keep information about player standing hidden
		* Give a bonus for triggering the end of a game.

* **Fixed Number of Events** - The game ends after an event occurs a specified number of times.
	* Most closely associated with card decks. A number of special trigger cards are shuffled into the deck. When the last of these is turned up, the game will end
	* This system can add a lot of variability and tension to a game, as players know approximately when it will end, but not exactly
	* The special cards may all happen very early in the game or very late, which creates long stretches with no scoring. A counter to this is to incorporate a mechanism to ensure the special cards are well distributed.

* **Elapsed Real Time** -The game ends after a set amount of actual time has elapsed.
	* Players know exactly how long the game will take, which helps them schedule and plan and which adds tension
	* This mechanism needs extra attention when used in competitive games since players can stall time, meaning other players have less time to move. Some measures
		* Everyone loses when time runs out
		* Simultaneous play
		* Individual timers

* **Connections** - The game ends when a specified number of connections are made on the board.
	* Analogous to [[Bridge and Chain Drawing Puzzles]]. 
	* Connection games need to deal with  [[topology]] issues relating to the game board.
	* Can players cross paths with other players? Often if this is not allowed, there is an optimal strategy.

* **Circuit Breaker / Sudden Death** - The game has a fixed and known victory condition and a special variable condition that ends the game prematurely.
	* They can help end a game once one player is far in front. This is called a **Circuit Breaker**. 
	* This ends a lopsided game quickly without having the losing side play an obviously lost game.
	* This can be an alternative victory route which introduces more strategic options.

* **Finale** - When the main game ends, a special mini-game is played to determine the victor.
	* It transitions to an alternate play mode at the end
	* This mechanism makes it clear to players what they need to do during the game to win and adds an exciting end-game element
	* It can also cheapen the meaning of the first part of the game, as a player may dominate the main game but still lose the finale.
	* It is more suitable for lighter and quicker games.

* **King of the Hill** - Players earn points by occupying a special position on the board.
	* A simple victory condition to understand.
	* It forces players into conflict. It discourages turtling and staying idle.
	* Battles are more casual since players can rebuild if they are weaker and strike again.
	* It leads to a Catch the Leader mechanism.

* **Catch the Leader** - The game systems advantage players that are behind or disadvantage players that are ahead.
	* If it is too strong, it can be advantageous for players to stay back to make a strong late move rather than be penalized earlier.
	* If it is too weak, the player in the lead can go further ahead. 

* **Tug of War** - A marker is moved up and back on a track toward or away from a neutral position.
	* The location of the marker can also award points or abilities at certain times
	* Easy to understand.
	* When used in an end-game, it is used as sudden death.
	* An inherent dynamic of this is that when one player moves closer to victory, the other moves further away.

* **Highest Lowest** - Each player’s score is equal to the lowest value of several categories. Whoever has the highest lowest value is the winner.
	* It forces players to pursue multiple paths equally rather than specialize.

* **Ordering** - The objective of the game is to rearrange a group of game elements from a disordered to an ordered state.
	* It is simple and has a clear goal.
	* It has many possible starting positions. However, note that depending on the rules, not all of them may have a solution.
	* It is more puzzle-like and more appropriate for cooperative games.
# Links
* [[Building Blocks of Tabletop Game Design - An Encyclopedia of Mechanisms by Engelstein and Shalev]] - Ch. 5