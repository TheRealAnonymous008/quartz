* The goal of the player is to win by planning against one or more opponents. *The main challenge is presented as strategic conflict challenges.*
* Most strategy games are [[Warfare|War games]] or analogues of it. The focus can be:
	* Explicit warfare and combat. In particular, this also includes replicating classic military situations and tactics (imaginary or otherwise)
	* Exploration and Conquest 
	* Survival (i.e., tower defense games)
	* Logistics
	* Diplomacy
	* Economy 
	* Espionage
	* Crisis Management

* Typically, the focus is less on: 
	* Physical coordination and actions
	* Random Chance - in particular, randomness should be away from the point of the strategic decision making as much as possible. This [[The Fundamentals of Game Design|allows players to react and have control over their choices]]. 
	* Asymmetry - in particular for competitive multiplayer games. 

* *The best way to design a strategy game is to start from board games*.
* [RTS Games are fundamentally games about multitasking](https://www.youtube.com/watch?v=Rl4myN8q_KM)
	* Features such as control groups and delayed timers help facilitate multitasking.
	* Build orders in RTS games are analogous to Chess openings.
	* Strategies in an RTS game can be broadly categorized into three. Each strategy counters other strategy in a broad sense. *Mixing and Adapting [[Game Theory|strategies]] is another core skill*, 
		* **Aggression** - *attack the enemy.* Counters Economy if there is no Defense
		* **Defense** - *protect your base*.  Counters Aggression because defending typically has a force multiplier
		* **Economy** - *accelerate your economy to outpace the enemy.*  Counters Defense because you can outpace the enemy to the point their investments in defense become obsolete.

## Design Considerations
* *One consideration in the design of strategy games is the time horizon -- whether to use real time or turn based or a mix of both*
	* Turn-based games focus more on the strategic decisions of the players [^turnbased]
	* Real time strategy games add time pressure. Players need to also react and adapt quickly.

* We should also characterize the units the player has access to.
	* Not all units fight. Some can have transport, logistics, or support roles
	* Not all units move.
	* Some units (buildings) are used to produce new fighting units. 
	* Units can either be atomic or composite (i.e., modular and with a lot of parts)
	* Units behave according to particular performance characteristics.
	* All war games offer the player a choice of different kinds of units. 
	* Other tactical dimensions to consider:
		* Stealth. [^stealth]
		* Flying or sailing (or amphibious movement)
		* Repair
		* Transport
		* Producing mobile units
		* Leadership (i.e., a special unit that buffs others or debuffs them if they are killed)
	* *Do not make invincible units*. As a rule, avoid designing any unit whose range and speed are greater than the range and speed of any enemy unit it may face. 
	* When creating a specialized unit for one side, *the other side must have a response or an equally good option.* Too much asymmetry will ruin game balance.
	* *A unit's cost should be a function of its military value*. This is another tool that can be used for balancing the military effectiveness. *Units with special abilities should cost more than a similar unit without that ability*. 

[^turnbased]: Simultaneous turn-based games are interesting.

* *The range of tactics available to the player is dependent on the [[Games as Rules|rules]] and units available to the player*. 
* AIs that aim to mimic the player, not only have to be able to exploit similar strategies, but also be subject to the same limitations as the player (i.e., AI that doesn't cheat)
* Long term strategies typically encompass elements such as diplomacy and economy. Still, *strategy games tend to reward aggressive play because they are more exciting*

* Another consideration is the role of exploration. *Almost all strategy games feature fog of war* which indicates uncharted territory (somewhat unrealistic if the area should be familiar), unpatrolled territory, and clearly visible regions
	* Fog of war adds an element of realism because without it the player is omniscient.
	* Fog of war adds encourages a dynamic that rewards both scouting for enemies and guarding home territory.
	* Fog of war enables tactical options such as flanking
	* *AI that cheats by being exempt to fog of war is a symptom of (or a design solution for) weak AI*

* Typically, either a rock-paper-scissors dynamic is designed into the game, or it (should) naturally emerge to avoid having [[Game Theory|Dominant strategies]]. 
	* The rock paper scissors dynamic adds another strategic layer where the player must anticipate the opponent's actions. However, for complex games, this is not baked into the design explicitly.
	* *Favor combat effectiveness that emerges as a result of unit attributes*. 
	* Accuracy and Dodge mechanics (chance to miss) introduce random chance to the game.
* How units move is also another aspect to consideration.
	* We can account for difficulty in moving across various terrain and slopes. 
	* We can account for size and density of the unit.
	* Consider how fast units can turn. If they can turn too fast, then flanking maneuvers will be less effective.
* *The player's role is typically a commander or manager*. The most common orders that can be issued are
	* *Move* to a given location (or following a set path).
	* *Attack* an enemy unit. This includes advancing and optionally pursuing
	* *Stop* attacking or moving.
	* *Hold* a position. Attack an enemy but do not pursue it if it retreats.
	* Establish a *Formation*. 
	* *Produce* a unit. 
	* *Retreat* towards safety.
	* *Dash* to a destination while avoiding enemies
	* *Patrol* a given route defined by waypoints.

* *Progression mechanics in strategy games are rare*. They tend to be emergent, although single player campaigns may have scripts. 

* *Strategy games require balance to be fun to play*
	* A game's [[Game Mechanics Design|economy]] is important to consider -- what resources are available and how are they spent. 
		* If resources are infinite, the game can, in principle, go on forever.
		* If resources are placed in the landscape, one dominant strategy to look out for is **resource rushes** where players monopolize these resources. The fix if this is not the intent is to *make economic opportunities symmetrical*. 
	* *Another dominant strategy to look out for is concentrated firepower*. This can happen as a result of unbalanced production rates. 
	* *Reducing combat effectiveness over time introduces [[System Dynamics|a positive feedback loop]]* which can result in the weaker side losing too quickly (or a stalemate if both sides are weak)
* *Adding a tech tree and upgrade systems introduce a delay* so that players are not introduced to the more powerful units early on. 
	* In a highly representational wargame, upgrades need not apply to entire unit families immediately. We may require the player to upgrade them individually. 
	* Permanent upgrades are ideal for long term strategy. Short term upgrades give huge temporary bonuses that are not sustainable long term.
	* Tech trees can encourage asymmetric play by forcing players to commit to a specific branch in the tree. However, this might take player agency away if they do not know what is at the end of the tree, and it makes the game tricky to balance.
	* *Do not restrict upgrades entirely and arbitrarily.* Instead, either give the players either the ability to set these up (i.e., for a multiplayer game), or introduce elements in the level that make certain upgrades not worthwhile. 
	* *Upgrades should strengthen the player's side and give the player new choices to make*.
	* Abstracting away the distribution process permits the unrealistic strategy of building outputs that would "realistically" not be viable because they would be unsupplied.

* *Logistics is largely simplified in war games*, especially since one person manages all of it. 
	* Most games ignore the human needs of the soldiers (food, sleep, etc).
	* Regarding ammunition -- if ammunition is cheap, doesn't do much damage, and is quickly expended, give units an unlimited supply. *Don't sweat the small stuff*.
	* Implementing supply lines realistically means modeling supplies as individual objects and creating transport units for this purpose (which can be tedious and expensive for the game engine).
	* *One strategy to still include logistics is to make the production process concrete but the distribution process abstract*
		* Another strategy is to use roads or supply wagons. Units must be near these to be continually effective 
		* Another strategy is to assume any unit within range of a supply depot can receive supply even if the depot is completely cut off. This is the approach of **influence maps**

[^stealth]: Typically, we balance this by having units move out of stealth when they attack. Otherwise, stealthy units become too powerful.

* *When making the world, consider the scale*. In particular, matters like movement speed are important.

* Because of their complex underlying systems, we need to consider the [[UX Design Principles|User Experience]]. 
	* The interface must present complicated information in a clear, organized way
	* This also ties with scope. Controlling more units directly = units are depersonalized.
	* *Players of strategy games need to be able to see the big picture*. Thus, favor some form of aerial / top-down perspective. 
	* Assuming the UI is presented as a windowed application, make all widgets intuitive and clear. Unavailable actions should be clearly indicated (visible but dimmed)
	* *Inexperienced players need clear and easy ways to find commands; Advanced players require quick access (i.e., keyboard shortcuts)*
	* Ensure the game presents commands grouped by function.

* Some AI approaches to consider
	* *Game Trees*. This will typically be reserved for simple games due to the exponential time search.
	* [[Neural Network]]. This will require training and proper characterization of the environment.
	* *Hierarchical [[Finite Automata and Regular Languages|Finite State Machine]]*. This allows for simple rules that lead to emergent behavior. The disadvantage is that units can typically only be in one state at a time.
* As a rule, *AI should not micromanage the troops. The troops should, instead, have intelligent behavior laid out in hierarchical fashion*
# Games
* [Beyond All Reason](beyondallreason.info) - an open source RTS. Some interesting features of the game that stand out:
	* There is an emphasis on teamwork in multiplayer. Players will typically assign themselves roles.
	* Like chess, has its own standard set of openings / build orders. This is somewhat inevitable considering the "meta'".
	* Simplified economy which makes the focus more oriented towards holding key areas 
	* One viable strategy is rushing up the tech tree.
# Links
* [[Fundamentals of __ Game Design Series by Ernest Adams]]

* [[Economics]] - more on what to consider when simulating economies.
* [[Algorithms in Games]]
