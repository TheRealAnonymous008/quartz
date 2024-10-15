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

# Feedback
* *The economy of a game (in particular the dynamics of a particular resources) can be plotted over time* to visualize it better and to discover underlying patterns .

| Negative Feedback                                                                                                                                                     | Positive Feedback                                                                                                   |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| Creates stability                                                                                                                                                     | Creates an arms race                                                                                                |
| Characterized by convergence to an equilibrium                                                                                                                        | Characterized by exponential growth or decay                                                                        |
| Can create a dynamic equilibrium when fed the difference of resources (as in one resource ends up compensating for the lack of another). Allows for balancing as well | Can be used to create deadlocks and dependencies between resources (i.e., one resource depends on another resource) |
| Allows for rubberbanding where players are neither too far ahead or too far behind. Creating excitement                                                               | Can be used to make players win or lose quickly.                                                                    |
| More or less creates an even playing field.                                                                                                                           | Makes it so that one player's advantage snowballs                                                                   |
| Can prolong the game                                                                                                                                                  | Can end the game quickly or destabilize it.                                                                         |
| Magnifies late game successes                                                                                                                                         | Magnifies early game successes                                                                                      |
| Leads to adaptive or goal seeking behavior                                                                                                                                                                       |                                                                                                                     |

* *It is important to consider how short term investments on a particular resources can impact gameplay in the long term.* 

* Feedback loops can be characterized in more detail as follows 
	* *Type* - Positive / Negative 
	* *Effect* - **Constructive / Destructive**. Creates an effect that will help a player win / lose
		* If the feedback is tied to a winning condition it is probably constructive. Otherwise, if it is tied to a losing condition, it is probably destructive. 
	* *Investment* - **High / Low** - many / few resources must be invested to activate the feedback
		* Investment is proportional to the number of resources required to activate the feedback loop (high = more)
	* *Return*  - **High / Low / Insufficient** - the net gain is high / low / negative
		* Return is proportional to the number of resources gained or produced from the feedback loop and in relation to the investment. 
	* *Speed* - **Immediate / Fast / Slow** - the feedback is in effect immediately / after a little time / after a lot of time
		* The speed of a feedback loop is inversely  proportional to the number of actions and elements involved to activate it (more = slower)
	* *Range* - **Short / Long** - the feedback operates directly / indirectly over few / many time steps
		* Feedback loops that consist of many elements have a high range. 
	* *Durability* - **None / Limited / Extended / Permanent** - the feedback only works once / over a short period of time / over a long period of time / permanently.
		* The durability of a feedback loop is usually permanent unless it depends on a limited resource that cannot be obtained (i.e., it depreciates). In such a case, the consumption rate of the resource and the amount lost per time unit determine how durable the loop is/ 
	* *Strength* - an informal indication of the feedback to the impact of the game. 
	* *Determinability* - the strength of a feedback loop may be affected by different factors. 
		* **Deterministic** - given a certain state, the mechanism will always act the same 
		* **Random** - the mechanism depends on random factors. This can affect speed or return (more randomness may mean infrequent return) 
		* **Multiplayer-Dynamic** - the type, strength or effect of the mechanism are affected by direct interaction with other players. 
		* **Strategy** - the type, strength or game effect of the mechanism are affected by the tactical or strategic interactions between players 
		* **Player Skill** - the type, strength or game effect of the mechanism are affected by the player's manual skill in executing the actions.
# Applications 
* Economies can be integrated in the game in a variety of ways, often interacting with other [[Game Mechanics Design|mechanics]]
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

# Case Studies 
* *Power Ups and Collectibles* - they create an internal economy centered around risk and reward.  
	* More valued Collectibles can be tied to high risk. 
	* Some powerups may be needed. Others may not be needed but are still helpful but are risky to obtain. 
	* Powerups lend themselves well to temporary positive feedback loops. 
	* For the return, the risk is balanced by the player skill. 
* *Racing Games* - they can be framed as the players aiming to produce distance.
	* The production rate is influenced by chance, skill, strategy, and quality of the player's vehicle. 
	* Rubber banding allows a "close race" so that players that are behind can catch up. 
* *RPG elements* - the economy consists of skills and other attributes of player characters. 
	* It must contain a positive feedback loop - player characters perform task successfully to increase abilities to increase their chance to perform more tasks successfully. 
	* A negative feedback loop counters the above positive feedback loop. The experience required to level up increases or the number of actions required to gain experience increases.
	* This strategy favors specialization, especially when skills are harder to obtain. 
* *FPS economy* - there is an economy between fighting aggressively and losing health. 
	* Enemies may provide a source for ammo and health. At the same time, shooting constitutes a drain for ammo. 
	* Health and ammo drops may be provided, however their effectiveness depends on player skill. 
* *RTS economy* - harvesting resources in the game constitutes an economy 
	* Most will require that players allocate their harvesters to harvest different resources. 
	* The resources are converted to a building which can be used to create more units and buildings
	* The production of a unit costs resources. However, they can be used offensively or defensively to counter other units. 
	* Technology trees introduce dependency chains but can also serve as an element to a feedback loop (albeit one that requires high investment).

# Links 
* [[Game Mechanics -- Advanced Game Design by Adams and Dormans|Adams and Dormans]] Ch. 4, 6-7
* [[Internal Economy Design Patterns]]

* [[Feedback Loop]] - more on feedback loops. 