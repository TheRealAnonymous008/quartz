* A subset of [[Object Placement Puzzles]]. Puzzles that make use of directions in their ruleset. In particular, those that include elements of "visibility" or directions via indicated arrows or clues outside the grid that indicate how many objects are "seen" from that side.
* Distinct from (but can have game elements similar to)  [[Loop Drawing Puzzles]] and [[Bridge and Chain Drawing Puzzles]] by requiring object placement rather than drawing lines.
* Note that visibility has to be a line, not just orthogonal or diagonal neighborhoods

### Akari
* *Goal*: Place light bulbs in white cells and light up the grid.
* *Constraint*: Light bulbs may not shine on each other. Bulbs illuminate in all orthogonal directions. 
* *Constraint*: Light is obstructed by the black cells.
* *Constraint*: Numbers in black cells indicate how many bulbs must be placed adjacent to it. 
* *Variant*: **Mirror Akari** - there are now mirrors in the grid.
	* No two bulbs shine on each other, even by reflected light. A bulb cannot shine on itself.
	* If a cell contains a diagonal wall ("mirror"), it should be lit.
	* If a cell contains a diagonal line ("two-sided mirror"), both sides of it should be lit.
	* A cell with a mirror cannot contain a bulb.
### Arofuro
* *Goal*: Place arrows pointing in four directions in each empty cell.
- *Constraint*: Arrows that point in the same direction cannot be adjacent to each other orthogonally.
- *Constraint*: Starting from any cell with an arrow, we can trace a path to a numbered cell.
- *Constraint*: A cell with a number indicates a total number of arrows that leads to this cell.

### Arrows
* *Goal*: Place arrows outside the grid. Every arrow can go orthogonally or diagonally
* *Constraint*: Arrows point to at least one cell with a number.
* *Constraint*: Numbers indicate the total number of arrows that point to them.

### Buraitoraito
* *Goal*: Place stars on the grid.
* *Constraint*: The numbers in the black cells represent how many stars can be seen from that cell.
* *Constraint*:  A star is visible from the black cell, if there is a straight orthogonal path to the star (i.e., horizontal or vertical)
* *Constraint*: Black cells block visibility.

### Gyokuseki
* *Goal*: Place black circles (gems) and white circles (stones) on the grid.
* *Constraint*: Every row and every column contains one black cell and a random quantity of white cells.
* *Constraint*: A number on the edge of the puzzle indicates how many circles can be seen in the corresponding row or column, up to and including the black cell.

### Irasuto
* *Goal*: Shade some cells on the grid.
* *Constraint*: Clues in white cells represent the number of empty white cells that can be seen from that cell (orthogonally).
* *Constraint*:  Clues in black cells represent the number of empty black cells that are seen from that cell

### Kin-Kon-Kan
* *Goal*: Fill in some cells with diagonal lines that act as mirrors.
* *Constraint*: Each region contains exactly one mirror.
* *Constraint*: Letter-number pairs on the outside of the grid must be paired with straight lines (laser beams) that bounce off the mirrors.
* *Constraint*: The number of bounces is equal to the number in the letter-number pair.

### Kuromasu
* *Goal*: Identify which cells on the grid are shaded
* *Constraint*: The numbers on the board represent the number of unshaded cells that can be seen from that cell, including itself.  
* *Constraint*: A cell can be seen from another cell if both cells are within the same row or column, and there are no shaded cells between them in that row or column.
* *Constraint*: Numbered cells are always unshaded.
* *Constraint*: No two shaded cells may be orthogonally adjacent.
* *Constraint*: Unshaded cells must form a connected region.

### Lighthouses
* *Goal*: Place ships on the grid.
* *Constraint*: Lighthouses (numbered cells) represent the number of ships lit by the lighthouse. A ship is lit if it is in the same row or column as the lighthouse
* *Constraint*: Each ship is lit by at least one lighthouse
* *Constraint*: No ship touches any other ship or lighthouse orthogonally or diagonally
* *Variant*: **Lighthouse battleships**. Ships are now battleships, that is more than one cell.
	* Battleships may not touch each other or the lighthouses, not even diagonally.

### Rabbits and Trees
* *Goal*: Place exactly one white circle (rabbit) and one black circle (tree) in every row and column.
* *Constraint*: A number indicates how many rabbits can be seen in the corresponding orthogonal direction
* *Constraint*:  Trees obstruct vision.

### Rukkuea
* *Goal*: Shade some cells in the grid.
- *Constraint*: Black cells form an area of square shape.
- *Constraint*: No black areas touch each other orthogonally. They may touch diagonally.
- *Constraint*: Two cells from distinct regions of the same size cannot see each other orthogonally. Vision is obstructed by other black cells.
- *Constraint*: Each number shows how many cells (itself + its orthogonal neighbors) must be shaded.

### Sun and Moon
* *Goal*: Place exactly one star and one stardust cloud in each row and column.
* *Constraint*: Stars illuminates planets, represented as circles, but only on the side that faces the star. Illumination is orthogonal until blocked.
* *Constraint*: Stardust clouds and Planets block starlight.

### Toichika
* *Goal*: Place arrows in some of the cells.
* *Constraint*: Each region contains exactly one arrow.
* *Constraint*: Arrows are paired if they point to each other. No arrow is unpaired.
* *Constraint*: Regions with paired arrows are not orthogonally adjacent (that is, they do not share edges)
* *Constraint*: No arrows are placed in between two paired arrows.
