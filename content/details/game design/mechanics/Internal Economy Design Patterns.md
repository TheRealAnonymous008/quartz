* These design patterns can be combined with each other, often even driving entire game genres. 
* Patterns can be **elaborated** that is, made more complex to add more complexity and meaningfulness to the game.  
* Additionally, patterns can be **simplified** to either understand the complex design better or to remove unwanted  complexity entirely (especially for mechanics that are not the focus) 
* *The goal of these design patterns is to understand gameplay mechanics, and in particular what can make them interesting*. 
* These design patterns can be applied both in the micro and macro scale. 
# Engines 
* Generate resources that may be required by other mechanisms in the game. It represents gain.

## Static Engine 
* *Intent*: Produces a steady flow of resources over time for players to consume or to collect while playing the game.
* *Motivation*: Creates a steady flow of resources that never dries up 

### Applicability
* You want to limit players’ actions without complicating the design. A static engine forces players to think how they are going to spend their resources without much need for long-term planning.

### Participants 

![[Static Engine.png|300]]
<figcaption> Static Engine. Image taken from Adams and Dormans </figcaption>

* The source produces energy at a fixed or unpredictable rate 
### Considerations
* The production rate does not change. Its effects on game balance are predictable. 
* Can cause imbalance only when its production rate is not the same for all players 
* Generally doesn't inspire long term strategies. Resource collection is quite obvious 

* *Increase unpredictability to encourage the players to plan*. This can be achieved by 
	* Using a varying production rate 
	* Varying the output level of resources 
	* Varying the length of time between moments of production 
	* Using skill or multiplayer dynamics 

## Dynamic Engine 
* *Intent*: A source produces an adjustable flow of resources. Players can invest resources to improve the flow.
* *Motivation*: A dynamic engine produces a steady flow of resources and opens the possibility for long-term investment by allowing the player to spend resources to improve production. The core of a dynamic engine is a positive constructive feedback loop.

