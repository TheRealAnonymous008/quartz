* The general goal is to place an object on the grid (or outside of it). Not all cells have to have that object.

### Akari
* *Goal*: Place light bulbs in white cells and light up the grid.
* *Constraint*: Light bulbs may not shine on each other. Bulbs illuminate in all orthogonal directions. 
* *Constraint*: Light is obstructed by the black cells.
* *Constraint*: Numbers in black cells indicate how many bulbs must be placed adjacent to it. 

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

### Buraitoraito
* *Goal*: Place stars on the grid.
* *Constraint*: The numbers in the black cells represent how many stars can be seen from that cell.
* *Constraint*:  A star is visible from the black cell, if there is a straight orthogonal path to the star (i.e., horizontal or vertical)
* *Constraint*: Black cells block visibility.

### Fill-a-Pix
* *Goal*: Shade some cells on the board. The solved board will form a picture.
* *Constraint*: The cells with clues represent how many of the nine squares around it (including itself) should be filled in.

### Gappy
* *Goal*: Shade some cells on the grid.
* *Constraint*: Each row and column contains exactly two shaded cells.
* *Constraint*: Shaded cells cannot touch each other orthogonally or diagonally.
* *Constraint*: Numbers outside the grid show the number of white cells between black cells in the corresponding row or column.

### Irasuto
* *Goal*: Shade some cells on the grid.
* *Constraint*: Clues in white cells represent the number of empty white cells that can be seen from that cell (orthogonally).
* *Constraint*:  Clues in black cells represent the number of empty black cells that are seen from that cell

### Kakurasu
* *Goal*: Color some of the cells to satisfy the clues
* *Constraint*: Numbers on the top and left sides give the totals for the black squares based on their value reading in that direciton
* *Constraint*: Numbers on the bottom and right side  give the value of the cells from that direction 
	* So that, for example, clues on the top give sums along columns. The values used are those specified on the right side of the grid (which go down along columns).

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
* *Constraint*: Paths may not cross### Minesweeper
* *Goal*: Place mines into empty cells on the grid.
* *Constraint*: Digits in the grid represent the number of mines in the neighboring cells, including diagonal neighbors.
* *Variant*: **Minesweeper Battleships** - mines are replaced with battleships. Clues indicate how many ship pieces are adjacent to it. 
	* *Constraint*: Ships may not touch each other, not even diagonally.

### Mochikoro
* *Goal*: Shade some cells on the grid.
* *Constraint*: Shaded cells divide the grid into rectangular islands of unshaded cells.
* *Constraint*: Islands cannot share edges, but they must be connected diagonally via their corners
* *Constraint*: Islands must have the same number of  cells as the number it contains.
* *Constraint*: No pools. No $2x2$ areas must contain only shaded cells

### No Four in a Row
* *Goal*: Fill the grid with symbols.
* *Constraint*:  Four consecutive symbols never appear in any row, column, or diagonal.

### Norinori
* *Goal*: Shade some cells in the grid
* *Constraint*: Every region contains exactly two black cells.
* *Constraint*: Each block must be a part of a domino, irrespective of region borders.
* *Constraint*: No two dominoes may share an edge. They can touch diagonally.

### Shakashaka
* *Goal*: Place triangles in some of the white cells.
* *Constraint* The white parts of the grid (that do not have black triangles) must form rectangular regions.
* *Constraint*: Black cells with a number must be orthogonally adjacent to the specified number of black triangles.

### Tents
* *Goal*: Place tents in some of the remaining squares on the grid.
* *Constraint*: There are exactly as many tents as trees.
* *Constraint*: Tents and trees can be matched up such that each tent is directly orthogonally adjacent to its own tree. A tent may be adjacent to other trees as well as its own.
* *Constraint*: No two tents are adjacent orthogonally or diagonally.
* *Constraint*: The number of tents in each row and column matches the numbers given.

### Tren
* *Goal*: Locate some blocks in the grid. Blocks correspond to "cars".
* *Constraint*: Blocks are either $1\times 2$ or $1\times 3$ in dimension.
* *Constraint*:  Each numbered cell is a part of a block.
* *Constraint*: Numbers indicate the amount of possible moves of the block. 
* *Constraint*: Blocks only move in the direction of their short edge.

### Walls
* *Goal*: Place a single orthogonal line in every blank cell.
* *Constraint*: A number in a black cell indicates the total length of the segments connected to that square.