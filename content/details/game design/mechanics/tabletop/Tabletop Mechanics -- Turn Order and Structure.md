* **Fixed Turn Order** - Turn order is set at the start of the game and never varies. Each player takes a turn in the same sequence until the end of the game.
	* Often results in an imbalance favoring the players going first. This imbalance can be offset by giving bonuses to the players behind in turn order
	* All players should have an equal number of turns
	* [[Dynamic Games of Incomplete Information|Knowledge about when the game ends]] can be used to meta-game.

* **Stat Turn Order** - The turn order within each Round is set by some statistic relating to the players’ resources or position in the game.
	* If players who are ahead on the score track during the game are penalized by turn order, it will give increased weight to strategies that maximize end-game points
	* When the advantages of turn order are extreme, manipulating turn order may become a dominant feature of gameplay

* **Bid Turn Order** - Players [[Tabletop Mechanics -- Auctions|bid]] for turn order.
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

* **Simultaneous Action Selection** - Players plan their turn simultaneously and secretly. Then, they reveal their plans at the same time. Actions are typically resolved in turn order. 
	* This mechanism gives players the opportunity to try to anticipate what their opponents will do and to plan accordingly
	* It can speed up games and reduce downtime because players are acting simultaneously.
	* Gives increased strategic depth.

* **Role Order** - Players secretly and simultaneously select an action, role, or priority. Then they are revealed, and the actions/roles revealed determine the order in which players act.
	* Role Order allows the designers to control the order in which operations occur, while giving players a choice about which of those will happen
	* Introduces a well-defined turn order that doesn’t suffer from needing to have a mechanism to shift the first player

* **Random Turn Order** - Representatives of play pieces or players are randomized and one is drawn at a time. That player or play piece takes its turn, and then a new random draw is made
	* The randomization adds excitement and tension, but at the cost of reducing the power of planning.
	* Not suitable for games that require heavy tactical depth.
	* Balancing games with this revolves around giving players more choices (i.e. forfeit now to have a benefit later, or turns corresponding to unit categories than players)

* **Action Timer** - Players place owned timers on action spaces and pieces and take an action. When the timer runs out, it may be moved to another location to take that action. There are no turns; players may move their own timers any time after they have expired.
	* Allows for a real-time feel without the frantic nature. 
	* The game flows naturally. Players have breathing room for planning.
	* Can feel sluggish at points when players have to wait to take their actions. Typically mitigated by allowing multiple timers (and multiple actions)
	* Timers can have varying durations.

* **Time Track** - There is a linear “Time Track” with many spaces. Each player has a marker on the track, which indicates where they are “in time.” Markers farther on the track are further forward in time.
	* The player with the marker lowest on the track (furthest “back in time”) takes the next action. Each action has a cost in time, and the player’s marker is advanced a number of spaces according to that cost. Then, the next lowest marker on the track takes an action. 
	* It is possible that the same player takes multiple turns in a row.
	* This has advantages:
		* It is clear who goes next even as turn order changes
		* Players have some choice over who goes next.
		* Actions can be balanced by having powerful actions take longer.
	* This has downsides
		* Players can have too much downtime if other players take multiple turns or if they take long-duration actions
		* Ties need to be resolved in such a way that the game remains balanced.

* **Passed Action Token** - Players possess one or more Action Tokens. Those who have an Action Token may take a turn, and then they pass the token clockwise, allowing the next player to perform an action.
	* Typically, to prevent stalling and to keep the game moving, in games with multiple Action Tokens, if both tokens are held by the same player, they suffer a penalty.
	* Mix between real-time and turn-based 
	* Players go one at a time (turn based) but perform actions in real time.
	* It encourages faster play, but faster players don't necessarily win.

* **Interleaved Phase Structure** - all players perform the first phase, then all perform the second phase, and so on. 
	* Preferred to reduce downtime compared to Sequential Phase Structures

* **Sequential Phase Structure** - each player performs all phases before moving to the next player/
	* Can have high downtime as players wait for other players to finish their turn
	* Can offer more strategic options since players can act before other players can respond.

* **Lose a Turn** - a player who "Loses a turn" must skip their next opportunity for a turn. 
	* Considered an anti-pattern because it can remove player agency and increase downtime. Players cannot play the game if they lose their turn
	* Can become a pattern if Losing a Turn can actually offer an advantage in some cases. This requires players have control when they lose a turn or they lose the turn as a result of their actions.
	* Can emerge as a result of other mechanisms (even if no explicit Lose a Turn rule is mentioned)

* **Interrupts** - Players take an action that interrupts the normal flow.
	* Interrupts can keep players engaged as they must find the perfect opportunity to play their interrupt
	* Interrupts can reduce downtime.
	* They can add uncertainty to the game and remove perfect plans. This is good or bad depending on the goal of the design.
	* They tend to favor experienced players as they know what to respond to against their opponent.
	* Requires mechanisms to facilitate and arbitrate.
	* If multiple interrupts are present, need to establish how to resolve them.
	* Interrupts may change turn order or even cause someone to lose a turn.

# Links
* [[Building Blocks of Tabletop Game Design - An Encyclopedia of Mechanisms by Engelstein and Shalev]] - Ch. 2