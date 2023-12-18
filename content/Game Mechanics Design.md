* At their core, [[The Fundamentals of Game Design|games should be unpredictable for them to be engaging]]. This can be achieved either using randomness, using the [[Game Theory|dynamic nature of player choice]], or through complex gameplay via its mechanics.
* The **mechanics** of a game pertain not just to the formal systems underlying it, but the mechanisms by which the game operates -- in other words, the specifics of how to code it. 
	* A **core mechanic** in this context means a mechanic that underlies a vast majority of the game's systems in some way
	* *The mechanics of a game can be implemented through many different media*. Hence, if it can be done on paper, [[Lenses for the Process|do so]].
	* There are five kinds of mechanics 
		* **Physics** - the [[Physics|science]] of motion, temporality, and force in the game world. 
		* **Internal Economy** - The mechanics of [[Economics|transactions]] involving game elements (both concrete and abstract resources) that are collected, consumed, and traded.
		* **Progression Mechanisms** - the mechanisms involved in [[Level Design Principles|level design]] that indicate how a player will progress through the game 
			* *Example*: Any new movement mechanic in a metroidvania. 
		* **Tactical Maneuvering** - mechanics involving the placement of game units on a map for offensive or defensive advantages. 
		* **Social Interaction** - [[Games as Play#Social Play|the mechanisms]] that allow players to interact with one another 
			* *Example*: Giving gifts.
	* Mechanics can also be discrete or continuous. 

![[Game Mechanics.png]]
<figcaption> Game Mechanics. Image taken from Adamss and Dormans</figcaption>

* It is important to distinguish the structural differences between mechanics of progression and emergence. *Games tend to have a mix of both*. 
  
| Structure                         | Emergence              | Progression                 |
| --------------------------------- | ---------------------- | --------------------------- |
| Number of Rules                   | Low                    | High                        |
| Number of Game Elements           | High                   | Low                         |
| Interactions between Elements     | High                   | Low                         |
| Possibility Space                 | Large and Wide         | Small and Deep              |
| Replay value                      | High                   | Low                         |
| Designer control of Game sequence | Low (due to emergence) | High (due to level design ) |
| Length                            | Tends to be short      | Tends to be long            |
| Learning curve                    | Steep                  | Gentle                      |

* *Mechanics don't have to be realistic, only consistent*.  Remember, all games have some form of recognizable patterns inside them and the mechanics should be one of these patterns 
# Mechanics 
## Physics
* Mechanics based on physics require understanding the underlying game  engine's physics simulation. 
* They usually cannot be (conveniently) prototyped via a board game, especially if they operate on a continuous space.
* Once players grasp the physics of a game, they can intuitively predict movements and results, but with less certainty. *Skill and dexterity become a more important aspect of the interaction*
* However, *physics also implicitly lends itself to discrete mechanics*. In particular, by allowing the players to formulate a strategy that can be described without knowledge of the underlying physical computations.
* *It is hard to innovate with physics mechanics*. 

## Economy 
* An economy consists of a set of basic elements 
	* **Resources** - any concept that can be measured numerically. Anything that the players can produce, gather, collect or destroy. 
		* **Tangible resources** - have physical properties in the game world. They exist in a particular location and have to be moved somewhere else. 
		* **Intangible resources** - have no physical properties in the game world. They do not occupy a space or exist in a particular location. These are just numbers.
		* **Abstract resources** - do not really exist in game but are computed from the current state of the game (i.e., a strategic advantage). They are mainly used for internal computation.
		* **Concrete resources** - really do exist in the game which the players can experience or interact with. 
	* **Entities** - where specific quantities of a resource are stored (i.e., a [[Programming|variable]]). 
		* **Simple entities** - store only one value. 
		* **Compound entities** - groups of related simple entities called attributes. 
	* **Economic functions** - functions that affect resources that move them around. 
		* **Sources** - mechanics that, under certain conditions, create new resources out of nothing and store them in an entity
		* **Drains** - mechanics that, under certain conditions, take resources out of the game, reducing the amount stored in an entity. 
		* **Converters** - mechanics that turn resources from one kind to another (destroying one and creating another)
		* **Traders** - mechanics that move a resource from one entity to another, and another resource back in the opposite direction according to an exchange rules. 
		* Sources and drains share similar properties:
			* They may be triggered by events in the game, or may operate continuously based on a production or consumption rate. 
			* They may also be toggled on or off

* *The economy of a game (in particular the dynamics of a particular resources) can be plotted over time* to visualize it better and to discover underlying patterns .
	* **Negative Feedback** - used to create *stability* in a dynamic systems. It creates equilibrium where the system stabilizes towards. The equilibrium is not necessarily fixed.
		* It can create a dynamic equilibrium when it is fed the difference of resources (i.e., one resource will end up compensating for the lack of another).  This allows for balancing as well. 
		* It can also allow for rubberbanding where players are neither too far ahead or too far behind, creating excitement. 
		* In play, players tend to be more or less on an even playing field.
		* They can prolong the game.
		* They magnify late game successes.
		* It leads to adaptive or goal seeking behavior. 
	* **Positive Feedback** -  used to create an *arms race*. It is characterized by an exponential curve in the economy. 
		* They can also be used to create deadlocks and mutual dependencies between resources. 
		* They can also be used to make a player win or lose quickly once a critical difference is created. 
		* They tend to destabilize the game.
		* They magnify early successes via snowballing.
	* *It is important to consider how short term investments on a particular resources can impact gameplay in the long term.* 

* Economies can be integrated in the game in a variety of ways. 
	* *Use it to complement physics* (skillfully performing physical actions gives you a resource). The physics system may also invoke risk and reward for the player. 
	* *Use it to influence progression*. Acquiring or removing certain resources may facilitate further progress into the game level or introduce new opportunities for exploration. 
		* Just make sure to not cause a deadlock in this case by making the resources required for progression immediately available. 
	* *Use it to add strategic gameplay*. Economies allow for reward planning and long-term investments.  Complex economies can sustain complex strategic behaviors. 
	* *Use it to create a large possibility space*. More complex economies lend themselves to larger posssibility spaces and more replay value.  Keep in mind the following 
		* If a particular combination of items and skills is more efficient than others, *players will choose only that option* and the economy will be thrown off balance. 
		* You have to be sure that the *possibility space is large enough* that player does not end up exploring it entirely in one play session.
			* Consider having choices that exclude each other to make them feel like they have real consequences. 
		* Design the levels in such a way that players *can use different strategies* to complete them. 

* Some tips for making games where the player builds an economy and keep the complexity under control 
	* Don't introduce all the player's building blocks at once. *Gently introduce players to the different game elements*. Lock advanced elements behind progression mechanics. 
	* *Be aware of the meta-economic structure.* Keep in mind that certain approaches are better than others. 
		* One way to balance this is to make structures that are effective in the early game be less effective in the late game.  Use slow-working, destructive positive feedback. 
	* Use maps to produce variety and constrain the possibility space.

## Mechanics of Emergence 
* [[Complex Systems|Emergence]] allows designers to create games which offers more player opportunities. 
* *These make good use of the computer's ability to do many processes*. 
* Games may have breadth (many possible choices) or depth (many possible outcomes as a result of subsequent actions).
* *Even relatively simple mechanics gives many gameplay opportunities*. The emergent properties arise from the mechanics interacting with each other. 
	* These opportunities give rise to new player strategies. 
* They have a *high replay value* because the challenges and possible actions that occur while playing are different every time
* *Emergent gameplay mechanics should be a balance between ordered (progression) mechanics and randomness*.
* The structural qualities of the game -- the presence of feedback loops, interconnected parts, and differing scales of complexity, determine emergent gameplay. 

## Progression 
* A game of progression requires a large amount of data, prepared in advance by the designer, that the player can access at arbitrary points
* They offer many predesigned challenges that the designer has ordered sequentially via level design. 
* These are suited for games that tell [[Narrative|stories]]. 
* They also allow the designers to arrange the levels in such a way a tutorial would meaningfully explain the mechanics of the game without overwhelming the player. 
* One challenge is **railroading** where a player feels like they are guided through the game instead of making their own choices. *Balancing between offering and restricting freedom is necessary*
* They typically have many rules but they do not interact with each other as much.

# Links 
* [[Game Mechanics -- Advanced Game Design by Adams and Dormans]]

* [[Games as Rules]]
* [[Lenses for the Game]]
* [[Models for Game Rules]]