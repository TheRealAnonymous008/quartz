* *Intent*: A drain automatically consumes resources produced by the player; the consumption rate is affected by the state of other elements in the game.
* *Motivation*: It counteracts production mechanisms but adapts to player performance. 
# Applicability 
* You want to balance games in which resources are produced too fast 
* You want to create a mechanism that counters production and automatically scales with player progress 
* You want to reduce the effectiveness of long-term strategies in favor of short-term strategies. 

# Participants 

![[Dynamic Friction.png]]
<figcaption> Dynamic Friction. Image taken from Adams and Dormans </figcaption>

* The production mechanism produces energy that the player needs for actions. 
* The dynamic drain consumes energy outside players' direct control but is affected by the state of at least one other element in the game system . 

# Considerations 
* It counters positive feedback and adds a negative feedback system. 
* It expands upon a [[Static Friction]]. 
* The element that causes the consumption rate to change could either be 
	* The amount of energy. This tends to cause a fast-acting negative feedback loop. 
	* The number of upgrades to a [[Dynamic Engine]] or [[Converter Engine]] system.  This tends to cause an indirect and slower-acting feedback loop. 
	* The player's progress towards a goal.  This tends to cause an indirect and slower-acting feedback loop. 

* We usually use fast positive feedback and slow negative feedback. 