### Applicability 
* You want to introduce a [[Trade Offs|trade off]] between short term goals and long-term investment. 
* You want the player to be be able to control the production rate more so than a regular [[#Static Engine]]

### Participants 

![[Dynamic Engine.png|300]]
<figcaption> Dynamic Engine. Image taken from Adams and Dormans </figcaption>

* Energy is produced and consumed by an action. Optionally, we can invest to produce upgrades that will improve the energy output of the engine. 
* Upgrades can either be for 
	* the production rate  - higher = steadier flow of energy 
	* the number of energy units produced - higher = bursts of energy 

### Considerations
* Requires balancing the feedback loop using a negative feedback loop.
* Requires considerations as to not creating a dominant strategy where either long-term or short-term strategy is strongly favored. This can be balanced by using an appropriate [[Game Theory - Games|discounting factor]] that indicates long term investment has diminishing returns 
* Characterized by players investing first and then beyond a certain point, the player will make more progress and try to do so at the quickest pace. 
 
* The positive feedback loop amplifies early wins which can lead to instability.  This can be balanced out by stabilizing the production rate. 
* *Upgrades can be converted back to energy* but at a lower rate than the original investment. This becomes viable when upgrades are expensive and there is a frequent need for large amounts of energy. 

## Converter Engine 
* *Intent*: Two converters are set up in a loop to create a surplus of resources that can be used elsewhere
* *Motivation* Two resources that can be converted into each other fuel a feedback loop that produces a surplus of resources. At least one of the converters must output more resources than it takes in to create the surplus. 

### Applicability
* You want to create a more complex mechanism to provide the player with more resources than a [[#Static Engine]] or a [[#Dynamic Engine]]. 
* It increases game difficulty since the feedback loop must be maintained. 
* You need multiple options and mechanics to tune the profile of the feedback loop that drives the engine and thereby the stream of resources that flow into the game.

### Participants 

![[Converter Engine.png|300]]
<figcaption> Converter Engine. Image taken from Adams and Dormans </figcaption>

* The converters change energy into fuel and fuel into energy. The net result is a surplus of energy 

### Considerations
* The converter engine is a more complicated mechanism than most other engines but also offers more opportunities to improve the engine. As a result, a converter engine is nearly always dynamic.
* *Introduces the possibility of deadlock* -- where both resources dry and the engine stops working. Players may also accidentally create these deadlocks. 
* The feedback loop present needs to be balanced appropriately

* Fix deadlocks by using a weak [[#Static Engine]] as a constant source.
* *More steps involved in the feedback loop means more difficulty in maintaining the loop but also more opportunities for tuning the engine*.
	* If there are two few steps to begin with, just use a dynamic engine 
	* If there are too many steps, the system becomes too difficult to maintain. 
* Introduce unpredictability for more interesting scenarios but beware this increases the risk of deadlock. 
* *Put a limiter in the cycle*. This keeps the engine under control and the surplus in acceptable ranges. 


## Engine Building
* *Intent*: A significant portion of gameplay is dedicated to building up and tuning an engine to create a steady flow of resources.
* *Motivation*: The game should offer multiple mechanics to improve the design of the engine. 

### Applicability
* You want to create a game that has a strong focus on building and construction 
* You want the game to focus on long-term strategy and planning 

### Participants 

![[Engine Building.png]]
<figcaption> Engine Building. Image taken from Adams and Dormans </figcaption>

* The building mechanisms increase the output of the core engine (which can be any engine)
* If energy is required to activate building mechanisms, then a positive, constructive feedback loop is created.

### Considerations
* Best suited for games with high intended difficulty or those that are slower paced / focus on strategy. 

* It should be difficult to assess the engine's state. 
* Introduce unpredictability to increase difficulty, variety, and the size of the strategy space.  The core engine's complexity also introduces unpredictability. 
* Spread the process of engine building over the entire game. 

* It can *operate without feedback* when energy is not required for the building mechanisms. This gives the player more strategy over which resources to prioritize, however the building mechanisms should be restricted in some way. 
* Has more upgrades than a [[#Dynamic Engine]]

# Friction 
* Drains resources from the economy, reduces its productivity or both. It represents loss 

## Static Friction 
* *Intent*: A drain automatically consumes resources produced by the player.
* *Motivation*: It counters a production mechanism by periodically consuming resources. 

### Applicability
* You want to create a mechanism that counters production but can eventually be overcome by the players 
* You want to exaggerate the long-term benefits from investing in upgrades for a [[#Dynamic Engine]].

### Participants 

![[Static Friction.png|300]]
<figcaption> Static Friction. Image taken from Adams and Dormans </figcaption>

* The production mechanism produces energy that players need to use to perform action. It does so outside of the players' direct control. 

### Considerations
* It is a simple way to counter an engine pattern. However, it tends to emphasize long term strategies since it does not affect any countermeasures such as upgrades (from dynamic engines) 

* Consumption rate can be fixed or random.  When it is fixed, it is more predictable.
* Random consumption rates can be a good alternative to random production rates. 
* When there is a continual loss of energy, the system's dynamics is less strong. Whereas, if there is a periodic loss (at irregular intervals), the system becomes more unstable. 

## Dynamic Friction 
* *Intent*: A drain automatically consumes resources produced by the player; the consumption rate is affected by the state of other elements in the game.
* *Motivation*: It counteracts production mechanisms but adapts to player performance. 

### Applicability 
* You want to balance games in which resources are produced too fast 
* You want to create a mechanism that counters production and automatically scales with player progress 
* You want to reduce the effectiveness of long-term strategies in favor of short-term strategies. 

### Participants 

![[Dynamic Friction.png]]
<figcaption> Dynamic Friction. Image taken from Adams and Dormans </figcaption>

* The production mechanism produces energy that the player needs for actions. 
* The dynamic drain consumes energy outside players' direct control but is affected by the state of at least one other element in the game system . 

### Considerations 
* It counters positive feedback and adds a negative feedback system. 
* It expands upon a [[#Static Friction]]. 
* The element that causes the consumption rate to change could either be 
	* The amount of energy. This tends to cause a fast-acting negative feedback loop. 
	* The number of upgrades to a [[#Dynamic Engine]] or [[#Converter Engine]] system.  This tends to cause an indirect and slower-acting feedback loop. 
	* The player's progress towards a goal.  This tends to cause an indirect and slower-acting feedback loop. 

* We usually use fast positive feedback and slow negative feedback. 
## Stopping Mechanism 
* *Intent*: Reduce the effectiveness of a mechanism every time it is activated.
* *Motivation*: Prevent the player from abusing a powerful mechanism by virtue of the Law of Diminishing returns. 

### Applicability 
* You want to prevent players from abusing particular actions 
* You want to counter dominant strategies 
* You want to reduce the effectiveness of a positive feedback mechanism 

### Participants 

![[Stopping Mechanism.png]]
<figcaption> Stopping Mechanism Image taken from Adams and Dormans </figcaption>

* An action must have an energy cost, produce a resource or both. The stopping mechanism reduces the effectiveness of an action mechanism every time it is activating by increasing costs or reducing the output of resources. 

### Considerations
* It reduces the effect of a positive feedback loop considerably and even make its return insufficient. 

* It is sometimes permanent but usually not.
	* When the accumulated output is used to measure the strength of the stopping mechanism, the effects are not permanent. 
	* Non-permanent stopping mechanisms mean players have to alternate between using actions. 
* If the stopping mechanism can apply to multiple players, the game will reward players that can use the action first. 

## Attrition 
* *Intent*: Players actively steal or destroy resources of other players that they need for other actions in the game.
* *Motivation*: By allowing players to directly steal or destroy each other’s resources, players can eliminate each other in a struggle for dominance.

### Applicability
* You want to allow direct and strategic interaction between multiple players.
* You want to introduce feedback into a system whose nature is determined by the strategic preferences and/or whims of the players.

### Participants 

![[Attrition.png]]
<figcaption> Attrition. Image taken from Adams and Dormans </figcaption>

* By performing attack actions, players can drain each other's strength. It may or may not also cost strength to perform. 
* If the attack doesn't cost strength, it must involve something to offset the advantage (for example skill or randomness). 

### Considerations
* The dominance resulting from attrition is dependent on a balance between attack costs, effectiveness, and how beneficial other actions in the game are. 
* Makes the system more dynamic and can introduce destructive feedback. Players may be stimulated to either attack stronger or weaker players. 

* Players should be required to invest some resource in attacking that could also be spent elsewhere. Otherwise, the game becomes a race with no strategic choice. 
* Attacks without investment works better in social games because players need to choose whom to attack.
* Commonly implemented with "life" and "energy" . But these two must be related. 
* Other actions (that are not attacking) typically constitute a production mechanism for strength. 

* When there is a bonus for attacking or eliminating players, the pattern can be made to stimulate the elimination of weaker players.

* It elaborates the [[#Dynamic Friction]] pattern. 

# Escalation 
* Put pressure on the player to deal with growing challenges.

## Escalating Challenge 
* *Intent*: Progress toward a goal increases the difficulty of further progression.
* *Motivation*: It makes it harder for players as they get closer to achieving their goals. The game adapts to the player's skill level, especially when good performance would allow the player to progress more quickly.

### Applicability
* You want to create a fast paced game based on player skill in which the game gets harder as the player advances.  
* You want to create emergent mechanics that partially replace predesigned level progression. 

### Participants 
![[Escalating Challenge.png]]

<figcaption> Escalating Challenge. Image taken from Adams and Dormans </figcaption>

* The task reduces targets, produces progress, or does both. The feedback mechanic increases the difficulty of the task as the player gets closer to achieving the goal.

### Considerations 
* Based on a simple positive feedback loop affecting difficulty. If failure ends the game, the escalating challenge ends the game quickly. 
* Usually the escalating challenge is affected by player skill. 
* Works well in a more complex game. It can be combined with [[#Escalating Complexity]]

## Escalating Complexity 
* *Intent*: Players act against growing complexity, trying to keep the game under control until positive feedback grows too strong and the accumulated complexity makes them lose.
* *Motivation*: Complexity contributes to the difficulty of the task. Escalating complexity means that eventually players can no longer keep up and eventually lose.

### Applicability
* You aim for a high-pressure skill-based game. 
* You want to create emergent mechanics that partially replace predesigned level progression. 

### Participants 

![[Escalating Complexity.png|300]]
<figcaption> Escalating Complexity. Image taken from Adams and Dormans </figcaption>

* Complexity immediately increases the production of more complexity (a strong positive feedback loop that must be kept under control) 
* Player loses when they can no longer manage said complexity

### Considerations
* It typically involves and rewards player skill (until they can no longer keep up). When the game ends, it will end quickly. 
* It creates a game with a varied pace. 
* It can be combined with an [[#Escalating Challenge]], which creates the progression mechanism. 
* It can serve as part of a [[#Multiple Feedback]] structure. 

## Arms Race
* *Intent*: Players can invest resources to improve their offensive and defensive capabilities against other players.
* *Motivation*: It allows players to invest in strategies that fit their skill and preferences. 

### Applicability
* You want to create more strategic options or avoid dominant strategies in games that use the [[#Attrition]] pattern.
* You want to lengthen the time of playing the game 
* You want to encourage the player to develop strategies and play styles that suit their individual skills and preferences. 

### Participants 

![[Arms Race.png]]
<figcaption> Arms Race. Image taken from Adams and Dormans </figcaption>

* Attack mechanisms allow players to drain or steal each other's strengths 
* Activating the attack mechanisms require investments in energy or time. 
* Upgrades can be used for both offense, defense or to restore player's strength. 

### Considerations
* Introduces many strategic options for players to explore which can make balancing difficult. Every strategy must have a counter-strategy. 
* Mechanisms that players don't like are usually ignored. 
* Arms races can delay confrontation and conflict for a long time, prolonging gameplay. 

* Consider *what are required for the upgrades*. 
	* When energy and strength are the same. Players may accidentally over-invest and make themselves vulnerable, especially if upgrades take time. 
	* When energy is separate from strength, their actual relationship needs to be determined. 
* *Make resources for activating upgrades heavily contested*. This prevents the game from taking too long 
* *It can be asymmetrical* but this means the game is more difficult to balance. 

# Miscellaneous Patterns
## Playing Style Reinforcement 
* *Intent*: By applying slow, positive, constructive feedback on player actions, the game encourages specialization and gradually adapts to the player’s preferred playing style.
* *Motivation*: Slow positive, constructive feedback on player actions cause the player to develop over time. Over time, the player avatar and units will reflect player preferences  

### Applicability 
* You want players to make a long-term investment in the game that spans multiple play sessions.
* You want to reward players for building, planning ahead, and developing personal strategies.
* You want players to grow into a specific role or strategy.

### Participants 

![[Playing Style Reinforcement.png|400]]
<figcaption> Playing Style Reinforcement. Image taken from Adams and Dormans </figcaption>

* Ability affects the success rate of actions 
* Attempting actions generates experience points or directly improves abilities. Some games require the action to be successful, while others do not. 
* Experience points might be spent to improve abilities 

### Considerations
* Best suited for games over multiple play sessions, for games with multiple strategies and play styles. 
* It can inspire min-maxing behavior. However, if min-maxing is successful, it usually becomes a dominant strategy.
* It favors experienced over inexperienced players because the former have a better understanding of the game. 
* It rewards players who (are willing to) play longer.  
* It can be ineffective for a player to change strategies over time in a game with playing style reinforcement, because the player will lose the benefit of previous investments in another play style.

* *Consider if experience points are necessary*
	* When using them, there is no direct coupling between growth and action, allowing harvesting of experience. 
	* When not using them, make sure feedback is balanced for the frequency of the actions. More frequent actions should give weaker feedback. 

* Use [[#Escalating Challenge]], [[#Dynamic Friction]] or [[#Stopping Mechanism]] to balance them. 

* *Decide whether the action needs to be executed successfully to generate the feedback*. 
	* When success is required, the feedback loop gains influence and the difficulty of the player's tasks also affects the success of an action. 
	* When success is not required, players have more options to improve neglected abilities during later and more difficult stages, but it might encourage players to perform an action at every conceivable opportunity (be wary when the action has little risk)
## Multiple Feedback 
* *Intent*: A single gameplay mechanism feeds into multiple feedback mechanisms, each with a different profile. 

### Applicability
* You want to increase a game’s difficulty.
* You want to reward the player’s ability to read the current game state.

### Participants 

![[Multiple Feedback.png]]
<figcaption> Multiple Feedback. Image taken from Adams and Dormans </figcaption>

## Trade 
* *Intent*: Allows trade between players to introduce multiple dynamics and negative, constructive feedback

### Applicability
* You want to introduce multiplayer dynamics to the game
* You want to introduce negative, constructive feedback 
* You want to introduce a social mechanic that encourages players to interact with one another via commerce (as opposed to combat).

### Participants 
![[Trade.png|400]]
<figcaption> Trade. Image taken from Adams and Dormans </figcaption>

## Worker Placement 
* *Intent*: The player controls a limited resource she must commit to activate or improve different mechanisms in the game. 

### Applicability
* You want to introduce constant micromanagement as a player task
* You want to encourage players to adapt to changing circumstances.
* You want to introduce timing as a crucial factor in successful strategies.
* You want to create a subtle mechanism for indirect conflict.

### Participants 
![[Worker Placement.png|300]]
<figcaption> Worker Placement. Image taken from Adams and Dormans </figcaption>

## Slow Cycle
* *Intent*: This is a mechanism that cycles through different states slowly, creating periodic changes to the game’s mechanics.

### Applicability
* You want to create more variation by introducing periodic phases to the game.
* You want to counteract the dominance of a particular strategy.
* You want to force players to periodically adapt strategies to shifting circumstances.
* You want to require a longer period of learning before achieving mastery of the game (Players experience slow cycles less frequently, so have fewer opportunities to learn from them)
* You want to introduce subtle, indirect strategic interaction by allowing players to influence the cycle’s period or amplitude.

### Participants 
![[Slow Cycle.png|400]]
<figcaption> Slow Cycle. Image taken from Adams and Dormans </figcaption>

# Links 
* [[The Language of Patterns]] - introduced the concept of design patterns 
* [[Game Mechanics -- Advanced Game Design by Adams and Dormans|Adams and Dormans]] - Ch. 7. 
	* These design patterns are listed in the Machinations Design Pattern. 

* [Game Ontology Project](https://www.gameontology.com/index.php/Main_Page) - a similar listing of common design concepts in games. 