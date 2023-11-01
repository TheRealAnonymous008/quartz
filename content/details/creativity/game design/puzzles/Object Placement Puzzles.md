* The general goal is to place an object on the grid (or outside of it). Not all cells have to have that object.

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

### Arrows
* *Goal*: Place arrows outside the grid. Every arrow can go orthogonally or diagonally
* *Constraint*: Arrows point to at least one cell with a number.
* *Constraint*: Numbers indicate the total number of arrows that point to them.

### Battleships
* *Goal*: Find the location of all the ships on the grid.
* *Constraint*: Ships do not touch each other. Not even diagonally.
* *Constraint*: Numbers MAY indicate the number of squares in that row or column are occupied by part of a ship.
* *Constraint*: Numbers MAY indicate the number of water segments in the ship
* *Variant*: **Clouds**. Ships are now rectangular in shape, with width and height of at least two cells.
* *Variant*: **Digital Battleships** Grid contains numbers. Values on the right and bottom edges reveal the sum of the numbers in each ship piece that appears in the respective row or column.

### Buraitoraito
* *Goal*: Place stars on the grid.
* *Constraint*: The numbers in the black cells represent how many stars can be seen from that cell.
* *Constraint*:  A star is visible from the black cell, if there is a straight orthogonal path to the star (i.e., horizontal or vertical)
* *Constraint*: Black cells block visibility.

### Chocona
* *Goal*: Shade some cells in the grid
* *Constraint*: A cell with a number indicates how many cells in the region must be shaded.
* *Constraint*: Regions without numbers mean any number of cells may be blackened
* *Constraint*: Black cells must form rectangles independent of region borders.
* *Constraint*: Black rectangles are not orthogonally adjacent.

### Dosun-Fuwari
* *Goal*: Place one black and one white circle in each region.
* *Constraint*: White circles (Balloons) must be placed either 
	* Into the top cell of the grid 
	* Into the cell right under black cells on the grid
	* Under other white circles.
* *Constraint*: Black circles (Iron balls) must be placed either
	* Into the bottom cell of the grid.
	* On the cell right over black cells on the grid.
	* Over other black circles.

### Fill-a-Pix
* *Goal*: Shade some cells on the board. The solved board will form a picture.
* *Constraint*: The cells with clues represent how many of the nine squares around it (including itself) should be filled in.

### Gappy
* *Goal*: Shade some cells on the grid.
* *Constraint*: Each row and column contains exactly two shaded cells.
* *Constraint*: Shaded cells cannot touch each other orthogonally or diagonally.
* *Constraint*: Numbers outside the grid show the number of white cells between black cells in the corresponding row or column.

### Gyokuseki
* *Goal*: Place black circles (gems) and white circles (stones) on the grid.
* *Constraint*: Every row and every column contains one black cell and a random quantity of white cells.
* *Constraint*: A number on the edge of the puzzle indicates how many circles can be seen in the corresponding row or column, up to and including the black cell.

### Hamusando
* *Goal*: Fill the grid with squares (toasts) and circles (hams).
* *Constraint*: Every row and column contains two squares and $N$ circles ($N$ is given).
* *Constraint*: A number at the edge of the grid indicates how many hams must be placed between the two toasts.

### Irasuto
* *Goal*: Shade some cells on the grid.
* *Constraint*: Clues in white cells represent the number of empty white cells that can be seen from that cell (orthogonally).
* *Constraint*:  Clues in black cells represent the number of empty black cells that are seen from that cell

### Kakurasu
* *Goal*: Color some of the cells to satisfy the clues
* *Constraint*: Numbers on the top and left sides give the totals for the black squares based on their value reading in that direciton
* *Constraint*: Numbers on the bottom and right side  give the value of the cells from that direction 
	* So that, for example, clues on the top give sums along columns. The values used are those specified on the right side of the grid (which go down along columns).

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

