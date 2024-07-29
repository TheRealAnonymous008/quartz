* **Tessellation** - The playing field is divided into spaces to regulate movement.
	* The field can be a **track** which is effectively one-dimensional.
		* Tracks can have branching paths to create shortcuts. 
		* Spaces can be divided into subspaces in the width of the track used to allow multiple players to occupy the same space.
	* The field can be a **grid**. Typically it involves either hexagonal or square grids.
		* If squares are used, the designer needs to decide if pieces may move diagonally. From a distance standpoint, a diagonal move is approximately 50% further than an orthogonal move, which needs to be compensated for in games striving for realism
		* If hexagons are used, all natural moves are equidistant from each other 
	* The field can be a 3D **space**.
		* This presents a UX challenge to make the space readable for players.
	* Irregular patterns can also be used. This is called an **Area Map**. Effectively a [[Graph Planarity|Planar graph]]
		* If they regulate movement, the areas should be approximately the same size, or at least “movement equivalent"
		* If possible, regions should not touch at a corner, and they should only touch along an edge.
	* If a region contains important information, like terrain type or resources, the graphics should be visible and distinct even if pieces are presents.

* **Roll and Move** - A randomizer is used to determine how far to move a piece. The space landed on determines the action(s) a player can take.
	* Because Roll and Move has been used in so many simplistic children’s games, it has the reputation as an anti-pattern. 
	* Players might feel they are not in control of their actions and are at the mercy of the randomizer.  Some ways to mitigate this:
		* Give more ways to apply the results of the randomizer
		* Have mechanisms that allow the player modify, use a subset of the roll or choose a direction. 
		* Wager movement.
		* Have [[Tabletop Mechanics -- Uncertainty|Probability Management]].

* **Pattern Movement** - Pieces move in a specific pattern relative to the board grid. 
	* There are three basic styles. 
		* **Fixed Target Space** - There are a few specified target squares, and the piece may be moved to any of them. 
		* **Any Distance in a Direction** - Pieces may move any number of spaces in a given direction until blocked by another piece.
		* **Jumping** - Jumping over pieces or chaining jumps together.
	* Moves need not be reversible.
	* Typically games with this Movement Mechanism have a Promotion Mechanism.

* **Movement Points** - A piece is given a number of points to spend on movement.
	* Allows the designer to differentiate units as well as movement conditions.
	* Another extension is to allow normal Movement Points to be increased by incurring some limitation or penalty.

* **Resource to Move** - Players expend a Resource to Move. It increases player choice.

* **Measurement** - Pieces may be moved up to a certain distance, measured by a ruler. 
	* The designer needs to decide whether to allow for Measurement at any time to determine the range or only after attacks or moves have been declared
		* Not allowing premeasurement gives an edge to players that are better at estimating ranges but tends to make for a lighter experience as strategy can fail due to a failure of estimation.
		* Allowing premeasurement slows the game down
	* There is always some imprecision in moving and Measurement
	* Measurement can make the game feel more cinematic and realistic.

* **Different Dice** - Different Dice are used to move depending on unit or game state.
	* This introduces some randomness in movement rates but allows the player (and designer) to control the range
	* One of the advantages of this system is that there are very few rules overhead. Once the die is selected, you roll it to generate that number of Movement Points.

* **Drift** - Two movement cards are played to move. The sum represents the distance forward moved; the difference represents the sideways movement (Drift).

* **Impulse** - A turn is broken up into a series of small Impulses. Depending on their speed, units will be able to move in specific Impulses.
	* Moves are interleaved. The system simulates the simultaneous movement of player pieces.
	* It increases realism but also complexity and bookkeeping.

* **Programmed Movement** - Players simultaneously program their movement and then reveal and execute it
	* A subset of [[Tabletop Mechanics -- Actions|Action Queues]]. 
	* Players need to visualize the movement in advance.
	* The game presents a spatial [[Grid Puzzles|Puzzle]].
	* One parameter designers can tweak is the size of the program queue.

* **Relative Position** - The precise location of units is not tracked. Only their Relative Position is important.
	* This system has the benefit of simplicity and focuses on specific aspects of racing
	* Eliminates the need for a board.
	* Keeps games [[Tabletop Mechanics -- Game Structure|Competitive]]. 

