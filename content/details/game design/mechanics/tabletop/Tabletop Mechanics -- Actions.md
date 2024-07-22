* **Action Points** - A player receives a number of Action Points on their turn. They may spend them on a variety of Actions.
	* A common implementation is that a player receives a fixed number of Action Points on their turn and can spend them on any combination of Actions
	* Adding varying costs for actions will require more balancing from the designers.
	* Actions can be limited to only one per turn
	* Action Point systems give the players a lot of flexibility in how they approach their turn
	* The pace of the game is determined by [[Game Economy|the number of Action Points available per turn]].
* **Action Drafting** - Players select from an assortment of Actions in a shared pool. The available Actions are limited in quantity, and once a player has chosen an Action it may not be chosen again.
	* Actions are treated as not just a resource but as part of a marketplace.
	* Tactics such as denying other players actions are possible
	* Action drafting incorporating randomness (i.e., something like [[Tabletop Mechanics -- Turn Order and Structure|Random Order]] for picking actions) reduce perfect planning.
	* Another variant is that players who claim an action first can perform more powerful variants of that action
* **Action Retrieval** - Each player has a set of Actions available to them, represented by cards, tokens, or some other component. 
	* Once the Action is performed, the component is spent and the Action may not be performed again until the component is retrieved. 
	* Action Retrieval may be an Action taken as part of a turn or it may consume an entire turn.
	* It rewards efficiency. Retrieving more frequently is disadvantageous.
	* It rewards long-term planning and balanced strategies that use as much of the action space as possible.
	* It also allows tactical play -- knowledge of what opponents cannot do can be incorporated
	* Actions may have on play and on retrieve effects.
	* Actions can have dynamic effects based on the relative order they are played.
	* The action space can be a mix of one time and recoverable.
* **Action / Event** - On their turn, the player plays a card that shows Action Points and an Event. They must choose to either use the Action Points or perform the Event. If they choose to use the Action Points, typically the Event may be performed by another player.
	* Allows integrating special actions or events into a system to emphasize the theme
	* Gives players a layer of choice compared to Event Decks.
	* Games using this system add another layer of player decision making by having some or all events only eligible for specific players.
	* Can enforce a proper sequencing of events.
* **Command Cards** - Players have a hand of cards that allows them to activate and perform actions with a subset of their units.
	* It reduces the length of turns and simplifies decision-making.
* **Action Queue** - Players create Action Queues and perform them in sequence
	* Players must plan actions and commit to a specific sequence of execution.
	* Leads to both planning and chaos as players commit to moves several turns in advance.
	* Queues can either be
		* **Rolling** - action at the head of the queue is revealed and performed as a new action is added to the end
		* **Batch** - a set number of actions are added to the queue at one time and then all are resolved in order.
	* When queues get longer, and particularly when movement and rotation actions are included in the available actions, players need to visualize where they will be as they progress through the queue. Visualization is difficult
	* Mechanics can also interact with the queue itself -- moving actions ahead or behind of the queue
* **Shared Action Queue** - All players add Actions to a central Action Queue. Actions in the Queue are performed by all players.
	* Increases interactivity  as they plan actions for their opponents
* **Follow** - One player selects an Action. Other players may then perform that Action or a modified version of it.
	* Often implemented alongside Action Drafting and Role Selection
	* Players have to consider what is good for them and what will be good for their opponent
	* Designers can make it so only certain actions can be "Follow"-ed
	* May slow down play if players have to decide if they want to Follow and how.
* **Order Counters** - Players place Order Tokens into regions, indicating what they want to do in that particular region of the board. After all the tokens are placed, they are executed in sequence
	* Combines an Interleaved Turn Structure with an Action Queue. Players are creating multiple Interleaved Action Queue during planning and resolving them.
	* Need to consider how to resolve orders. 
		* LIFO structures introduce the challenge of remembering the orders so far. 
		* FIFO structures are easier to remember 
* **Rondel** - The available Actions are represented as pie wedges in a circle. Each player has one or more tokens on Rondel’s wedges. On their turn, they may move their token around the Rondel and perform the Action indicated by the wedge where they stop. 
	* It is typically more costly to move further around the Rondel.
	* The Rondel represents a menu of possible actions.
	* It requires players to balance between taking an action now and waiting to do it at a lower cost.
* **Action Selection Restriction** -Players are restricted in which actions they may choose.
	* It can force players to choose the less optimal actions.