### Link-A-Pix
* *Goal*: Shade some cells corresponding to lines drawn on the board. The solved board will form a picture
* *Constraint*: The cells with clues are the endpoints of a path and they represent the length of the path containing them (1 clues count as that cell being shaded.)
* *Constraint*: Both endpoints of a path must contain clues. All clues are given.
* *Constraint*: Paths may not cross
### Minesweeper
* *Goal*: Place mines into empty cells on the grid.
* *Constraint*: Digits in the grid represent the number of mines in the neighboring cells, including diagonal neighbors.
* *Variant*: **Minesweeper Battleships** - mines are replaced with battleships. Clues indicate how many ship pieces are adjacent to it. 
	* Ships may not touch each other, not even diagonally.
* *Variant*: **Double Minesweeper** - place mines into each empty cell in the grid.

### Mochikoro
* *Goal*: Shade some cells on the grid.
* *Constraint*: Shaded cells divide the grid into rectangular islands of unshaded cells.
* *Constraint*: Islands cannot share edges, but they must be connected diagonally via their corners
* *Constraint*: Islands must have the same number of  cells as the number it contains.
* *Constraint*: No pools. No $2x2$ areas must contain only shaded cells

### No Four in a Row
* *Goal*: Fill the grid with symbols.
* *Constraint*:  Four consecutive symbols never appear in any row, column, or diagonal.

### Nondango
* *Goal*: Shade some circles on the grid.
* *Constraint*: Each region contains one black circle.
* *Constraint*: Three consecutive circles of of the same color never appear in any orthogonal or diagonal direction. There must be a circle of the other color or an empty cell between them.

### Norinori
* *Goal*: Shade some cells in the grid
* *Constraint*: Every region contains exactly two black cells.
* *Constraint*: Each block must be a part of a domino, irrespective of region borders.
* *Constraint*: No two dominoes may share an edge. They can touch diagonally.

### Number Cross
* *Goal*: Shade some cells.
* *Constraint*: Numbers outside the grid show the sums of the numbers in white cells in the corresponding row or column.

### Rabbits and Trees
* *Goal*: Place exactly one white circle (rabbit) and one black circle (tree) in every row and column.
* *Constraint*: A number indicates how many rabbits can be seen in the corresponding orthogonal direction
* *Constraint*:  Trees obstruct vision.