* **Mancala** - Movement is based on the number of units at the starting location.
	* A common variation on this mechanism is that only one piece moves, but the distance it gets to move is exactly equal to the number of pieces in the space it starts in
	* A common variation on this mechanism is that only one piece moves, but the distance it gets to move is exactly equal to the number of pieces in the space it starts in

* **Chaining** - Pieces are stationary but are built out in chains.
	* Building the chains gives a dynamic feel of movement. 
	* Using chains, rather than just a single unit, creates opportunities to blockade other players, forcing them to cross your path, or topologically isolate them. This provides many tactical options for players.

* **Bias** - Pieces automatically move in a certain direction, or it is easier to move in a certain direction.
	* Typically used to simulate fluid currents or conveyor belts. 
	* **Automatic Bias** mechanisms move pieces in a set direction, typically at the end of each turn.
	* **Influencer Bias** mechanisms make it easier to move in certain directions.
	* Giving players options to control these bias mechanisms can provide tactical options.
	* If the system gets complicated, it can be difficult for players to picture where they will be at the end of their turn

* **Moving Multiple Units** - Actions may Move one or Multiple Units. Considerations from [[Tabletop Mechanics -- Actions|Command Cards]] apply here.

* **Map Addition** - The map is added to as it is explored.
	* **Constrained Map Addition** - the shape of the board is known and players must explore within these bounds
	* **Unconstrained Map Addition** - players are free to explore as they wish (under some constraints).
	* This mechanism is often implemented with tiles and so is a subset of Tile Laying
	* If players can build in any direction, it may keep them somewhat separated as each explores their own area. If more interaction is desired, some incentive to move to the center needs to be included
	* The Map Addition mechanism can also be used to introduce [[Tabletop Mechanics -- Uncertainty|uncertainty]] into an essentially linear track
	* Exploration can be [[Procedural Generation|procedurally generated]]

* **Map Reduction** - Over the course of the game, the map shrinks.
	* Removing parts of the map can be psychologically interesting for the players, as they feel more constricted both in space and in options.
	* Many other games don’t shrink the physical board; they simply reduce the options available to the players

* **Map Deformation** - The map is modified during the course of the game through rotation or shifts.
	* Because this can often radically change the game situation, this mechanism introduces a large dose of chaos into the proceedings
	* It can also make it difficult for certain players who may have spatial relation issues to visualize the result of the deformation.

* **Move Through Deck** - Players Move Through a Deck of cards
	* This mechanism gives players the feeling of movement by forcing them to work through a deck to get to the bottom or some goal card.
	* Adopting this metaphor allows designers to give players a sense of forward momentum while keeping the game compact, eliminating the need for a board or large map
	* It allows randomization and [[Tabletop Mechanics -- Actions|Gating and Unlocking]]

* **Movement Template** - A defined Movement Template is used to determine where a piece moves to.
	* The use of templates allows for unit differentiation by defining which templates may be available to them

* **Pieces as Maps** - The Pieces themselves compose the Map.

* **Multiple Maps** - The game takes place on Multiple Maps which are connected at defined points.
	* Having Multiple Maps forces players to approach the geometry of the situation in a different way.
	* Introducing Multiple Maps gives more complexity

* **Shortcuts** - A shorter or quicker route exists that may not always be available.
	* Shortcuts give points to wrap around the geometry of the board
	* Shortcuts can be limited to only certain characters.

* **Hidden Movement** - Movement occurs that is not visible to all players.
	* Hidden Movement requires actions to be taken without the knowledge of the other players.
	* More complex systems may require players to be familiar with the (complex) rules.
	* Since deception and deduction are typically part of the Hidden Movement experience, most of these games have defined points or reasons when players must reveal their location.
	* Hidden movement games can take advantage of recording moves to force players to actually program movement in advance. This gives a dynamic of "chasing" after another player 
	* **Anchor / Distance** - a variant of this where the unit is placed at an anchor point and at each time step moves one distance unit. When the movement is complete or the unit revealed, the unit is placed on the map based on the distance. Effectively, the Anchor can function as a "last revealed location" marker.
# Links
* [[Building Blocks of Tabletop Game Design - An Encyclopedia of Mechanisms by Engelstein and Shalev]] - Ch. 10