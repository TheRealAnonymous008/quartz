* The following presents a list of puzzles alongside the general goal of the puzzle and any additional rules present.
* Although some degree of [[Mathematics]] is present for all of these. We exclude mathematical problems.

# Dissection Puzzles
* Cut a shape into smaller shapes and re-arrange them to produce a particular pattern or geometric shape
	* *Extension*: Frame the problem as going from one shape to another shape while using:
		* The fewest / given number of cuts.
		* The fewest / given number of shapes 
	* *Extension*: Go from one shape to many smaller target shapes. Adding additional constraints (i.e., each smaller shape is the same size)
	* *Extension*: Go from many given shapes to one target shape.

* **Disappearance Puzzles** - arrange the geometric shapes in such a way that in the resulting shape, there is an apparent addition / subtraction of units. 
	* Alternatively, explain where the sleight of hand is in the disappearance

### Tangram-Like Puzzles
* **Tangram** - starting with a set of pieces of different shapes, assemble various figures based on their silhouettes. 
	* The STANDARD set is 5 triangles of varying sides + a square and a rhomboid.
		* *Extension*:  **Circular Tangram** - generalizes Tangram to use pieces that can have curved sides.
		* *Extension*: Use a different set of given shapes. 
		* Usually, though, the pieces can be assembled to form a basic shape (a square, circle, heart, egg, etc...)
	* The player is given a silhouette.
		* We can make it harder by obstructing the silhouette non-intrusively (adding stripes, for example).
		* Silhouettes can be abstract to representational, pertaining to people or objects. Sometimes even these objects may be given in place of the silhouette.
	* The player MUST use all pieces to assemble the figure.
	* In assembling, the pieces MUST touch without overlapping.

* **Polyforms** - Similar to Tangram except with the additional constraint that all pieces are identical or similar in some way. The goal is still to produce a similar shape.
	* **Polyomino problem** - a variant using a polyomino (usually a pentomino). Given a set of polyominos, cover the silhouette of the shape without the pieces overlapping.
	* *Extension*: Add a constraint where certain patterns may not be produced (for example, four polyominos may not touch at a corner).
	* *Extension*: Not just 2D shapes, but use 3D shapes too with varying thicknesses.
		* **Soma Cube Variants** - given a set of 3D polycubes (cubes assembled in a particular 3D shape), make a bigger cube (or a bigger shape) using all the pieces.

* **Matchstick Puzzles** - Similar to Tangram except with the additional constraint of all pieces corresponding to sticks (aka edges). The goal is still to produce some shape. 
	* *Extension*: We may only operate on a limited number of moves.
		* *Extension*: Move matchsticks to produce another configuration.
		* *Extension*: Remove matchsticks to produce another configuration.
		* *Extension*: Allow / Forbid matchsticks to be broken
	* *Extension*: The matchsticks are of different lengths.
	* *Extension*: Allow / Forbid matchsticks to cross.
	* *Extension*: The matchsticks must make a 3D structure that satisfies additional constraints.

### Miscellaneous Types
* **Domino Puzzles** - puzzles that involve the use of dominoes---defined as a piece consisting of two half-tiles. Each half tile has a number of pips on them.
	* *Variant*: Make a pattern given a set of dominoes such that half-tiles that touched each other had the same number of pips.
	* *Variant*: Make a pattern such that the "rows", "columns" or both satisfied an arithmetical constraint (i.e., same sums)
	* *Extension*: Whether or not to allow dominoes with blank half-tiles and how to handle them exactly.

# Logic Puzzles
* Any form of mathematical puzzle counts here.
## [[Grid Puzzles]]
### Positioning Puzzles
* **Chessboard / Checker Puzzles**
	* Involve the use of a chessboard, usually exploiting the property of having white and black cells.
	* Alternatively, it may involve the use of circular checker pieces that slide around each other in a certain way. The goal is to arrange them in a new way.
	* Constraints on movement may also take inspiration from chess moves or checker moves.
* **Connection Problem**
	* Form a [[Graph Theory|Graph]] that connects a set of nodes together, satisfying some sort of property.
* **Moving Peg Puzzles**
	* An array of holes is drilled in a board. White pegs are placed in the upper half. Black pegs are placed in the lower half. The center is left vacant.
	* The goal is to transfer the white pegs to the lower half and the black pegs to the upper half. 
	* A peg may move either
		* to an adjacent vacant square or 
		* by jumping over one neighboring peg to a vacant square
	* Moves must only be forward or backward, parallel to the sides of the square.
* **Peg Solitaire**
	* We have a board full of pegs arranged in some way.
	* Pegs can only be moved by jumping over a neighboring peg to a vacant space directly on the other side. Following this jump, the peg that was jumped over is removed.
	* Jumps are only made along lattice lines.
	* The goal is to remove all pegs on the board.
* **Transportation Puzzle**
	* We have a set of objects and two (or more) islands with a river separating them.
	* The goal is to move all the objects to the other side of the river.
	* Certain objects cannot be together.
	* *Example*: Tower of Hanoi
	* *Example*: Farmer, Fox, Rabbit, Cabbage Problem
* **Shunting Problem**
	* Given trains on a set of railroad tracks, find a way to get the trains to where they are supposed to go without them colliding.
	* Constraints on the number of moves or the time taken may be given.
	* *Variant*: The length of the track may influence the number of rolling vehicles which can be placed on them.
	* *Variant*: Certain trains may not go on certain tracks.
	* *Variant*: Build up a train in a specific order, picking up rolling stock from various locations.
	* *Variant*: Decompose the train, placing rolling stock items in specified locations.
	* *Variant*: Devise the optimum sequence of rolling stock items in a train, so that it can be efficiently assembled at its starting point and decomposed at its destination(s).