### Retrograde Battleships
* *Goal*: Place the ships on the grid similar to [[#Battleships]]
* *Constraint*: No ship may touch another orthogonally or diagonally/
* *Constraint*: Ship segments are given and must be respected.

### Roma
* *Goal*: Place arrows pointing in four orthogonal directions in each empty cell.
* *Constraint*: Arrows cannot repeat in a region.
* *Constraint*: Starting at any cell, going in the direction of the arrows, it is possible to reach the marked cell on the grid 

### Rukkuea
* *Goal*: Shade some cells in the grid.
- *Constraint*: Black cells form an area of square shape.
- *Constraint*: No black areas touch each other orthogonally. They may touch diagonally.
- *Constraint*: Two cells from distinct regions of the same size cannot see each other orthogonally. Vision is obstructed by other black cells.
- *Constraint*: Each number shows how many cells (itself + its orthogonal neighbors) must be shaded.

### Santoitchi
* *Goal*: Shade some cells in the grid
* *Constraint*: Numbered cells must not be shaded.
* *Constraint*: All white cells must be divided on regions having the size of exactly three cells.
- *Constraint*: Two black cells must not be orthogonally adjacent.
- *Constraint*: Each region contains a number.
- *Constraint*: A number indicates how many black cells share an edge with that region.

### Shakashaka
* *Goal*: Place triangles in some of the white cells.
* *Constraint* The white parts of the grid (that do not have black triangles) must form rectangular regions.
* *Constraint*: Black cells with a number must be orthogonally adjacent to the specified number of black triangles.

### Shimaguni
* *Goal*: Shade some cells in the grid.
* *Constraint*: All black cells in a region must be connected.
- *Constraint*: A cell with a number indicates how many cells in the region must be shaded.
- *Constraint*: In regions without a number at least one cell must be shaded.
- *Constraint*: Two regions with the same amount of shaded cells must not be orthogonally adjacent.
- *Constraint*:: When two cells are orthogonally adjacent across a region boundary, at least one cell must be unshaded.

### Starry Night
* *Goal*: Place one white circle (sun), one black circle (moon) and one star in every row and column of the grid.
* *Constraint*: Same figures may not touch each other diagonally.
* *Constraint*: Figures outside indicate the distance between the star and circles in that row or column.
	* White circle indicates the sun is closer to the star than the moon.
	* Black circle indicates the moon is closer to the star than the sun.
	* A star indicates that both sun and moon are equidistant.

### Stostone
* *Goal*: Shade some cells (i.e., place stones on the grid)
- *Constraint*: All black cells in a region must be connected horizontally or vertically.
- *Constraint*: A cell with a number indicates how many cells in the region must be blackened.
- *Constraint*: In regions without a number any amount of cells may be blackened (at least one).
- *Constraint*: When two cells are orthogonally adjacent across a region boundary, at least one cell must be white.
- *Constraint*: If all stones "fall down", they must cover exactly the bottom half of the grid.

### Sun and Moon
* *Goal*: Place exactly one star and one stardust cloud in each row and column.
* *Constraint*: Stars illuminates planets, represented as circles, but only on the side that faces the star. Illumination is orthogonal until blocked.
* *Constraint*: Stardust clouds and Planets block starlight.

### Tairupeinto
* *Goal*: Shade some cells on the grid.
* *Constraint*: Each region is either completely filled or completely empty.
* *Constraint*: Numbers outside the grid indicate the number of shaded cells in that direction.

### Tents
* *Goal*: Place tents in some of the remaining squares on the grid.
* *Constraint*: There are exactly as many tents as trees.
* *Constraint*: Tents and trees can be matched up such that each tent is directly orthogonally adjacent to its own tree. A tent may be adjacent to other trees as well as its own.
* *Constraint*: No two tents are adjacent orthogonally or diagonally.
* *Constraint*: The number of tents in each row and column matches the numbers given.

### Toichika
* *Goal*: Place arrows in some of the cells.
* *Constraint*: Each region contains exactly one arrow.
* *Constraint*: Arrows are paired if they point to each other. No arrow is unpaired.
* *Constraint*: Regions with paired arrows are not orthogonally adjacent (that is, they do not share edges)
* *Constraint*: No arrows are placed in between two paired arrows.

### Tren
* *Goal*: Locate some blocks in the grid. Blocks correspond to "cars".
* *Constraint*: Blocks are either $1\times 2$ or $1\times 3$ in dimension.
* *Constraint*:  Each numbered cell is a part of a block.
* *Constraint*: Numbers indicate the amount of possible moves of the block. 
* *Constraint*: Blocks only move in the direction of their short edge.
* *Variant*: **Tren+**
	- Each block contains exactly one number or a question sign (unknown number), indicating the amount of its possible movements.
	- All cells that are not part of any block must be connected horizontally or vertically.
- *Variant*: **Ghost Tren**
	- Blocks can also be placed without any numbers, with no restrictions on their ability to move.
	- All cells that are not part of any block must be connected horizontally or vertically.

### Trilogy
* *Goal*: Fill the grid with figures.
* *Constraint*: Consecutive figures must not be all the same or all different in any row column or diagonal.

### Triplets
* *Goal*: Fill each square with figures (square, circle, triangle)
* *Constraint*: Regions must either contain all identical or all different figures.
* *Constraint*: When two figures are orthogonally adjacent across a region boundary, the figures must be different.

### Walls
* *Goal*: Place a single orthogonal line in every blank cell.
* *Constraint*: A number in a black cell indicates the total length of the segments connected to that square.

### Water Fun
* *Goal*: Fill the grid with water
* *Constraint*: Numbers outside the grid show how many cells of each row and column are filled with water.
* *Constraint*: Connected areas of filled cells must have the same level of water everywhere