* **Variable Player Powers** - Each player has special Actions that only he or she can perform or that modify standard actions.
	* It introduces asymmetry in the game. 
	* Some strategies may only be optimal for certain players which may limit player choice.
	* It increases replayability as players can try other powers.
	* It increases complexity and cognitive load, which typically means that the underlying action / [[Tabletop Mechanics -- Resolution|resolution]] framework should be simple
* **Once Per Game Abilities** - Players have a special ability that they can use one time per game.
	* Typically different per player or character. Because they are only performed once, they can be powerful.
	* The threat of using this ability also adds tension and is a decision factor in player strategy.
	* Timing becomes critical
* **Advantage Token** - One player has a token that permits them to perform a special Action or modify an Action. Once used, the token passes to another player.
	* It determines what actions are available to players. 
	* It adds a timing factor because players weigh the value of the advantage against its loss and use by an opponent.
	* Can also be used for tie-breaking 
	* Can be used to give players control over the random aspects of the game.
* **Gating and Unlocking** - At certain points in the game, new actions are made available to the players. Actions may become available by a variety of means, including reaching a certain turn or game stage.
	* Depleting a shared pool or bringing some track past a threshold level through the cumulative effects of the actions of all the players is another common approach to triggering unlocks. 
	* The mechanism is not limited to gating actions. Game events and narrative breaks may also be gated and unlocked through this type of triggering mechanism
	* It affects the availability of Actions rather than how they are selected. 
	* It can introduce new resources, more options and new mechanics
	* Gating mechanics helps control complexity and power scaling.
	* Adding new actions feels like the game is progressing and getting more advanced.
	* This also extends to unlocking new threats as play progresses.
* **Tech Trees** - During the course of the game, new Actions become available to specific players, or existing Actions are improved. These advancements are done by spending resources.
	* Upgrades may have pre-requisites for each other. 
	* It could also be expressed as a track where players get stronger as they progress through the track.
	* Tech acts as another resource subject to the internal game economy.
	* It gives the designer control over what actions are available per turn
* **Events** - Actions occur outside the control of players that cause an immediate effect, change the state of the game, or impact subsequent actions.
	* The usefulness of an event is proportional to how long its effect lasts.
	* Events can force players to re-strategize.
	* Events should not feel too random.
* **Narrative Choice** - Multiple action options are presented to the players via a narrative format.
	* Incorporates [[Narrative]] into the gameplay.
	* Frequently incorporates stat checks to determine outcome.
	* Prone to ludonarrative dissonance or even just incoherent narratives if the designer isn't careful.
* **Bingo** - Game elements are selected at random, and each player needs to use the elements for their own actions.
	* It takes luck out of randomness because players are given the same random sequence.
* **Layering** - Components are placed above other components and can overlap in various ways. Only the topmost visible icons/areas are active.
	* Typically involves cards in some way since cards can be layered on top of each other.
	* Introduces a spatial element that involves matching elements up. However, overlapping is more complex than tile placement since it is more constrained.
	* **Splaying** is a variant of this where cards are arranged so that one side of a lower card pokes out of the side of a card above it.
* **Slide / Push** - Players slide a token, and other tokens ahead of it are pushed.
	* **Quantized Slides** mean that tokens move in specific locations.
	* **Freeform Slides** allow sliding anywhere on the play surface.
	* One consideration is the number of pushing directions available. More axes = more player options = more complex decision making.
	* Another thing to consider is what happens if pieces are slid off the grid.
	* For freeform slides, there must be a degree of uncertainty.
* **Matching** - A player is limited to playing a card or token that matches some feature on the card or the token played just prior.
	* In some instances, several cards or tokens from previous plays will be visible and available to match against.
	* It is simple, ideal for low complexity games or subsystems in high complexity games.
	* Games that feature matching as the core mechanism are often shedding games, where the objective is for a player to get rid of all their cards.
	* Have multiple axes of matching or make cards have multiple matching opportunities. This expands player choice.
	* Need to balance the degree to which two cards can match.
	* Extends to linking things together (i.e. combos)
	* The rules for matching need not be static. It can dynamically change throughout the game
	* Some games can require players to react to matching. Often found in speed games.
* **Drawing** - Players draw a picture and other players guess what the picture is intended to depict.
	* A key objective for most designs in this category is to level the playing field in terms of artistic talent (i.e. time pressure or [[Tabletop Mechanics -- Resolution|targeted clues]] so that some but not all can guess )
	* The center of this mechanism really is [[Semantics|representing]] a target object
# Links
* [[Building Blocks of Tabletop Game Design - An Encyclopedia of Mechanisms by Engelstein and Shalev]] - Ch. 3