* **Sliding Block Puzzle**
	* Consists of a set of blocks arranged on a board. The blocks can slide around.
	* The goal is to arrange the blocks in a certain way.
	* Pieces CANNOT be lifted off the board. 
	* *Example*: The 15 Puzzle
	* *Example*: Sokoban

# Mechanical Puzzles
* **Packing Puzzle** - the goal is to fit two items together, but the way they fit together is not as straightforward. The solver must determine how to fit them together.
	* *Example*: The Melting Block
	* *Example*: Conway's Packing Problem
	* *Example*: The Chinese Cube
	* *Example*: The Vanishing Sphere

### Disassembly Puzzles
* The challenge for these puzzles is not only to solve it, but to undo the solution (i.e., to reassemble the problem)

* **Burr Puzzle** - also called Chinese crosses or Notched stick puzzles. Consists of structures that interlock with each other. The goal is to disassemble the structures.
	* *Example*: Van der Poel's puzzle,
	* *Example*: The Japanese Crystal

* **Magic Boxes** - the goal is to unlock the box. The lock has complex mechanisms that the solver must determine and unlock.
	* *Example*: Haselgrove Box
* **Magic Disk** - consists of interlocking disks that must be separated from each other.
* **Rattle Puzzle** - consists of a container with an item inside that would rattle when the container was shaken. The goal is to remove the item(s) inside.
	* *Example*: The Ball in the Cage

### Ring String Ball Problems
* Features any two of a ring, string (solid rod or cord), and a ball. The goal is:
	* *Variant*: Remove one element from the puzzle. 
	* *Variant*: Move one element with respect to the main component.
	* *Variant*: Find the sequence of moves such that one part is removed or repositioned.
	* *Variant*: Solve the puzzle with additional constraints (i.e., the cord and the ring must stay together).
* Generally when a string is used, the key is generally to be found in a loop drawn over a knot or ball. 
* Example puzzles are found in [[Creative Puzzles of the World by Van Delft and Botermans|Van Delft and Botermans]].
	* **Maleda** - the goal is to remove the staple by raising the rings and rods in a certain order.

### String Puzzles
* **Whai / Cat's Cradles** - the goal is to form intricate patterns using only string held taut by one's fingers.
* Generally feature strings where the objective is:
	* *Variant*: Rejoin two ends of the string.
	* *Variant*: Perform a cut on the string that obeys certain constraints.
	* *Variant*: Pull at the string in a certain way so that knots vanish.
	* *Variant*: Unknot the cord (can be extended further to escape from bonds.)
	* *Variant*: Perform an intricate knot subject to constraints.

### Wire Puzzles
* **Wire Puzzles** - a similar variant to the Burr Puzzle except involving metal pieces that have been bent and interlocked with each other in a convoluted manner.
	* *Example*: A famous one -- the Gordian Knot
	* Variants of this can incorporate elements from [[#Ring String Ball Problems]]
* **Wire and String Puzzle** - consists of a wire and a string (with possibly additional components like balls or knots). 
	* **Closed String Puzzles** - the string consists of one closed loop. The goal is usually to disentangle the string from the wire.
	* **Unclosed Loose String** - the pieces of the string are not closed and not attached to the wire. Usually the ends are fitted with an object to keep the string from slipping out.
	* **Unclosed Fixed String** - the pieces of the string are not closed, but somewhere on its length is attached to the wire. The goal here is usually similar to a [[#String Puzzles|string puzzle]].
# Tour Puzzles
* The puzzle involves the player traveling around a board, possibly requiring the player visit certain points on the board.
### Mazes
* Patterns of intricately winding paths have been cut on the landscape. The goal is to navigate from point $A$ to point $B$, traversing through the maze.
* A classic technique to solving this (which doesn't always work) is to *keep your hand on one side of the maze at all times.* 
	* This fails when there is more than one entrance and there is a route connecting them that doesn't pass through the goal, or if there are loops
* Another technique by Tremeaux (which is just DFS in disguise)
	* Mark one side of the corridor (say the right) as you pass through the maze. 
	* Whenever you reach a dead end, retrace your steps, still marking the right hand wall.
	* Whenever you reach a previously visited junction along a path that you are following for the first time, turn around and retrace your steps, still marking the right hand wall.
	* When you reach a previously visited junction along a path that you have used before, take a new path. If there is any available. Otherwise, take any previously used path.
	* Never enter a path that has been marked on both sides.
* Other methods make use of [[Graph Algorithms]].
* When making a maze, it is usually best to start with the solution path first.
	* *Variant*: 3D Mazes
	* *Variant*: More than one goal (that may need to be reached in a specific order)
	* *Variant*: More than one entrance.
	* *Variant*: Entrance and or exit is inside the maze rather than the typical case where they are outside.

# Optimization Puzzles
* Applies to any of the puzzles above (or to new ones).

* Instead of being given the number of moves, find the optimal number of moves that still solve the problem.
* This also extends to tasks that are adjacent to [[Automata Theory|Automata]] or [[Instruction Set Architecture|Assembly]] wherein we want to minimize:
	* The number of instructions
	* The "space" occupied by the solution (analogues to memory or size for example).
	* The time it takes for some program to finish.

# Links
* [[Creative Puzzles of the World by Van Delft and Botermans]]